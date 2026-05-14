
本场景展示一款第三人称射击游戏。使用WASD键移动，空格键跳跃，Shift键冲刺。鼠标左键发射弹药。鼠标操作旋转玩家瞄准核心对象，该对象控制玩家方向与瞄准。摄像机由此驱动——此类控制器无法直接独立控制摄像机方向。


摄像机由自定义的AimCameraRig摄像机管理器控制，当右键按下时激活瞄准摄像机。该系统同时在瞄准时切换玩家旋转模式。


准星标示玩家瞄准位置。红色圆点则显示若从瞄准核心发射射线时的实际命中点。当准星与红点未对齐时，表示玩家与准星指向目标间存在障碍物，此时准星会向外拉伸以示警示。


关闭帮助窗口后光标将被锁定。按Esc键可解锁。

=== 

### CursorLockManager

![[Pasted image 20251105100512.png]]

### CinemachineInputAxisController

- CinemachineInputAxisController的主要目的是桥接Unity的输入系统与Cinemachine相机系统。它可以自动检测并驱动那些实现==**IInputAxisOwner**==接口的Cinemachine行为（如CinemachineFreeLook、CinemachineOrbital等），让用户输入（如鼠标、键盘或游戏手柄）能够平滑地控制相机的轴向运动。


![[Pasted image 20251105112737.png]]

- 通过 #if CINEMACHINE_UNITY_INPUTSYSTEM 来限定使用inputsystem来
- PlayerIndex：单人玩家默认为-1，多人将其
- AutoEnableInputs： 如果为 true（默认），会在启动时自动启用绑定的 Input Actions。
- InputActionReference ： 在 Reader 类中）：这是连接的核心。开发者在 Inspector 中分配一个 InputActionReference（指向 Input Action Asset 中的一个 Action），组件会解析它来读取输入。
- ReadControlValueOverride ： 一个委托，允许开发者覆盖默认读取逻辑，以支持 float 或 Vector2 以外的 InputAction 类型（例如自定义类型



===
 ![[Pasted image 20251105113823.png]]
 - 通过ResolveAndReadInputAction获取值，加上阻尼的度数Gain
 - ReadInput(): 检查Action的 type，并获取鼠标输入
![[Pasted image 20251105114207.png]]