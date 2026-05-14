### 装备
![[Pasted image 20250809092706.png]]
![[Pasted image 20250809092745.png]]
 
 - 装备武器，与inventory的内容类似，所以请注意代码是否可以重用
 - Maybe Attach prefab这个操作

### 射击

![[Pasted image 20250809093421.png]]
- pull fire trigger 和 Release fire Trigger
- 根据指令的不同，武器会做出不同的反应
- 需要注意多武器下的影响

![[Pasted image 20250809093446.png]]

## Reload
![[Pasted image 20250809093633.png]]
- 可在AI方面使用

## Jamming 干扰
![[Pasted image 20250809093657.png]]

- 武器卡壳时，卡克的武器将无法重新装填或射击
- 需要排除卡壳问题，并得到修复
- Fix None会修改堵塞，命令会启动动画并修复堵塞问题


### Leaning 倾斜
![[Pasted image 20250809093915.png]]

- 角色可可以向左，或者向右倾斜从角落中射击，这些斜视叫可在sight中设置
- 回复设置为0度的character Lean指令