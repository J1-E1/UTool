
- 附加该组件在摄像机上，可以关联一个摄像机镜头引用
- 此Shot可以在运行时更改，决定摄像机的行为

![[Pasted image 20260301104300.png]]

- Main Camera 可以被全局访问


## Creating the Main Camera[¶](https://docs.gamecreator.io/gamecreator/cameras/controller/#creating-the-main-camera "Permanent link")

![[Pasted image 20260301104357.png]]

- Main Camera 组件拥有3个不同的块 Game Time ； Shot； Avoid Clipping
- **Avoid Clipping** ： 允许摄像机避免穿过场景的几何体。

## Transition to a new Shot[¶](https://docs.gamecreator.io/gamecreator/cameras/controller/#transition-to-a-new-shot "Permanent link")

== 
- 将角色控制器从一个镜头切换到另一个镜头， 使用 **Change Shot** instruction

![[Pasted image 20260301105012.png]]

- Change Shot to， 使用更改镜头的指令
- Duratioin 用于控制镜头的切换所需时间， Game Creator 会自动处理相关的剩余部分逻辑