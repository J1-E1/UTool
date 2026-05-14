| col1                           | col2         | 需求                                                                                                                                                                                                          |  |
| ------------------------------ | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | - |
| 自定义组件                     |              |                                                                                                                                                                                                               |  |
| UI动画组件                     | UIAnmiation  | -  需要requireComponeent()Animator)<br />- Play 接口来播放指定动画，参数：动画名、播放完毕后的回调函数委托<br />- 可在无需程序控制下，自动播放，因此public变量中需要有AutoPlay这个参数<br />- 似乎为抽象函数 |  |
| 按钮button                     |              | - 点击按钮，播放音效，click时播放绑定声音文件的触发<br />- 需要根据不同的音效系统，变化                                                                                                                       |  |
| UI元素跟随3D物体组件           |              | -场景中的血条更具，3d物体的组件二移动<br />-通过不断计算3d物体在屏幕中的位置来确定ui位置<br />- 前后位置不同时更新                                                                                            |  |
| 滚动页组件，无线循环scrollview |              | - 列表中有固定的子cell量，当最上有一行被挡住，将其移动到最后<br />- 减少drawcall的量                                                                                                                          |  |
| 数字瓢字组件，记数组件         |              |                                                                                                                                                                                                               |  |
| 自定义下拉框                   |              |                                                                                                                                                                                                               |  |
| 实现                           |              |                                                                                                                                                                                                               |  |
| ButtonManager                  | ButtonManger | - 支持多事件类型， 自动-fitting，动态contentMangaer<br />- 点击**‘Use Custom Content**， 来手动控制content内容                                                                                               |  |
|                                |              |                                                                                                                                                                                                               |  |

## ButtonManager

参数

| 属性              | 类型       | function                       |
| ----------------- | ---------- | ------------------------------ |
| buttonText        |            |                                |
| buttonIcon        |            |                                |
| onclick           |            | 处理按钮触发时的events         |
| onDoubleClick     | UnityEvent | 双击后的events                 |
| onHover           |            |                                |
| clickSound        | AudioClip  | On button click 时的声音       |
| hoversound        | AudioClip  | Hover时候的按钮声音            |
| use Customcontent | bool       | 处理content属性，如button text |

====

接口

```csharp
using UnityEngine;
using Michsky.MUIP;public class SampleClass : MonoBehaviour
{
    [SerializeField] private ButtonManager myButton;
    [SerializeField] private Sprite buttonIcon;    void YourFunction()
    {
        // Updating button content
        myButton.SetText("New Text");
        myButton.SetIcon(buttonIcon);        // Set button interactability
        myButton.Interactable(false);
        myButton.Interactable(true);        // Enable or disable options
        myButton.useRipple = true;
        myButton.enableButtonSounds = true;
        myButton.useClickSound = true;
        myButton.useHoverSound = true;
        myButton.useCustomContent = false;        // Add events
        myButton.onClick.AddListener(TestFunction);
        myButton.onDoubleClick.AddListener(TestFunction);
        myButton.onHover.AddListener(TestFunction);
        myButton.onLeave.AddListener(TestFunction);
    }    void TestFunction()
    {
        Debug.Log("Event test");
    }
}
```

## Charts（PieChart）

- 用于显示饼图的组件

![1752644024303](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/MordenUI/1752644024303.png)


|             col1             |  col2  |           col3           | 条件或者补充                                                                                                         |
| :---------------------------: | :-----: | :----------------------: | -------------------------------------------------------------------------------------------------------------------- |
|   **borderThickness**   |  float  |  似乎是用来改变圆的直径  |                                                                                                                      |
| **addValueToIndicator** | boolean | 是否增加显示的"指示标记" | ![1752644584851](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/MordenUI/1752644584851.png)                                                                     |
|     **valuePrefix**     | string |         改变前缀         | 如果开启indicator的符号，比如增加了<br />- 前缀(<br />- 后缀）<br />![1752644622824](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/MordenUI/1752644622824.png) |
|     **valueSuffix**     | string |         改变后缀         |                                                                                                                      |

```csharp

usingUnityEngine;
usingMichsky.MUIP;//MUIPnamespace

publicclassSampleClass:MonoBehaviour
{
[SerializeField]privatePieChartmyChart;//Chartvariable

voidYourFunction()
{
myChart.ChangeValue(intitemIndex,floatitemValue);//Changespecificitemvalue
myChart.UpdateIndicators();//Updatealllabelindicators
myChart.AddNewItem();//Addsanewchartitemtothelist
}
}
```


## Horizontal Selector



## Notification

![1751951656060](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/MordenUI/1751951656060.png)

- 允许多notification的的stacking形式， show one by one

  - 创建一个 Parent ，object或者rect
  - Add component， Add Notification Stacking
  - 开启“Use Stacking”的形式

  | col1        | col2   | col3                        |
  | ----------- | ------ | --------------------------- |
  | Icon        | sprite | 设置notification 的显示icon |
  | title       |        | notification的header        |
  | description | string | 设置描述的                  |
  | isOn        |        | 返回notification的状态      |
  |             |        |                             |
  | enableTimer | bool   | 设置notification会多久显示  |
- 代码部分

```csharp
using UnityEngine;
using Michsky.MUIP; // MUIP namespacepublic class SampleClass : MonoBehaviour
{
    [SerializeField] private NotificationManager myNotification; // Variable    void YourFunction()
    {
        myNotification.icon = spriteVariable; // Change icon
        myNotification.title = "New Title"; // Change title
        myNotification.description = "New Description"; // Change desc
        myNotification.UpdateUI(); // Update UI
        myNotification.Open(); // Open notification
        myNotification.Close(); // Close notification
        myNotification.onOpen.AddListener(TestFunction); // Invoke open events
        myNotification.onClose.AddListener(TestFunction); // Invoke close events
    }    void TestFunction()
    {
        Debug.Log("Test function");
    }
}

```

## Window Manager

![1752635251430](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/MordenUI/1752635251430.png)

- 将页面放在Windows的content下，页面自动驱动animated
- 将页面，以及触发的按钮设置在window manger的初始化页面中，即可自动初始化，不需要**WindowManager.OpenWindow()**

| col1                   | col2      | col3                       |
| ---------------------- | --------- | -------------------------- |
| currentWindowIndex     | int       | 返回当前选中的window index |
| cullTransparentWindows | boolean   | 禁用不交互的windows        |
| initializeButtons      | boolean   | 自动初始化windows的按钮    |
| onWindowChange         | UnitEvent | window回调                 |


```csharp
usingMichsky.MUIP;//MUIPnamespace
usingUnityEngine;

publicclassSampleClass:MonoBehaviour
{
[SerializeField]privateWindowManagermyWindowManager;

voidYourFunction()
{
myWindowManager.OpenWindow("YourWindowName");//openaspecificwindow
myWindowManager.OpenWindowByIndex(1);//openaspecificwindowbyindex
myWindowManager.NextWindow();//opennextpage
myWindowManager.PrevWindow();//openpreviouspage
myWindowManager.ShowCurrentWindow();//showcurrentwindow
myWindowManager.HideCurrentWindow();//hidecurrentwindow
myWindowManager.ShowCurrentButton();//showcurrentwindowbutton
myWindowManager.HideCurrentButton();//hidecurrentwindowbutton
}
}
```
