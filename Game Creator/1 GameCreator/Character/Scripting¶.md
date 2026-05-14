## Character[¶](https://docs.gamecreator.io/gamecreator/characters/scripting/character/#character "Permanent link")

### ## Kernel[¶](https://docs.gamecreator.io/gamecreator/characters/scripting/character/#kernel "Permanent link")

- 由5个单元构成，这些单元共同组成了内核

![[Pasted image 20251107093530.png]]

- **Player** ： 定义角色是否为可操控角色，以及用户如何与其交互。若需创建自定义角色输入系统，则需实现 IUnitPlayer 接口。

- **Motion**： 场景中不同的情况，受这些内容影响，同各国此系统，比如人物的高等内容。
- **Driver**： 根据Motion的输入来决定角色的移动，若需集成其他资源商店包中的角色系统，请创建一个继承自 IUnitDriver 的新类。


![[Pasted image 20251107094003.png]]

- **Facing:** 决定，决定角色朝向，例如，默认行为是让角色朝向其移动方向。若需自定义角色朝向，请创建实现 IUnitFacing 接口的自定义类。
- **Animim**: 该系统接收驱动程序的输入，并通过Mecanim参数告知动画器组件应播放何种动画。若需为角色使用自定义动画器，请创建实现IUnitAnimim接口的类。

== 
- IPlayer系统，它首先调用了 **Player**'s system `Update()`方法，接收用户的Input，同时call了motion中的两个方法来移动
![[Pasted image 20251107100053.png]]

- 然后是Motion：此处将计算外部作用力，例如重力、斜坡滑行、冲刺、跳跃等。
- Motion更新前，会考虑Player系统，一个系统可以访问任何其他系统的数据，在此之前
![[Pasted image 20251107100152.png]]


- 执行Driver的update方法，他根据运动的参数来驱动角色的Transfrom来更新
- 执行Facing，根据Driver和Motion提供的数据，它计算出角色应该朝向哪里
- 执行Animation， 执行Animator中必要的参数和剩下的系统

== 
![[Pasted image 20251107102009.png]]
- 每个系统都独立


### Player[¶](https://docs.gamecreator.io/gamecreator/characters/scripting/character/#player "Permanent link")

- 负责玩家的交互，若未勾选  `Is Player`，将会整个跳过
- `IsControllable`， 当处于过场动画时，如果不希望控制玩家

### Motion[¶](https://docs.gamecreator.io/gamecreator/characters/scripting/character/#motion "Permanent link")

- 接收移动指令
- 设置核心控制参数， 包含其所有特性参数，如身高、移动速度、终端速度等。


![[Pasted image 20251107102825.png]]
- MoveToDirection 方法定义角色移动方向，需每帧调用以维持移动状态，否则角色将停止移动。
- StopToDirection 用于停止角色移动。当角色因减速值而移动时，此方法尤为实用。

==


==
- Motion还处理角色的跳跃动作，当条件允许时，`Jump()`, 将instruct 角色来perform a jump



### Driver[¶](https://docs.gamecreator.io/gamecreator/characters/scripting/character/#driver "Permanent link")
- 使用 Character Controller， 或者Navigation Mesh Agent，用于避障的导航网格代理，基于物理的刚性实体
- Unit 接收 Facing 和Motion的 locomotion information，physical translation 和 rotation


### Facing[¶](https://docs.gamecreator.io/gamecreator/characters/scripting/character/#facing "Permanent link")
- 控制身体（非头部）的朝向，默认情况下，所有角色在移动时才会旋转身体，此时==身体会朝向移动方向转动。==

- 在特定情况下，角色可能需要暂时朝向某个方向。例如用枪瞄准目标物体时，或与其他角色对话时。Game Creator内置的图层系统为这类情况提供了简洁的解决方案。

![[Pasted image 20251107111605.png]]
- 直接集成IUnitFacing ， 而不是TUnitFacing，其中已经内置现成的层级系统，因此无需重新编写相关代码

== 


== 

![[Pasted image 20251107111919.png]]
- 当删除某些key或者layer，将不会报错



- 调用 ==StartFacing()== 方法时，角色将==平滑旋转==至指定目标方向，直至调用 ==StopFacing()== 方法。
-  直接移除该层？

== 

### Animim[¶](https://docs.gamecreator.io/gamecreator/characters/scripting/character/#animim "Permanent link")

- 处理外观，到动作
- 该部分需要一个Animator 组件

![[Pasted image 20251107112859.png]]

- 默认系统自带一组过程动画，并在（如呼吸和用力）上叠加播放
- 能产生细微但连贯的动态效果。可通过HeartRate（心率）、Exertion（用力程度）和Twitching（抽搐）属性调整呼吸频率和用力强度。
- can be modified using the ==`HeartRate`, `Exertion` and `Twitching`== proprerties.


## Change Model[¶](https://docs.gamecreator.io/gamecreator/characters/scripting/character/#change-model "Permanent link")

- 包含FBX的prefab
GameObject instance = character.ChangeModel(prefab, default);