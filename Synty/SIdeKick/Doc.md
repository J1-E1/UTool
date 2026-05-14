
- 可以通过load重新载入角色并来修改， save 来保存
![[Pasted image 20251022093122.png]]


- 分别选用Head，UpperBody，LowerBody，这些部件可以组成角色
- Body Type Presets: 体型包含性别和提醒的组合
- Color Presets: 颜色预设为物种、服饰

![[Pasted image 20251022101628.png]]


- 点击Parts Tab用于调整不同的细节部分
![[Pasted image 20251022102329.png]]

- 调整角色的身材等，通过Body Tab
![[Pasted image 20251022102441.png]]

- 修改颜色 通过 Color Tab
![[Pasted image 20251022102512.png]]


### Demo 场景


表情
- Project location - Assets/Synty/SidekickCharacters/_Scenes/Sidekick_Facial_Demo
- 通过调整角色表情来增加表现

### 驱动角色

表情
- Assets\Synty\SidekickCharacters\Samples\Animations
- 拥有若干个图层，Emotion_Additive 和 FaceAnim_NeutralCycle
- Emotion_Additive，情绪添加是
- FaceAnim_NeutralCycle ： loop，用于面部运动的循环覆盖动画


![[Pasted image 20251022103314.png]]
![[Pasted image 20251022103707.png]]


### Character Properties 角色属性

- 角色的Parts被分为3个部分，Head，upper Body， Lower Body， 每个都可以通过Parts Tab来做更多的微调

- 在某些情况下，单一部分会被替代，比如角色配置海盗假腿，有些东西就不需要了

![[Pasted image 20251022105424.png]]
- 如上图，Leg和foot就不需要了，被替代为Peg leg


Body Shape
- 将bake down Skinned mesh render 红配置网格渲染器

Color Sections

- 有很多颜色的部分都可以修改包括眼球等
![[Pasted image 20251022110703.png]]


### Runtime Character Creation

- SidekickRuntime.cs，包括所有的运行时功能
- Assets/Synty/SidekickCharacters/Scripts/Runtime/API)
- 这是一个示例类，用于追踪创建Sidekick角色所需的变量
- 包括两个必填参数，和2个可选参数
![[Pasted image 20251022111030.png]]


#### Basic Character Creation Workflow

- 具体操作是调用CreateCharacter函数，如果想要model并保持有single mesh，为CreateCharacter 增加一个参数combineMesh = True
- 若保持部件分离，则将其设置为false
- 合并过程将会是耗时的


### Third party assets

- UniVRM