
https://docs.gamecreator.io/inventory/items/equipping/

---

- **Is Equippable** 标签必须勾选，从而允许设置以下的参数
- Can Equip会首先检测在装上装备的时候
- Prefab中设置的会被实例化

![[Pasted image 20251101095202.png]]


---

- 尝试将**物品**装备到已被其他**物品**占据的装备栏位时，当前装备的物品会自动卸下，以便装备新**物品。**
- Unenquip时会执行 **On Unequip** instruction list.

![[Pasted image 20251101095605.png]]

---

= 在执行Can Equip，On Equip， On Unequip Instruction的时候

- Self属性引用代表的时, gameObject， item被装备的和卸下的
- Traget代表，穿上Bag的那个Gameobject


---

