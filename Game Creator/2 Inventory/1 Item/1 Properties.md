
- 属性是构成物品的可变值，例如，物品的攻击力、耐久度或是否施加特殊效果（例如灼烧）
![[Pasted image 20251031211336.png]]

### Creating a new Property

- 如果要添加property，直接点击property即可
![[Pasted image 20251031211514.png]]

- **Property ID** ：唯一的属性id， 好记些
- 是否隐藏，是否再用户界面中隐藏
== optional

- **Icon** ： 在用户界面提供一个可见的 sprite图
- **Color** ： 为属性指定颜色
- **Number** ： 游戏中的可变值，增加提升属性值
- **Text** ： 动态值，表示用于游戏内名称

###  Inheriting Properties

- 继承开关将自动继承所有父级别的属性，通过左侧的开关字段来更新覆盖继承属性的值
- 继承关系， 比如基础的“盾牌”， 然后子类，继承”木盾“，钢盾，并修改不同的属性值

![[Pasted image 20251031213911.png]]


### Hiding Properties

![[Pasted image 20251031214531.png]]
- 如果hide某些属性值，用户界面中只会出现部分值
- 比如欧协item有一个 is-metal属性，来决定它是否为金属