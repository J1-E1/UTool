# Cinemachine - Advanced Camera System

## Overview / 概述

**EN:** Cinemachine is Unity's advanced camera system that provides procedural camera behavior and dynamic shot composition.

**CN:** Cinemachine 是 Unity 的高级相机系统，提供程序化相机行为和动态镜头构图。

---

## Core Architecture / 核心架构

### Three Main Components / 三个主要组件

Cinemachine consists of three core parts:

Cinemachine 由三个核心部分组成：

#### 1. Unity Camera / Unity 相机

**EN:**
- The physical camera that captures the scene
- Only one Unity Camera is needed in your setup
- Acts as the rendering endpoint for all virtual cameras

**CN:**
- 捕捉场景的物理相机
- 设置中只需要一个 Unity 相机
- 作为所有虚拟相机的渲染端点

#### 2. Cinemachine Brain / Cinemachine 大脑

**EN:**
- Component attached to the Unity Camera
- Monitors all active Cinemachine Cameras in the scene
- Handles smooth transitions between different camera perspectives
- Timeline sequences have higher priority than Cinemachine Brain settings

**CN:**
- 附加到 Unity 相机的组件
- 监控场景中所有活跃的 Cinemachine 相机
- 处理不同相机视角之间的平滑过渡
- Timeline 序列的优先级高于 Cinemachine Brain 设置

#### 3. Cinemachine Cameras / Cinemachine 虚拟相机

**EN:**
- One or more virtual cameras in the scene
- Dynamically override Unity Camera properties and behavior when active
- Can be managed and extended with additional Cinemachine components
- Switch between cameras based on game state and priorities

**CN:**
- 场景中的一个或多个虚拟相机
- 激活时动态覆盖 Unity 相机的属性和行为
- 可以通过额外的 Cinemachine 组件进行管理和扩展
- 根据游戏状态和优先级在相机之间切换

---

## How It Works / 工作原理

**EN:**
The Cinemachine Brain continuously evaluates all virtual cameras and blends between them based on priority. When a virtual camera becomes active, it controls the Unity Camera's position, rotation, and other properties.

**CN:**
Cinemachine Brain 持续评估所有虚拟相机，并根据优先级在它们之间进行混合。当虚拟相机激活时，它会控制 Unity 相机的位置、旋转和其他属性。

---

## Camera Transitions / 相机过渡

**EN:**
- **Instant:** Immediate cut to the new camera
- **Timed:** Smooth blend over a specified duration

**CN:**
- **即时：** 立即切换到新相机
- **定时：** 在指定时间内平滑混合

---

## Quick Start / 快速开始

**EN:**
1. Add Cinemachine Brain component to your Main Camera
2. Create a Cinemachine Virtual Camera in the scene
3. Configure follow and look-at targets
4. Adjust camera properties and behaviors

**CN:**
1. 将 Cinemachine Brain 组件添加到主相机
2. 在场景中创建 Cinemachine 虚拟相机
3. 配置跟随和观察目标
4. 调整相机属性和行为

---

## Resources / 资源

- [Official Unity Documentation](https://docs.unity3d.com/Packages/com.unity.cinemachine@latest)
- [Unity Learn Cinemachine Tutorials](https://learn.unity.com/search?k=cinemachine)

---

## Additional Documentation / 其他文档

- [Pan & Tilt Controls](./Reference/Pan%20Tilt.md) - Advanced camera control techniques
