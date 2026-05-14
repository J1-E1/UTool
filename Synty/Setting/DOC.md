## Copying the example settings UI into your own game.

将现有的示例UI整合到现有项目中

### An alternative to step 3 is using your existing UI
 - 使用现有的用户界面
 ![[Pasted image 20250928102024.png]]


### Step 4: (Optional) Delete or disable unused settings.
- 禁用未使用的Setting内容，有些需要正确设置才会有效果

![[Pasted image 20250928104737.png]]

- 移除不必要的部分
![[Pasted image 20250928133210.png]]
- 然后删除任何存储的设置，不然系统会重新存储他们
![[Pasted image 20250928133430.png]]


![[Pasted image 20250928141018.png]]
- 无需设置所有的id

## Settings

Connection Object
- 设置的setting所连接的具体的和unity核心相关的接口
![[Pasted image 20250928144234.png]]


### Setting Resolvers
- 用以连接UI与Setting system之间的关系
- 需要继承

有些预设预定义的 UI 解析器
![[Pasted image 20250928145522.png]]


## Auto-Save

## Setting Events

## 输入
### StringSetting + InputBindingConnection (NEW InputSystem)

- 详细内容需要多查看Input Rebinding部分的内容


组件
- InputBindingUGUI， 2种状态 Active 和 inactive
- 监听key， mouse， inputs 按钮
- inputBinding 需要使用 inputBindingUGUI
- 按键点击后具有两种状态，用于修改按键
![[Pasted image 20251009164858.png]]
![[Pasted image 20251009164846.png]]

- 需要额外阅读Input Binding 部分的内容> “Input Binding“

[[SettingsGeneratorManual.pdf#page=59&selection=4,63,6,1|SettingsGeneratorManual, 页面 59]]
## Input Rebinding (Using the new Input System)

> Rebinding Overview

[[SettingsGeneratorManual.pdf#page=90&selection=2,0,2,18|SettingsGeneratorManual, 页面 90]]

 ![[Pasted image 20251009182304.png]]
 - 使用inputaction作为游戏内的配置等设置
 - 系统需要Actions Asset
 - 不知有什么用处> AddChangeListener

[[SettingsGeneratorManual.pdf#page=91&selection=53,0,53,17|SettingsGeneratorManual, 页面 91]]


### Rebinding Tutorial

- 这个Setting System 需要 知道 Input Actions(Bindings)， 然后将其与界面部分连接
![[Pasted image 20251009184154.png]]
- 因此需要绑定一个InputBindingConnection
- 在这个InputAction上点击Create ==InputBindingConnections== 来创建相应的子文件

![[Pasted image 20251009185230.png]]

- 然后就需要将对应生成的Connection来串联到我们的Setting汇总表中
- string的key， ID设置清除，比如是keyboard.jump
![[Pasted image 20251009185759.png]]
- 然后老样子在Resolve上色湖之剩余参数
![[Pasted image 20251009185951.png]]

3=

- Input Binding UGUI部分有一个 Input Binding 部分
![[Pasted image 20251009190204.png]]

![[Pasted image 20251009190426.png]]
- 忽略某些按键的设置
> gnore Control Paths:

[[SettingsGeneratorManual.pdf#page=94&selection=23,1,23,21|SettingsGeneratorManual, 页面 94]]




![[Pasted image 20251009191406.png]]
- Binding Path： 在运行是，设置当前链接的地址； 当出现异常时，该路径也将作为备用路径来显示
![[Pasted image 20251009191847.png]]
- 冲突设置
- InputBindingUGUIResolver.ResolveBindingConflictFunc， 此函数可以提供一个提示框
- 用于显示警告对话框（或执行其他操作）。若未设置该函数，系统在检测到冲突时将直接撤销绑定（默认行为）。
- > NOTICE
[[SettingsGeneratorManual.pdf#page=96&selection=10,0,10,6|SettingsGeneratorManual, 页面 96]]


### Input Rebinding Caveats
- 组合绑定的设置目前不支持
