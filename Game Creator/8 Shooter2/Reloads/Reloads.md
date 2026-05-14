https://docs.gamecreator.io/shooter/reloads/


---
## Animation

- Animation 字段是是必填的，角色装弹时播放
- mask
- transition in， out， 允许角色平滑融入或者脱离当前的角色stance


---
## Reload Mode

![[Pasted image 20260320220940.png]]


![[Pasted image 20260320221039.png]]

- 这个change weapon 和 change character 似乎可以保持并存下里
- ？验证？

---
### Magazine Track

- 黄色
- 轨道用作方便的弹匣系统，可以无缝地创建一个新的弹匣（或任何游戏对象实例），并将其从角色的肢体移动到武器上。
- 黄色轨迹范围首先在指定的骨骼上实例化所选预制件的实例，然后在轨迹的末端将其重新父级化到武器的位置，同时平滑地平移和旋转到位。

![[Pasted image 20260320221827.png]]

![[Pasted image 20260320222030.png]]

- 首先在指定的骨骼上实例化prefab
-  Game Object property dropdown and selecting _Reloading Previous Magazine_ and _Reloading New Magazine_ respectively.
- ？似乎是直接做一change操作


---
### Quick-Reload Track

![[Pasted image 20260320215846.png]]

- ？Greeen track，允许可以装备可以quick reload

![[Pasted image 20260320215946.png]]

- 允许跳过active reloading 或者 pro reloading的操作
- 基于角色一个点击跳过的按钮
- Quick Reload ，点击按键，提前结束animation，然后reloaing完成
- 快速装弹尝试

- 请注意，如果“**尝试快速装弹”**指令在绿色范围之外运行，但在装弹操作期间运行，系统会将该尝试注册为快速装弹失败，并且动画将继续播放，直到完成或被其他操作取消为止。

![[Pasted image 20260320220442.png]]



---

### Instructions Track

![[Pasted image 20260320215254.png]]

- 第三条Track， 在不同的点位上设置instruction

![[Pasted image 20260320215454.png]]

- 这些instruction points，播放sound effects，change blend shape
- previous empty magazine or even ejecting shells.
- ？这些instruction的触发是如何执行的，如何与time关联

---

## Configuration

![[Pasted image 20260320215050.png]]

- Speed：reload animation happed的时候，reload animation的执行速度
- 


---

## Instructions

![[Pasted image 20260320214849.png]]

- 在**On Start** and **On Finish** instructions， 在开始和结束的reloading执行的时候
- ？实际何时执行，进度条中有什么内容