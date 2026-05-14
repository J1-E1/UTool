

---

- 创建一个Euqipment asset
- Create → Game Creator → Inventory → Equipment
![[Pasted image 20251101103218.png]]


---

- 一个装备Slot拥有一个 **Base Item** 和一个 **Bone** reference
- Base Item， 所有某个部位的装备基类
	- 例如Helmets继承Head，那这个槽位会允许所有的Head装备
	- 放在具体Bone位置上面

![[Pasted image 20251101103848.png]]


---

### Using the Equipment

- 将这个**Equipment** 连接到 **Bag**，从而让角色知道哪个槽位时允许的，并mapped到具体的那一个bone
- 当前Equipment拥有4个装备和3额外的可消耗装备
![[Pasted image 20260310221038.png]]

- 将这个Equipment放在这个Bag上面
![[Pasted image 20260310221222.png]]


- 当这个Equipment放在Bag之后，并将显示每一个Slot从而可以保证起被Override正确