# UniTask - Unity 零分配异步/等待

![Unity](https://img.shields.io/badge/Unity-2020.3%20LTS%2B-blue.svg)
![UniTask](https://img.shields.io/badge/UniTask-2.x-green.svg)
![.NET](https://img.shields.io/badge/.NET-Standard%202.1-blue.svg)
![Status](https://img.shields.io/badge/status-稳定-success.svg)
![Documentation](https://img.shields.io/badge/docs-完整-brightgreen.svg)

[English](./README.md) | 简体中文 | [返回主页](../README-CN.md)

## 概述

Unity 的高性能、零分配异步/等待库。用完整的 async/await 支持和最小 GC 分配替代协程。

---

## 为什么使用 UniTask？

- **零分配** - 基于结构体的 ValueTask 模式消除 GC 压力
- **高性能** - 比标准 C# Task 和 Unity 协程更快
- **完整的 async/await 支持** - 自然地编写异步代码
- **Unity 集成** - 与 Unity 生命周期无缝协作
- **取消支持** - 内置取消令牌支持
- **LINQ 风格操作符** - 熟悉的异步操作查询语法

---

## 安装

通过 Unity 包管理器使用 git URL 安装：

```
https://github.com/Cysharp/UniTask.git?path=src/UniTask/Assets/Plugins/UniTask
```

---

## 基本用法

### 简单异步方法

```csharp
using Cysharp.Threading.Tasks;
using UnityEngine;

public class Example : MonoBehaviour
{
    async void Start()
    {
        await UniTask.Delay(1000);
        Debug.Log("1 秒过去了！");
    }
}
```

### 替代协程

**之前（协程）：**
```csharp
IEnumerator DelayedAction()
{
    yield return new WaitForSeconds(1f);
    Debug.Log("完成！");
}
```

**之后（UniTask）：**
```csharp
async UniTaskVoid DelayedAction()
{
    await UniTask.Delay(1000);
    Debug.Log("完成！");
}
```

---

## 常用模式

### 等待帧

```csharp
await UniTask.Yield();                    // 下一帧
await UniTask.WaitForEndOfFrame();        // 帧结束
await UniTask.WaitForFixedUpdate();       // 固定更新
```

### 取消操作

```csharp
async UniTask LoadDataAsync(CancellationToken cancellationToken)
{
    cancellationToken.ThrowIfCancellationRequested();
    await UniTask.Delay(1000, cancellationToken: cancellationToken);
}

// 使用组件的取消令牌
await LoadDataAsync(this.GetCancellationTokenOnDestroy());
```

### WhenAll / WhenAny

```csharp
// 等待所有任务
await UniTask.WhenAll(
    LoadPlayerDataAsync(),
    LoadGameSettingsAsync(),
    LoadLevelDataAsync()
);

// 等待任一任务
var (winIndex, result) = await UniTask.WhenAny(
    Task1Async(),
    Task2Async()
);
```

### 超时

```csharp
try
{
    await LoadDataAsync().Timeout(TimeSpan.FromSeconds(5));
}
catch (TimeoutException)
{
    Debug.Log("操作超时！");
}
```

---

## 最佳实践

1. 对返回值的方法使用 `UniTask`
2. 对即发即忘操作使用 `UniTaskVoid`
3. 在长时间运行的操作中始终处理取消令牌
4. 对 MonoBehaviour 方法使用 `this.GetCancellationTokenOnDestroy()`
5. 当不等待 UniTaskVoid 时调用 `.Forget()`

---

## 性能提示

- UniTask 基于结构体，零堆分配
- 尽可能使用 `UniTask.Yield()` 而不是 `WaitForEndOfFrame`
- 在 Unity 中优先使用 `async UniTask` 而不是 `async Task`
- 对频繁创建的任务使用对象池

---

## 常见用例

### 加载场景

```csharp
async UniTask LoadSceneAsync(string sceneName)
{
    var operation = SceneManager.LoadSceneAsync(sceneName);
    await operation.ToUniTask();
}
```

### 网络请求

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

### 按钮点击

```csharp
async UniTaskVoid Start()
{
    var button = GetComponent<Button>();
    await button.OnClickAsync(this.GetCancellationTokenOnDestroy());
    Debug.Log("按钮被点击！");
}
```

---

## 资源

- [GitHub 仓库](https://github.com/Cysharp/UniTask)
- [官方文档](https://github.com/Cysharp/UniTask#readme)
- [API 参考](https://cysharp.github.io/UniTask/)

---

## 系统要求

- Unity 2020.3 或更高版本
- .NET Standard 2.1 或更高版本

---

## 许可证

MIT 许可证 - 可免费用于商业和非商业项目。
