https://github.com/dotnet/roslyn/blob/main/docs/features/task-types.md
---

# Async Task Types in C#

[](https://github.com/dotnet/roslyn/blob/main/docs/features/task-types.md#async-task-types-in-c)

Extend `async` to support _task types_ that match a specific pattern, in addition to the well known types `System.Threading.Tasks.Task` and `System.Threading.Tasks.Task<T>`.

## Task Type

[](https://github.com/dotnet/roslyn/blob/main/docs/features/task-types.md#task-type)


A _task type_ is a `class` or `struct` with an associated _builder type_ identified with `System.Runtime.CompilerServices.AsyncMethodBuilderAttribute`. The _task type_ may be non-generic, for async methods that do not return a value, or generic, for methods that return a value.

To support `await`, the _task type_ must have a corresponding, accessible `GetAwaiter()` method that returns an instance of an _awaiter type_ (see _C# 7.7.7.1 Awaitable expressions_).

```cs
[AsyncMethodBuilder(typeof(MyTaskMethodBuilder<>))]
class MyTask<T>
{
    public Awaiter<T> GetAwaiter();
}

class Awaiter<T> : INotifyCompletion
{
    public bool IsCompleted { get; }
    public T GetResult();
    public void OnCompleted(Action completion);
}
```

## Builder Type

[](https://github.com/dotnet/roslyn/blob/main/docs/features/task-types.md#builder-type)

The _builder type_ is a `class` or `struct` that corresponds to the specific _task type_. The _builder type_ can have at most 1 type parameter and must not be nested in a generic type. The _builder type_ has the following `public` methods. For non-generic _builder types_, `SetResult()` has no parameters.

```cs
class MyTaskMethodBuilder<T>
{
    public static MyTaskMethodBuilder<T> Create();

    public void Start<TStateMachine>(ref TStateMachine stateMachine)
        where TStateMachine : IAsyncStateMachine;

    public void SetStateMachine(IAsyncStateMachine stateMachine);
    public void SetException(Exception exception);
    public void SetResult(T result);

    public void AwaitOnCompleted<TAwaiter, TStateMachine>(
        ref TAwaiter awaiter, ref TStateMachine stateMachine)
        where TAwaiter : INotifyCompletion
        where TStateMachine : IAsyncStateMachine;
    public void AwaitUnsafeOnCompleted<TAwaiter, TStateMachine>(
        ref TAwaiter awaiter, ref TStateMachine stateMachine)
        where TAwaiter : ICriticalNotifyCompletion
        where TStateMachine : IAsyncStateMachine;

    public MyTask<T> Task { get; }
}
```

## Execution

[](https://github.com/dotnet/roslyn/blob/main/docs/features/task-types.md#execution)

The types above are used by the compiler to generate the code for the state machine of an `async` method. (The generated code is equivalent to the code generated for async methods that return `Task`, `Task<T>`, or `void`. The difference is, for those well known types, the _builder types_ are also known to the compiler.)

`Builder.Create()` is invoked to create an instance of the _builder type_.

If the state machine is implemented as a `struct`, then `builder.SetStateMachine(stateMachine)` is called with a boxed instance of the state machine that the builder can cache if necessary.

`builder.Start(ref stateMachine)` is invoked to associate the builder with compiler-generated state machine instance. The builder must call `stateMachine.MoveNext()` either in `Start()` or after `Start()` has returned to advance the state machine. After `Start()` returns, the `async` method calls `builder.Task` for the task to return from the async method.

Each call to `stateMachine.MoveNext()` will advance the state machine. If the state machine completes successfully, `builder.SetResult()` is called, with the method return value if any. If an exception is thrown in the state machine, `builder.SetException(exception)` is called.

If the state machine reaches an `await expr` expression, `expr.GetAwaiter()` is invoked. If the awaiter implements `ICriticalNotifyCompletion` and `IsCompleted` is false, the state machine invokes `builder.AwaitUnsafeOnCompleted(ref awaiter, ref stateMachine)`. `AwaitUnsafeOnCompleted()` should call `awaiter.OnCompleted(action)` with an action that calls `stateMachine.MoveNext()` when the awaiter completes. Similarly for `INotifyCompletion` and `builder.AwaitOnCompleted()`.

## Overload Resolution

[](https://github.com/dotnet/roslyn/blob/main/docs/features/task-types.md#overload-resolution)

Overload resolution is extended to recognize _task types_ in addition to `Task` and `Task<T>`.

An `async` lambda with no return value is an exact match for an overload candidate parameter of non-generic _task type_, and an `async` lambda with return type `T` is an exact match for an overload candidate parameter of generic _task type_.

Otherwise if an `async` lambda is not an exact match for either of two candidate parameters of _task types_, or an exact match for both, and there is an implicit conversion from one candidate type to the other, the from candidate wins. Otherwise recursively evaluate the types `A` and `B` within `Task1<A>` and `Task2<B>` for better match.

Otherwise if an `async` lambda is not an exact match for either of two candidate parameters of _task types_, but one candidate is a more specialized type than the other, the more specialized candidate wins.



===

---

Task Type (任务类型)
- 现在只要你的类或结构体满足两个条件，编译器就认它：

1. **头上顶着个标签**：必须有 `[AsyncMethodBuilder]` 特性，告诉编译器：“别用默认逻辑，用我指定的 Builder 来构建任务”。
    
2. **能被等待**：必须有一个 `GetAwaiter()` 方法（也就是符合 Awaitable Pattern）。


---
Builder Type (构建器类型)


-


---
#### **Execution (执行流程)**

- **原文含义**：描述了编译器生成的**状态机 (State Machine)** 如何与 Builder 交互。
    
- **解释**：
    
    1. **编译器重写**：编译器把你写的 `async` 方法转换成一个 `struct`（状态机）。
        
    2. **初始化**：调用 `Builder.Create()`。
        
    3. **启动**：调用 `Builder.Start(ref stateMachine)`，这会执行你的代码直到遇到第一个 `await`。
        
    4. **暂停与恢复**：
        
        - 遇到 `await`，如果任务没完成，Builder 会调用 `AwaitOnCompleted` 把状态机挂起（注册回调）。
            
        - 当等待的任务完成了，回调触发，调用 `stateMachine.MoveNext()`，代码从暂停的地方继续往下跑。
            
    5. **结束**：方法跑完，Builder 调用 `SetResult`，把结果塞进你最开始拿到的那个 Task 对象里。


---

#### **为什么需要自定义 Task Type？**

原生的 `Task` 是一个 **类 (Class)**。

- **痛点**：每次调用 `async` 方法返回 `Task`，都要在堆内存 (Heap) 上 `new` 一个对象。对于高频调用的游戏逻辑（每帧运行），这会导致大量的 **GC (垃圾回收)** 压力。
    
- **解决方案**：通过这个特性，我们可以定义一个 **结构体 (Struct)** 类型的 Task（如 `UniTask` 或 `ValueTask`）。
    
    - Builder 也是结构体。
        
    - 状态机也是结构体。
        
    - **结果**：整个异步调用链可以在**栈 (Stack)** 上完成，实现 **零内存分配 (Zero Allocation)**


// 使用自定义的异步类型 MyTask
[AsyncMethodBuilder(typeof(MyTaskBuilder))] // 1. 指定 Builder
public struct MyTask { ... } 

public async MyTask DemoAsync() {
    var i = await DoWorkAsync();
    return;
}


public MyTask DemoAsync() {
    // 1. 创建 Builder
    var builder = MyTaskBuilder.Create();
    
    // 2. 创建状态机
    var stateMachine = new DemoAsyncStateMachine();
    stateMachine.builder = builder;
    stateMachine.state = -1; 
    
    // 3. 启动
    builder.Start(ref stateMachine);
    
    // 4. 返回 Builder 生产出来的 Task
    return builder.Task; 
}


---

#### **关于 Overload Resolution (重载决议)**

这一段讲的是：如果你有两个重载方法，参数分别是 `Func<Task>` 和 `Func<MyTask>`，当你传入一个 `async () => {}` 时，编译器该选谁？

- **规则**：
    
    1. 如果 Lambda 有返回值（`async () => return 1`），优先匹配泛型 Task（如 `MyTask<int>`）。
        
    2. 如果 Lambda 无返回值（`async () => {}`），优先匹配非泛型 Task（如 `MyTask`）。
        
    3. **最具体的类型胜出**：这允许库作者提供更优化的重载。例如，如果 `UniTask` 比 `Task` 更具体（或者在特定上下文中更匹配），编译器会优先选择 `UniTask` 的版本。
        

- 自动匹配一个高性能的方式

---

#### **INotifyCompletion vs ICriticalNotifyCompletion**

文档中提到了这两个接口。

- `INotifyCompletion`：标准的等待接口。
    
- `ICriticalNotifyCompletion`：**“不安全”** 的版本（Unsafe）。
    
    - **区别**：`Unsafe` 版本不会捕获当前的 `ExecutionContext`（执行上下文）。
        
    - **作用**：在不用跨越线程安全边界（如 ASP.NET 的身份验证上下文）时，使用 `Unsafe` 版本性能更高。**UniTask 极其依赖这个特性来提升性能**，因为它不需要保存和恢复繁重的上下文信息。
        

### 总结

这段内容解释了 **C# 编译器如何允许“外挂”异步系统**。

- **官方 Task**：就像是官方提供的“标准轿车”，功能全但比较重，要在堆上分配内存。
    
- **自定义 Task (UniTask)**：就像是利用这套规则（AsyncMethodBuilder）造出来的“赛车”，去掉了空调音响（Context），把车身换成碳纤维（Struct），专门为了在特定赛道（Unity 单线程环境）上跑出最高速度。