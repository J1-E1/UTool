# UTool - Unity 工具与插件知识库

## Unity 开发工具和框架的综合文档

![Unity](https://img.shields.io/badge/Unity-6.0%2B-blue.svg)
![Documentation](https://img.shields.io/badge/docs-综合文档-brightgreen.svg)
![Language](https://img.shields.io/badge/language-EN%20%7C%20CN-orange.svg)
![License](https://img.shields.io/badge/license-教育用途-lightgrey.svg)
![Status](https://img.shields.io/badge/status-活跃-success.svg)

[English](./README.md) | 简体中文

Unity 开发的精选知识库，涵盖流行的工具、插件和框架。本仓库提供组织化的笔记、API 参考、配置指南和常用 Unity 资产的最佳实践。

## 目录

- [组件](#-组件)
- [快速开始](#-快速开始)
- [文档结构](#-文档结构)
- [贡献](#-贡献)
- [许可证](#-许可证)

## 🎮 组件

### 相机与摄影

**[Cinemachine](./Cinemachine)** - 高级虚拟相机系统
- 程序化相机行为和镜头构图
- 基于优先级混合的虚拟相机
- Timeline 集成和平滑过渡

### 游戏开发框架

**[Game Creator](./Game%20Creator)** - 可视化脚本框架
- 使用触发器和动作进行无代码游戏开发
- 完整系统：库存、属性、任务、战斗
- 模块化架构，包含射击、近战和移动模块

### UI 框架

**[MlskyUI](./MlskyUI)** - 现代 UI 组件库
- 支持深色和现代主题
- 预构建组件：按钮、模态框、滑块
- 手柄支持和本地化

**[Radial Menu](./RadialMenu)** - 圆形菜单系统
- 可自定义的径向按钮布局
- 对象池提升性能
- 多种视觉样式

### 编程工具

**[UniTask](./UniTask)** - 零分配异步/等待
- 高性能异步操作
- Unity 特定的异步模式
- 取消令牌支持

### 美术与资产

**[Synty Studios](./Synty)** - 低多边形资产集合
- 模块化角色系统
- 环境和道具包
- 性能优化指南

## 🚀 快速开始

### 浏览文档

1. 从上面的列表导航到组件文件夹
2. 阅读 `README.md` 了解概述和快速开始
3. 探索详细的文档文件了解具体功能
4. 查看代码示例和实现模式

### 组件选择指南

- **相机工作** → Cinemachine
- **快速原型** → Game Creator
- **UI 系统** → MlskyUI 或 Radial Menu
- **异步编程** → UniTask
- **美术资产** → Synty Studios

## 📂 文档结构

每个组件遵循以下组织结构：

```
Component/
├── README.md              # 概述、功能、快速开始
├── SubSystem/             # 详细功能文档
│   └── feature.md
└── images/                # 截图和图表
    └── descriptive-name.png
```

### 文档特性

- **双语内容** - 关键概念使用中英文解释
- **代码示例** - 带有内联注释的即用代码片段
- **视觉参考** - UI 和配置的截图
- **最佳实践** - 性能提示和常见模式

### Unity 版本兼容性

本文档主要面向 **Unity 6.0+**，但各个组件有不同的版本要求：

| 组件 | 最低 Unity 版本 | 说明 |
|------|----------------|------|
| Cinemachine | 2021.3 LTS+ | Unity 6.0+ 内置包 |
| Game Creator | 2021.3 LTS+ | 需要现代 Unity 功能 |
| MlskyUI | 2020.3 LTS+ | 兼容较旧版本 |
| RadialMenu | 2019.4 LTS+ | 广泛兼容性 |
| UniTask | 2020.3 LTS+ | 需要 .NET Standard 2.1 |
| Synty 资产 | 2019.4+ | 通用兼容性 |

**推荐：** 使用 Unity 2021.3 LTS 或 Unity 6.0 以获得所有组件的最佳兼容性。

## 🤝 贡献

欢迎贡献！添加文档时：

1. 遵循现有的结构和命名约定
2. 在适当的地方包含中英文内容
3. 为图片使用描述性名称（而不是时间戳）
4. 提交前测试所有代码示例
5. 添加新组件时更新主 README

## 📝 许可证

本仓库包含教育性笔记和参考资料。请尊重所记录工具和资产的原始许可证。

---

**注意：** 这是一个文档仓库。实际的资产包必须从其官方来源获取（Unity Asset Store、GitHub 等）。

---

<p align="center">
  <sub>为 Unity 开发者社区构建</sub>
</p>
