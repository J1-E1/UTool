![[Pasted image 20250808225022.png]]
- Can Shoot 表示此瞄准器的武器是否可射击
- Priority：优先级，当同时持有两件武器时比如手电筒，和手枪，手枪应该具有更高的优先级
- Smooth Time：平滑时间，它决定了武器瞄准时的延迟程度，如果禁用，不会有任何延迟，角色会立即瞄准目标点

state
![[Pasted image 20250808225453.png]]
- 混合了Weapon 和Sight States，Animation state ， sight state 可以mask 上升的body用以只控制上半生的情况

Instruction
- On Enter 和 On Exit
- 当需要设置一个Over-the- shoulder的camer，可能会所有field of view； 这可以在这个时候所缩小并由此来改变


### Aiming

- 当角色瞄准时使用Sight

![[Pasted image 20250808225952.png]]
- Acurray：精度，默认值为0，默写游戏会使得，腰射或者掩体盲射，的经度低于俯视瞄准
- Aim：表示瞄准时point在空间中是如何计算的

### 弹道

![[Pasted image 20250808231103.png]]

###  十字线
![[Pasted image 20250808231127.png]]