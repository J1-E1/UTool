

### Weapons

- 如果一把有多种射击模式的武器，例如，一把可以发射榴弹的突击步枪
  - 创建两个**Weapon**资源，并将其放在同一个Prop上
- *Create → Game Creator → Shooter → Weapon*
![[Pasted image 20250808194537.png]]


### Weapon Data

![[Pasted image 20250808195611.png]]

- 首先是一些基本的武器数据， 标题，描述，图标，颜色
![[Pasted image 20250808195710.png]]

- Hit Reaction ：可选字段， 该武器集中后，会施加反应； 不设置则没有
- ID：ID默认位置，装备武器时的ID也要不同

- Weapon 装备时，会进入 Animation State状态，这些State会包括，Enter Gesture，可以设置拔枪，或者瞄准等
- Layer字段，标记其state在哪一层播放

### Weapon Mode
![[Pasted image 20250808202313.png]]
- 用于设置武器的某些内容，枪口 ，瞄准点，弹壳弹出等
- 枪口：蓝色点表示
- 瞄准点，橘色使用瞄准点作为最佳瞄准位置，红色表示
![[Pasted image 20250808202334.png]]
![[Pasted image 20250808202428.png]]

###  Magazine 弹夹
![[Pasted image 20250808202610.png]]

- 用于配置可扩展的字段，用于配置弹药
- Auto Reload：是否自动装填弹药等（同时需要考虑下==敌人AI==）
### 枪口
![[Pasted image 20250808203020.png]]
- 使用工具来配置更加合理

### Fire 开火
![[Pasted image 20250808203613.png]]
**Projectiles per Shot** ： 决定每次射击将会有多少子弹
**Cartridges per Shot** ： 每次射击的弹药数量

### Projectile
![[Pasted image 20250808204200.png]]

### Sights 瞄准镜头

![[Pasted image 20250808211608.png]]
- 用于决定武器的瞄准模式
- 一件武器可以有多个瞄准入口，每个入口允许橘色改变其瞄准模式（或姿势）

Scope Through
- 仅在瞄准器sight资源使用Human IK生物力学选项时可用
- 也许还需要探究以下
![[Pasted image 20250808212006.png]]


| col1                  | col2                                                                                                                                        | col3                                        |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| **Can Shoot**   | - 使用的这个Sight是可射击的还是如何；<br />- 如果是类似拔出武器的，非射击，设置为False即可<br />- 可以设计一个Cover保护机制，可以瞄准并射击 | ![1746111428505](image/doc/1746111428505.png) |
| Priority              | - 装备的先后，                                                                                                                              |                                             |
| **Smooth Time** | - 平滑事件，决定瞄准的滞后程度<br />- 禁用，不会有任何延迟，角色会立刻瞄准                                                                  |                                             |
| State                 | - State字段允许，允许进入Animation State，当切换Sight的时候<br />- use Avatar Mask<br />- Mix Weapon states and Sight states                |                                             |
| On Enter， On Exit    | - 在切换为Sight时候的回调<br />- 在使用肩上摄像头缩小视野范围时，进入时应缩小视野，退出时则恢复默认值。                                     |                                             |
### 装填Reload
![[Pasted image 20250808220619.png]]

![[Pasted image 20250808215438.png]]
- State， 角色可以进入动画状态，状态字段，允许选择一个状态，和哪个图层（大多数情况下，可以忽略，每个Reload资源都会播放自己的动画资源，并覆盖state）
- 装填左轮子弹的时候考虑到了可以使用state

### Weapon Animation
![[Pasted image 20250808221716.png]]
- 可能在某些特殊的地方需要使用这些动画，通常不需要

### Instruction指令
### Ammo

![1746111015616](image/doc/1746111015616.png)

- 标题，描述，图标，字段，等常用值，只在界面中表示信息，对游戏无影响
- infinite，默认状态下，该值代表武器的弹药总量
-
