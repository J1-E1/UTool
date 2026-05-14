- Game Creator的内置动画建立在Unity的Mecanim之上
- 增加了**Gestures** and **States**，不要额外的将它们放在Animator Controller graph中

![[Pasted image 20250805212902.png]]

### Gesture手势
- 播放一次就会从Animation grah中移除；例如挥拳，播放一次后将其从当前手势中移除

### States 状态
- 先缓缓播放的动画，例如角色坐在椅子上，角色蹲着移动
	- **Animation States**： 重复播放一个动画状态，直到停止
	- **Locomotion States**： 更加复杂，来反应特定的参数，例如角色的速度，可以blend或者transition
- _Create_ → _Game Creator_ → _Characters_ → **_Animation State_**
### Animation States

- ==单个动画剪辑，loop播放，直到被告知停止并混合==
	- 例如一个角色正在循环播放坐在椅子上的动画，这就是一个state状态
	- 需要提供一个Animation State
![[Pasted image 20250805224349.png]]

- Mask 用于遮罩
- Entry，用于进入和退出部分可选字段，退出当前state需要做的内容，比如拔剑

State存在一个Properties属性部分，用来修改Character上的Linear和Angular speed等
![[Pasted image 20250806133552.png]]
- 这样的设置允许修改移动speed通过state本身
- Running State === Layer 1 == Speed 10
- Walking State === Layer 2 == Speed 5
- Running 先进行，然后是Walk，之后将其速度修改5
![[Pasted image 20250806133702.png]]
### Locomotion States

- 更加复杂的state会对特定参数做出反应，如speed等，多个片段会混合，过渡

![[Pasted image 20250806133916.png]]
- **基本状态：**有一个空闲和一个 8 轴方向动画剪辑字段用于移动
- **完整状态：**有一个空闲和一个 16 轴方向动画剪辑字段用于移动：8 个用于半速移动，另外 8 个用于全速移动。
![[Pasted image 20250806134747.png]]
![[Pasted image 20250807093112.png]]
### Layers图层

- 每个状态都会被分配一个图层编号，播放动画是，编号越高，优先级越高
![[Pasted image 20250806135034.png]]
- 10 -2 -1

- 建议添加，“删除时”的过渡时间，以便新动画和底层动画平滑融合
![[Pasted image 20250806135146.png]]

- ==手势Gesture动画始终高于任何状态==

### Weight权重

- 新动画可以按照百分比于堆栈下播放的任何其他动画混合
![[Pasted image 20250806135410.png]]

### 进入状态

![[Pasted image 20250806135501.png]]
- Character来引用Action进入游戏橘色状态
- State Type决定时 _(Animation Clip)_、状态资源**(** _State_ asset) 还是运行时动画控制器 (Runtime Animation Controller)
- Layer，确定此状态在角色图层堆栈中占据哪个图层，默认Blend Mode设置为Blend，或者时Additive叠加正在播放的动画之上
- Delay为延迟几秒
- Speed为播放速度
- Weight为播放的权重，1时动画按照原样播放，较低的值郧西任何先前的动画渗透，并和较低层中正在播放的任何动画之间混合在一起
- 过渡，淡入所需要的时间
### 退出状态

![[Pasted image 20250806135940.png]]
