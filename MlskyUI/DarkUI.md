- https://docs.michsky.com/docs/dark-ui/quick-start/

## 整理

== 快速使用

- 使用Input System (New)
- 需要关注不同平台的输入问题，估涉及的平台为inputSystem

### ==  In Game 在游戏中

HUD  Manager

- 可以设置HUD的显示，允许动态变化在运行时间

![1749038182424](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/DarkUI/1749038182424.png)

Pause Menu Manager

### == UIManager

- 位置

  ![1744182708826](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/DarkUI/1744182708826.png)
- “换皮”控制器

![1744182306752](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/DarkUI/1744182306752.png)

- Update Values

  - hui动态更新UI elements，相反则会在play之后（runtime）更新

  ![1744182964383](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/DarkUI/1744182964383.png)
- 脚本解释

  ![1744183861795](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/DarkUI/1744183861795.png)

  - 应该是访问Editor通过 `serializedObject`访问被编辑对象的序列化数据
  - 使得编辑器能够可视化修改脚本的对应字段
  - 以及更换自定义的GUISKin
- 可以看更加详细的颜色hex

  ![1744184178890](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/DarkUI/1744184178890.png)
- UI Manager Hints ： 查看每个manger的tips

### == UI Elements

Button

- 设置text
- 通过UpdateUI来更新，并forcelayoutgroup的修改

```csharp
using Michsky.UI.Dark; // namespacepublic ButtonManager myButton; // Your button variablevoid YourFunction()
{
   // Updating button content
   myButton.buttonText = "My New Text";
   myButton.UpdateUI();   // Enable or disable options
   myButton.useRipple = true;
   myButton.useCustomContent = false;
}

```

![1744185507101](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/DarkUI/1744185507101.png)

Horizontal Selector

- 似乎是list中向前或者向后的内容
- Items,  您可以在此列表中添加水平选择器项目。如果愿意，还可以为每个项目添加功能。只要启用 “指示器”，每个按钮都会在运行时生成一个指示器项。
- Saving，启用此功能后，您可以保存所选值。请注意，每个选择器都应有自己唯一的选择器标签值。否则，选择器之间可能会发生冲突。

```csharp
using Michsky.UI.Dark; // namespacepublic HorizontalSelector mySelector; // Your selector variablevoid YourFunction()
{
   // Creating a new item
   mySelector.CreateNewItem("Item Title");   // Creating items within a loop
   for (int i = 0; i < yourIndexOrVariable; ++i)
   {
	  mySelector.CreateNewItem("Item Title");
   }   // Adding a new dynamic event
   mySelector.selectorEvent.AddListener(YourEventHere);   // Initializing the selector - use this if you've created a new item at runtime
   mySelector.defaultIndex = 3; // optional
   mySelector.SetupSelector();   // Changing index & updating UI
   mySelector.index = 3;
   mySelector.UpdateUI();   mySelector.ForwardClick(); // Select next item
   mySelector.PreviousClick(); // Select previous item
   mySelector.RemoveItem("Item Title"); // Delete a specific item
}

```

### Modal Window

- 用于定义一个弹窗的内容，使用 Modal Window manger
- 提供了接口，统一更新ui，以及fade In ， fade out
- 对Bulrmanger的使用，可以帮助其显示的时候有虚化的作用

![1744186576123](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/DarkUI/1744186576123.png)

Slider

- 基本使用的是原生的slider组件
- 在此基础上加上了定制的内容

![1744187938450](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/DarkUI/1744187938450.png)

### ==  Panels & Windows

### ==  Splash Screen

- Splash Screen Manager， 基本就是用来延迟显示一些内容的页面
- 注意代码的使用方式

```csharp
usingMichsky.UI.Dark;//namespace

publicSplashScreenManagerssManager;

voidYourFunction()
{
ssManager.disableSplashScreen=false;//Disableorenablesplashscreen
ssManager.startDelay=0.5f;//Addadelaybeforethesequence
}

```

![1744188181812](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/DarkUI/1744188181812.png)

### == Gamepad Handler

- 应该是用于控制输入设备的识别
- 默认面板管理器： 管理用户界面的主要组件。它默认连接到 “菜单管理器”。
  面板管理器 场景中的所有主面板管理器。
  键盘对象： 这些对象将在鼠标/键盘的任何意义上激活，并在游戏手柄的意义上停用。
  游戏板对象： 这些对象将在任何意义上的游戏板上激活，并在鼠标上停用。
  始终更新：断开/连接时将更新输入设备。
  影响光标： 根据游戏手柄状态启用或禁用光标。
  游戏手柄热键： 这些输入会影响游戏手柄状态的切换。
- 关注代码的使用方式
  - 判断是否有接入
  - 判断更新的频次等

```csharp
using Michsky.UI.Dark; // namespace
public GamepadChecker gamepadManager;void YourFunction()
{
   gamepadManager.alwaysUpdate = true; // Change the update state
   gamepadManager.gamepadConnected; // Get the gamepad conenction state
   gamepadManager.hAxis; // Get the right stick horizontal axis (0f - 1f)
   gamepadManager.vAxis; // Get the right stick vertical axis (0f - 1f)
}
```

![1744188709737](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/DarkUI/1744188709737.png)

### ==  Gamepad Scroll Event

![1744188926988](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/DarkUI/1744188926988.png)

### == Localization

- 本地化设置，通过此系统来， 设置默认语言，即添加删除语言
- 通过UImanger来设置其是否启用**Tools > Reach UI > Show UI Manager**

### == Achievement

#### **主控**

- 将控制开关放在 “UIManager”上面，如颜色，show Library等内容

![1747882453114](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/DarkUI/1747882453114.png)

#### **数据**

- 可以修改Libray数据，链接到 Achievement Library
- 预览Data Manger中的内容，可以修改 **Data Behaviour**至 **"Unlocked"** 的形式，最终还是将其设置为“Default”，在preview结束后

![1747883073633](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/DarkUI/1747883073633.png)

#### **成就数据**

- 注意几个关键的点， Title， Icon，Hidden Title，以及Hidden 描述等
- ui控制控件的属性由Achievement Manager 来控制

![1747883290792](📁%2003_Inbox/Unity/Tool/MIsky.UI/image/DarkUI/1747883290792.png)

#### 代码部分

- 接口为两个，初始化，设置成绩是否获得

```csharp
using UnityEngine;
using Michsky.UI.Reach; // Reach UI namespacepublic class SampleClass : MonoBehaviour
{
    [SerializeField] private AchievementManager achManager;    void Start()
    {
        // Manually initialize achievement items
        achManager.InitializeItems();    // Set achievement {name} to true or false
        // No reference required for this call as it's static
        AchievementManager.SetAchievement("Ach Name", true);
    }
}

```
