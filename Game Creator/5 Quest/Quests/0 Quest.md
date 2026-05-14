
- Quest Asset包含一系列的Tasks，需要按照顺序来完成

![[Pasted image 20260327222505.png]]

- 不太确定以上的内容需要完成什么
- 创建一个Quest asset， Create → Game Creator → Quests → Quest.

![[Pasted image 20260327222600.png]]


---
## Overview

- 包括整体的3个部分， 开头有3个部分


---

- 一些基本的信息，Name，Description等，同时还有Color和Sprite等
- Type：决定Quest是隐藏的还是普通的逻辑
- Hidden Quests，也许是成就系统等

![[Pasted image 20260327222946.png]]


- order，即优先级决定了其资源的等级
- ID决定唯一表示符号， 使用点击的按钮来决定其唯一值的问题
![[Pasted image 20260327223311.png]]

- 任务层级结构，控制着任务的运行方式
![[Pasted image 20260327223110.png]]

- 一系列指令，任务改变时，这些指令将会被执行
- 例如完成某些任务完成后，指令将被执行
![[Pasted image 20260327223423.png]]


![[Pasted image 20260327223502.png]]


---
## States

- 似乎需要Quest Activate一个Quest
- Journal， 激活任务，下一个子任务也会被激活，重复执行，直到所有root 任务被完成

![[Pasted image 20260327223713.png]]

- An **Active** quest can then either transition to **Inactive**,
- - **Completed**
- **Abandoned**
- **Failed**
![[Pasted image 20260327223811.png]]
