![[Pasted image 20251101100057.png]]

- 可以装备不同的game object 和Items 和 Currencies
- 有两种不同的背包
	- **List**，按顺序依次，每个物品占用的空间大小相同
	- **Grid**，每个物品占用一定数量的单元格，在库存网格视图中可以手动排列这些单元格


---

### Bag Options

- 最大重量，最大限制
- 如果设置了最大高度，则背包可容纳的物品数量也有限制
- 如果设置了最大重量，则当所有物品的重量总和超过最大值时，背包将被视为超载。

### Equipment

### Stock and Wealth
- 某些背包默认包含一定数量的物品和货币，比如商人
![[Pasted image 20251101101411.png]]
- “Add Stock” 会创建一个新的库存选项，并且Amount商品数量
- “Add Wealth”, 添加新的财富选项，并接受货币名称及其面值
![[Pasted image 20251101101717.png]]
- Bag 组件同样也可以变为随机战利品，建议使用战利品表，而不是库存选项

---

### Wearer[¶](https://docs.gamecreator.io/inventory/bags/#wearer "Permanent link")

The **Wearer** selector refers to the targeted game object that wears the **Bag**'s equipment. By default it is set to _Self_ because the **Bag** is usually attached along the **Character** component. However, if for some reason that is not the case, you can choose which character should be targeted as the equipment wearer.

- 穿戴背包装备的目标游戏对象，默认是self，自身
