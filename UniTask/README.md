# UniTask - Zero-Allocation Async/Await for Unity

![Unity](https://img.shields.io/badge/Unity-2020.3%20LTS%2B-blue.svg)
![UniTask](https://img.shields.io/badge/UniTask-2.x-green.svg)
![.NET](https://img.shields.io/badge/.NET-Standard%202.1-blue.svg)
![Status](https://img.shields.io/badge/status-stable-success.svg)
![Documentation](https://img.shields.io/badge/docs-complete-brightgreen.svg)

English | [简体中文](./README-CN.md) | [Return to Main](../README.md)

## Overview

High-performance, zero-allocation async/await library for Unity. Replaces Coroutines with full async/await support and minimal GC allocation.

---

## Why UniTask?

- **Zero Allocation** - Struct-based ValueTask pattern eliminates GC pressure
- **High Performance** - Faster than standard C# Task and Unity Coroutines
- **Full async/await Support** - Write asynchronous code naturally
- **Unity Integration** - Works seamlessly with Unity lifecycle
- **Cancellation Support** - Built-in cancellation token support
- **LINQ Style Operators** - Familiar query syntax for async operations

---

## Installation

Install via Unity Package Manager using git URL:

```
https://github.com/Cysharp/UniTask.git?path=src/UniTask/Assets/Plugins/UniTask
```

---

## Basic Usage

### Simple Async Method

```csharp
using Cysharp.Threading.Tasks;
using UnityEngine;

public class Example : MonoBehaviour
{
    async void Start()
    {
        await UniTask.Delay(1000);
        Debug.Log("1 second passed!");
    }
}
```

### Replacing Coroutines

**Before (Coroutine):**
```csharp
IEnumerator DelayedAction()
{
    yield return new WaitForSeconds(1f);
    Debug.Log("Done!");
}
```

**After (UniTask):**
```csharp
async UniTaskVoid DelayedAction()
{
    await UniTask.Delay(1000);
    Debug.Log("Done!");
}
```

---

## Common Patterns

### Wait for Frame

```csharp
await UniTask.Yield();                    // Next frame
await UniTask.WaitForEndOfFrame();        // End of frame
await UniTask.WaitForFixedUpdate();       // Fixed update
```

### Cancellation

```csharp
async UniTask LoadDataAsync(CancellationToken cancellationToken)
{
    cancellationToken.ThrowIfCancellationRequested();
    await UniTask.Delay(1000, cancellationToken: cancellationToken);
}

// Use component's cancellation token
await LoadDataAsync(this.GetCancellationTokenOnDestroy());
```

### WhenAll / WhenAny

```csharp
// Wait for all tasks
await UniTask.WhenAll(
    LoadPlayerDataAsync(),
    LoadGameSettingsAsync(),
    LoadLevelDataAsync()
);

// Wait for any task
var (winIndex, result) = await UniTask.WhenAny(
    Task1Async(),
    Task2Async()
);
```

### Timeout

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

## Best Practices

1. Use `UniTask` for methods that return values
2. Use `UniTaskVoid` for fire-and-forget operations
3. Always handle cancellation tokens in long-running operations
4. Use `this.GetCancellationTokenOnDestroy()` for MonoBehaviour methods
5. Call `.Forget()` on UniTaskVoid when you don't await it

---

## Performance Tips

- UniTask is struct-based, causing zero heap allocation
- Use `UniTask.Yield()` instead of `WaitForEndOfFrame` when possible
- Prefer `async UniTask` over `async Task` in Unity
- Use object pooling for frequently created tasks

---

## Common Use Cases

### Loading Scenes

```csharp
async UniTask LoadSceneAsync(string sceneName)
{
    var operation = SceneManager.LoadSceneAsync(sceneName);
    await operation.ToUniTask();
}
```

### Web Requests

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

### Button Click

```csharp
async UniTaskVoid Start()
{
    var button = GetComponent<Button>();
    await button.OnClickAsync(this.GetCancellationTokenOnDestroy());
    Debug.Log("Button clicked!");
}
```

---

## Resources

- [GitHub Repository](https://github.com/Cysharp/UniTask)
- [Official Documentation](https://github.com/Cysharp/UniTask#readme)
- [API Reference](https://cysharp.github.io/UniTask/)

---

## Requirements

- Unity 2020.3+
- .NET Standard 2.1+

---

## License

MIT License - Free to use in commercial and non-commercial projects.
