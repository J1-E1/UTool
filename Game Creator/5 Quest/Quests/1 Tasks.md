
- 控制Quest
![[Pasted image 20260327225610.png]]

- Task：代表一个node，包含一系列的Subtasks，同时Subtasks也许会包含不同的Subtasks

![[Pasted image 20260327225734.png]]

- <mark style="background: #FFF3A3A6;">左边</mark>按键代表可以创建一个同级的任务节点，<mark style="background: #FFF3A3A6;">右边</mark>按钮创建一个子任务、

![[Pasted image 20260327230744.png]]
- 可以移动不同的Task


---
## Task States

- 有5个基本的state逻辑
- **Inactive:** The default state.
- **Active:** An active task is currently being executed and can transition to a finished state.
- **Completed:** The task has been successfully resolved.
- **Abandoned:** The task has been abandoned, with similar effects to the failed state.
- **Failed:** The task has been failed.

![[Pasted image 20260327231042.png]]


- 有几个固定的规则定义
	- INACTIVE 只能转换为ACTIVE状态
	- ACTIVE可以转换为INACTIVE的状态
	- _Finished_只能转换为INACTIVE状态


---
## Task Anatomy

![[Pasted image 20260327231808.png]]

### Settings

- Completion Mode决定Task是否完成，并决定是否有任何的子任务
- Is Hidden, 这块区域表示是否考虑是否时Hidden的，【这里只是决定是不是在UI中显示】
- **Name** and **Description**
-  **Color** and **Sprite**
using Sprite

![[Pasted image 20260327232147.png]]

### Counters

#### No Counter

- 默认情况下，任务设置为_“无” 。这意味着必须使用__“完成任务”_指令才能完成任务。但是，任务也可以包含一个计数器，当任务值与计数器值相等时，任务会自动完成
![[Pasted image 20260327232515.png]]

#### Value Counter

- 值计数器， 当选项设置为一个计数，则表示这里完成任务需要达到的值
- 比如反击击杀任务，表明npc要求玩家击杀一定数量的敌人，计算需要计算当前执行人数量
![[Pasted image 20260327232407.png]]

#### Property Counter

- Property允许计数达到一定数量后自动完成任务，该值与动态属性同步
- 也许需要一个Global值来设置从而计算相关变化

![[Pasted image 20260327232824.png]]


- 也许需要一个Global值来设置从而计算相关变化
![[Pasted image 20260327233032.png]]

### Instructions

- A **Task**, just like a **Quest**, has a collection of **Instructions** that can be executed whenever a task changes its state.
- 像Task一样不同状态下，指令可以执行

## Running Subtasks


- 具有一个或者多个子任务，并更具字段来决定其是否是”已完成“、”已放弃“或者”放弃“
![[Pasted image 20260327233435.png]]

### Subtasks in Sequence

- **子任务**完成后，下一个同级任务将被激活。此过程重复进行，直至所有**子任务**完成，此时**主任务**也将自动完成。
![[Pasted image 20260327233549.png]]


- 如果任何子**任务**被放弃或失败，则该**任务**也会相应地被放弃或失败。
![[Pasted image 20260327233628.png]]


### Subtasks in Combination

![[Pasted image 20260327233849.png]]

### Any Subtask

![[Pasted image 20260327233717.png]]

- 任何任务一旦激活，就会立即激活所有子任务
- 一旦任何子**任务**完成，该**任务**也会自动完成，其余子**任务**仍保持活动状态。

![[Pasted image 20260327233829.png]]


### Manual

- 不激活任何Subtasks

![[Pasted image 20260327233906.png]]

![[Pasted image 20260327234051.png]]

