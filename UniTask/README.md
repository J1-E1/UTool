# UniTask - Zero-Allocation Async/Await for Unity

## Overview / 概述

**EN:** UniTask is a high-performance, zero-allocation async/await library designed specifically for Unity. It provides a better alternative to Unity's Coroutines with full async/await support and minimal GC allocation.

**CN:** UniTask 是专为 Unity 设计的高性能、零分配的异步/等待库。它提供了比 Unity 协程更好的替代方案，具有完整的 async/await 支持和最小的 GC 分配。

---

## Why UniTask? / 为什么使用 UniTask？

**EN:**
- **Zero Allocation** - Struct-based ValueTask pattern eliminates GC pressure
- **High Performance** - Faster than standard C# Task and Unity Coroutines
- **Full async/await Support** - Write asynchronous code naturally
- **Unity Integration** - Works seamlessly with Unity lifecycle and components
- **Cancellation Support** - Built-in cancellation token support
- **LINQ Style Operators** - Familiar query syntax for async operations

**CN:**
- **零分配** - 基于结构体的 ValueTask 模式消除 GC 压力
- **高性能** - 比标准 C# Task 和 Unity 协程更快
- **完整的 async/await 支持** - 自然地编写异步代码
- **Unity 集成** - 与 Unity 生命周期和组件无缝协作
- **取消支持** - 内置取消令牌支持
- **LINQ 风格操作符** - 熟悉的异步操作查询语法

---

## Quick Start / 快速开始

### Installation / 安装

**EN:** Install via Unity Package Manager using git URL:

**CN:** 通过 Unity 包管理器使用 git URL 安装：

```
https://github.com/Cysharp/UniTask.git?path=src/UniTask/Assets/Plugins/UniTask
```

---

## Basic Usage / 基本用法

### Simple Async Method / 简单异步方法

```csharp
using Cysharp.Threading.Tasks;
using UnityEngine;

public class Example : MonoBehaviour
{
    async void Start()
    {
        // Wait for 1 second (zero allocation)
        await UniTask.Delay(1000);
        
        Debug.Log("1 second passed!");
    }
}
```

### Replacing Coroutines / 替代协程

**Before (Coroutine) / 之前（协程）：**
```csharp
IEnumerator DelayedAction()
{
    yield return new WaitForSeconds(1f);
    Debug.Log("Done!");
}

StartCoroutine(DelayedAction());
```

**After (UniTask) / 之后（UniTask）：**
```csharp
async UniTaskVoid DelayedAction()
{
    await UniTask.Delay(1000);
    Debug.Log("Done!");
}

DelayedAction().Forget();
```

---

## Common Patterns / 常用模式

### Wait for Frame / 等待帧

```csharp
// Wait for next frame
await UniTask.Yield();

// Wait for end of frame
await UniTask.WaitForEndOfFrame();

// Wait for fixed update
await UniTask.WaitForFixedUpdate();
```

### Cancellation / 取消操作

```csharp
async UniTask LoadDataAsync(CancellationToken cancellationToken)
{
    // Check if cancelled
    cancellationToken.ThrowIfCancellationRequested();
    
    await UniTask.Delay(1000, cancellationToken: cancellationToken);
    
    // Load data...
}

// Use component's cancellation token
await LoadDataAsync(this.GetCancellationTokenOnDestroy());
```

### WhenAll / WhenAny / 并行等待

```csharp
// Wait for all tasks to complete
await UniTask.WhenAll(
    LoadPlayerDataAsync(),
    LoadGameSettingsAsync(),
    LoadLevelDataAsync()
);

// Wait for any task to complete
var (winIndex, result) = await UniTask.WhenAny(
    Task1Async(),
    Task2Async()
);
```

### Timeout / 超时

```csharp
try
{
    await LoadDataAsync().Timeout(TimeSpan.FromSeconds(5));
}
catch (TimeoutException)
{
    Debug.Log("Operation timed out!");
}
```

---

## Async LINQ / 异步 LINQ

```csharp
// Process items asynchronously
await UniTaskAsyncEnumerable.Range(0, 10)
    .Select(async x => 
    {
        await UniTask.Delay(100);
        return x * 2;
    })
    .ForEachAsync(x => Debug.Log(x));
```

---

## Best Practices / 最佳实践

**EN:**
1. Use `UniTask` for methods that return values
2. Use `UniTaskVoid` for fire-and-forget operations
3. Always handle cancellation tokens in long-running operations
4. Use `this.GetCancellationTokenOnDestroy()` for MonoBehaviour methods
5. Call `.Forget()` on UniTaskVoid when you don't await it

**CN:**
1. 对返回值的方法使用 `UniTask`
2. 对即发即忘操作使用 `UniTaskVoid`
3. 在长时间运行的操作中始终处理取消令牌
4. 对 MonoBehaviour 方法使用 `this.GetCancellationTokenOnDestroy()`
5. 当不等待 UniTaskVoid 时调用 `.Forget()`

---

## Performance Tips / 性能提示

**EN:**
- UniTask is struct-based, causing zero heap allocation
- Use `UniTask.Yield()` instead of `WaitForEndOfFrame` when possible
- Prefer `async UniTask` over `async Task` in Unity
- Use object pooling for frequently created tasks

**CN:**
- UniTask 基于结构体，零堆分配
- 尽可能使用 `UniTask.Yield()` 而不是 `WaitForEndOfFrame`
- 在 Unity 中优先使用 `async UniTask` 而不是 `async Task`
- 对频繁创建的任务使用对象池

---

## Common Use Cases / 常见用例

### Loading Scenes / 加载场景

```csharp
async UniTask LoadSceneAsync(string sceneName)
{
    var operation = SceneManager.LoadSceneAsync(sceneName);
    await operation.ToUniTask();
}
```

### Web Requests / 网络请求

```csharp
async UniTask<string> GetDataAsync(string url)
{
    using var request = UnityWebRequest.Get(url);
    await request.SendWebRequest();
    
    if (request.result != UnityWebRequest.Result.Success)
    {
        throw new Exception(request.error);
    }
    
    return request.downloadHandler.text;
}
```

### Button Click / 按钮点击

```csharp
async UniTaskVoid Start()
{
    var button = GetComponent<Button>();
    
    await button.OnClickAsync(this.GetCancellationTokenOnDestroy());
    
    Debug.Log("Button clicked!");
}
```

---

## Resources / 资源

- [GitHub Repository](https://github.com/Cysharp/UniTask)
- [Official Documentation](https://github.com/Cysharp/UniTask#readme)
- [API Reference](https://cysharp.github.io/UniTask/)

---

## System Requirements / 系统要求

**EN:**
- Unity 2020.3 or later
- .NET Standard 2.1 or later

**CN:**
- Unity 2020.3 或更高版本
- .NET Standard 2.1 或更高版本

---

## License / 许可证

MIT License - Free to use in commercial and non-commercial projects.

MIT 许可证 - 可免费用于商业和非商业项目。
