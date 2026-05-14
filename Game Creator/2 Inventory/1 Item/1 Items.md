
- Items : 游戏中可添加至背包
- 包含名称描述、属性、视觉呈现及其他信息，用于制作、交易、使用和装备



### Items vs Runtime Items
- Item 是一个scriptable object，包括部分信息，如名称, weight, what Item Properties
- 运行时为一个item对象在场景中，可在游戏会话中保存，拥有特定物品示例的专属数值
![[Pasted image 20251031100343.png]]
> 剑的耐久度 ： 所有金属剑都将来自相同的物品定义。当你将金属剑交给玩家时，你是在创建一个金属剑的运行时物品，它可以拥有自己的独特属性值，例如随每次碰撞而减少的耐久度。

- Item ， Runtime 概念类似于， prefabs 和 Prefab Instances，前者作为模板，后者可生成多个实例

### 创建一个物品
![[Pasted image 20251031100542.png]]

- _Create → Game Creator → Inventory → Item_.

![[Pasted image 20251031100730.png]]



- ID值，用于物品的，唯一标识，当复制时，其上方会出现红色标识，表示存在两个相同ID的物品
- 重新生成即可
- Prefab字段用于将物品拖入实例化场景，若未提供预制题，物品将不会被实例化

### Inheritance 继承？
- 继承属性，允许Item从另一个继承值，如Properties，Sockets
- 继承关系示例图
  
  ![[Pasted image 20251031103148.png]]
### Information 信息？

- 用于定义Item的，name，描述，sprite，color
- 动态属性，其值可以进行本地化处理
![[Pasted image 20251031104207.png]]


### Shape

- 物品的With 和 Height，表明了在背包中占据的大小
- 同样表示了其重量，占据背包中多小（如果背包有最大重量限制）
- 最大堆叠数，此字段决定了相同物品可堆叠的最大数量
![[Pasted image 20251031104459.png]]

- 如果一个物品有多个Sockets，则Max Stack将会自动限制为1，（技术限制）


### Price 价格

- 一件物品的交易价格由 [Currency](https://docs.gamecreator.io/inventory/currencies/) 这个Asset来决定，这个值是一个总和，不包含任何折扣或修正值。

![[Pasted image 20251031104817.png]]
- 物品只能使用一种货币来交易
- 可附加物品价格，附加物品 + 改物品的自身价格 的总和; 例如剑 45 + 符文（20） = 附加剑后的的价值65(45 + 20)
![[Pasted image 20251031104922.png]]

### Properties 属性

- 属性是由一个名称表示的数据块，包含一个数值，一段文本
- 用于显示改项目的信息并在游戏中使用
![[Pasted image 20251031111854.png]]

- 常见的使用，定义攻击点数，定义攻击的点数为35
- 更多信息在 [Properties](https://docs.gamecreator.io/inventory/items/properties/)
![[Pasted image 20251031112044.png]]

### Sockets

- 插槽允许物品附加到其他物品上，可附加由继承关系决定

![[Pasted image 20251031112328.png]]
- 比如一个槽位接受，符文武平，那么所有继承该符文物品的内容都会被接受
- **[Sockets](https://docs.gamecreator.io/inventory/items/sockets/)** 查看这里更多的槽位信息

### Equipping

- 有些物品可以从背包中穿戴， 所以也许是用于穿戴时候的内容？
- 查看更多的**[Equipping](https://docs.gamecreator.io/inventory/items/equipping/)**的内容
![[Pasted image 20251031113039.png]]


### Usegae

- 允许定义可随时使用的实用物品行为
- behavior of an utility **Item** which can be used at any given time.
![[Pasted image 20251031133623.png]]
- 定义了可用物品的使用次数是否是有限的，也可以是无限的。
- Consume On Use 定义了武平在使用后是否被消耗

== 有限 和 无限
- 比如说生命药水使用一次就会被消耗
- 哨子可以多次使用
== 
- can use 会在使用物品时尝试运行判断（都是Condition的内容）
- On Use 当item是使用的，在“使用时”指令， 物品所属的带有背包组件的游戏对象

==
- 继承关系可以保证某些相同指令合并，以继承的方式来简化

### Crafting
- 组装部分可以定义部分的组合用以创建Items
- 同样也可以拆解item，来形成多个不同的ingredients
![[Pasted image 20251031140003.png]]