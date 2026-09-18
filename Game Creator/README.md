# Game Creator - Visual Scripting Framework

## Overview / 概述

**EN:** Game Creator is a comprehensive visual scripting framework for Unity that enables no-code game development. Create complex gameplay mechanics, character behaviors, and interactive systems without writing code.

**CN:** Game Creator 是 Unity 的综合可视化脚本框架，支持无代码游戏开发。无需编写代码即可创建复杂的游戏机制、角色行为和交互系统。

---

## What is Game Creator? / 什么是 Game Creator？

**EN:**
Game Creator provides a visual, node-based system for creating game logic through:
- **Triggers** - Events that activate actions (on click, on collision, etc.)
- **Actions** - Operations that execute in sequence
- **Conditions** - Logic gates for decision making
- **Variables** - Data storage and manipulation
- **State Machines** - Complex behavior management

**CN:**
Game Creator 提供基于节点的可视化系统来创建游戏逻辑：
- **触发器** - 激活动作的事件（点击时、碰撞时等）
- **动作** - 按顺序执行的操作
- **条件** - 用于决策的逻辑门
- **变量** - 数据存储和操作
- **状态机** - 复杂的行为管理

---

## Core Systems / 核心系统

### 1. Game Creator Core / 核心系统
Basic framework components and visual scripting tools.

基础框架组件和可视化脚本工具。

[View Core Documentation](./1%20GameCreator)

**Key Features / 主要功能:**
- Character system
- Camera system
- Visual scripting
- Trigger and action system

### 2. Inventory System / 库存系统
Complete inventory management with items, bags, and merchants.

完整的库存管理，包括物品、背包和商人。

[View Inventory Documentation](./2%20Inventory)

**Key Features / 主要功能:**
- Item creation and properties
- Equipment system
- Currency management
- Merchant shops
- Crafting/tinkering

### 3. Stats System / 属性系统
Character attributes, classes, and progression.

角色属性、职业和进度系统。

[View Stats Documentation](./4%20Stats)

**Key Features / 主要功能:**
- Character classes
- Attributes and traits
- Leveling system
- Status effects

### 4. Quest System / 任务系统
Quest creation and task management.

任务创建和任务管理。

[View Quest Documentation](./5%20Quest)

**Key Features / 主要功能:**
- Quest creation
- Task tracking
- Quest chains
- Rewards system

### 5. Shooter Module / 射击模块
FPS and TPS shooting mechanics.

第一人称和第三人称射击机制。

[View Shooter Documentation](./8%20Shooter2)

**Key Features / 主要功能:**
- Weapon system
- Aiming and sights
- Reload mechanics
- Projectile system

### 6. Melee Module / 近战模块
Melee combat system with skills and combos.

包含技能和连招的近战战斗系统。

[View Melee Documentation](./9%20Melee)

**Key Features / 主要功能:**
- Weapon system
- Skill system
- Combo chains
- Reactions and parrying

### 7. Traversal Module / 移动模块
Advanced character movement and parkour.

高级角色移动和跑酷系统。

[View Traversal Documentation](./10%20Traversal)

**Key Features / 主要功能:**
- Climbing system
- Vaulting
- Ledge grabbing
- Advanced movement

---

## Quick Start / 快速开始

### Installation / 安装

**EN:**
1. Import Game Creator from Unity Asset Store
2. Install required dependencies (if any)
3. Open the Game Creator welcome window
4. Follow the setup wizard

**CN:**
1. 从 Unity Asset Store 导入 Game Creator
2. 安装所需依赖项（如果有）
3. 打开 Game Creator 欢迎窗口
4. 按照设置向导操作

### Creating Your First Interaction / 创建第一个交互

**EN:**
1. Add a **Trigger** component to a GameObject
2. Choose a trigger type (e.g., "On Start", "On Click")
3. Add **Actions** to the trigger (e.g., "Move Character", "Play Animation")
4. Test in Play mode

**CN:**
1. 向 GameObject 添加 **Trigger** 组件
2. 选择触发器类型（例如"开始时"、"点击时"）
3. 向触发器添加 **Actions**（例如"移动角色"、"播放动画"）
4. 在播放模式下测试

---

## Visual Scripting Basics / 可视化脚本基础

### Triggers / 触发器

**EN:**
Triggers detect events and activate actions:
- **On Start** - Executes when the scene loads
- **On Click** - Executes when clicked
- **On Collision** - Executes when objects collide
- **On Key Down** - Executes when a key is pressed
- **On Variable Change** - Executes when a variable changes

**CN:**
触发器检测事件并激活动作：
- **开始时** - 场景加载时执行
- **点击时** - 点击时执行
- **碰撞时** - 对象碰撞时执行
- **按键时** - 按下键时执行
- **变量改变时** - 变量改变时执行

### Actions / 动作

**EN:**
Actions perform operations in sequence:
- Character actions (move, jump, play animation)
- Camera actions (switch shots, shake, zoom)
- Audio actions (play sound, music control)
- Variable actions (set, increment, compare)
- Flow control (wait, loop, conditions)

**CN:**
动作按顺序执行操作：
- 角色动作（移动、跳跃、播放动画）
- 相机动作（切换镜头、抖动、缩放）
- 音频动作（播放声音、音乐控制）
- 变量动作（设置、递增、比较）
- 流程控制（等待、循环、条件）

### Conditions / 条件

**EN:**
Conditions evaluate logic and branch execution:
- Compare variables
- Check player state
- Evaluate distances
- Test inventory contents

**CN:**
条件评估逻辑并分支执行：
- 比较变量
- 检查玩家状态
- 评估距离
- 测试库存内容

---

## Best Practices / 最佳实践

**EN:**
1. **Organize with Comments** - Use descriptive names for triggers and actions
2. **Use Variables** - Store reusable values in global or local variables
3. **Modular Design** - Break complex logic into smaller triggers
4. **Test Frequently** - Run play mode often to catch issues early
5. **Use Conditions** - Add logic gates to make behaviors dynamic

**CN:**
1. **使用注释组织** - 为触发器和动作使用描述性名称
2. **使用变量** - 在全局或局部变量中存储可重用值
3. **模块化设计** - 将复杂逻辑分解为更小的触发器
4. **频繁测试** - 经常运行播放模式以尽早发现问题
5. **使用条件** - 添加逻辑门使行为动态化

---

## Common Workflows / 常见工作流程

### Character Movement / 角色移动
1. Add Character component to a GameObject
2. Configure input settings
3. Add camera controller for third-person view
4. Test movement and adjust parameters

### Interactive Objects / 交互对象
1. Add collider to object
2. Add "On Interact" trigger
3. Add actions (play sound, change material, spawn item)
4. Configure interaction prompt

### Save System / 保存系统
1. Define which data to save (variables, inventory, etc.)
2. Add save/load actions to menu
3. Test save persistence across sessions

---

## Performance Tips / 性能提示

**EN:**
- Use **Events** for cross-object communication instead of Update loops
- **Cache** references to frequently used components
- Use **Pooling** for frequently spawned objects
- Optimize trigger conditions to avoid unnecessary checks
- Profile your game regularly

**CN:**
- 使用 **事件** 进行跨对象通信而不是 Update 循环
- **缓存** 频繁使用的组件引用
- 对频繁生成的对象使用 **池**
- 优化触发器条件以避免不必要的检查
- 定期分析游戏性能

---

## Integration with Code / 与代码集成

**EN:**
Game Creator can be extended with custom C# scripts:
- Create custom actions
- Add new trigger types
- Define custom conditions
- Extend existing modules

See the Visual Scripting documentation for details on creating custom components.

**CN:**
Game Creator 可以通过自定义 C# 脚本扩展：
- 创建自定义动作
- 添加新的触发器类型
- 定义自定义条件
- 扩展现有模块

有关创建自定义组件的详细信息，请参阅可视化脚本文档。

---

## Resources / 资源

**EN:**
- [Official Documentation](https://docs.gamecreator.io/)
- [Community Forum](https://forum.gamecreator.io/)
- [Video Tutorials](https://www.youtube.com/c/GameCreatorUnity)
- [Discord Community](https://discord.gg/gamecreator)

**CN:**
- [官方文档](https://docs.gamecreator.io/)
- [社区论坛](https://forum.gamecreator.io/)
- [视频教程](https://www.youtube.com/c/GameCreatorUnity)
- [Discord 社区](https://discord.gg/gamecreator)

---

## System Requirements / 系统要求

**EN:**
- Unity 2021.3 LTS or later
- Game Creator 2.x package

**CN:**
- Unity 2021.3 LTS 或更高版本
- Game Creator 2.x 包

---

## License / 许可证

**EN:**
Game Creator is a commercial asset available on the Unity Asset Store. Refer to the Asset Store license for usage terms.

**CN:**
Game Creator 是 Unity Asset Store 上提供的商业资产。有关使用条款，请参阅 Asset Store 许可证。

---

## Support / 支持

**EN:**
For technical support, bug reports, and feature requests:
- Visit the official documentation
- Post in the community forum
- Contact support through the Asset Store

**CN:**
技术支持、错误报告和功能请求：
- 访问官方文档
- 在社区论坛发帖
- 通过 Asset Store 联系支持
