# Cinemachine - 高级相机系统

![Unity](https://img.shields.io/badge/Unity-2021.3%20LTS%2B-blue.svg)
![Cinemachine](https://img.shields.io/badge/Cinemachine-3.x-green.svg)
![Status](https://img.shields.io/badge/status-稳定-success.svg)
![Documentation](https://img.shields.io/badge/docs-完整-brightgreen.svg)

[English](./README.md) | 简体中文 | [返回主页](../README-CN.md)

## 概述

Cinemachine 是 Unity 的高级相机系统，提供程序化相机行为和动态镜头构图。

---

## 核心架构

Cinemachine 由三个核心组件组成：

#### 1. Unity 相机
- 捕捉场景的物理相机
- 每个设置只需一个
- 所有虚拟相机的渲染端点

#### 2. Cinemachine 大脑
- 附加到 Unity 相机的组件
- 监控所有活跃的虚拟相机
- 处理平滑过渡
- Timeline 优先级更高

#### 3. 虚拟相机
- 一个或多个定义行为的相机
- 激活时覆盖 Unity 相机
- 根据优先级和游戏状态切换

---

## 工作原理

Cinemachine Brain 评估所有虚拟相机并根据优先级进行混合。

---

## 相机过渡

- **即时：** 立即切换
- **定时：** 指定时间内平滑混合

---

## 快速开始

1. 将 Cinemachine Brain 添加到主相机
2. 在场景中创建虚拟相机
3. 配置跟随和观察目标
4. 调整相机属性

---

## 资源

- [官方文档](https://docs.unity3d.com/Packages/com.unity.cinemachine@latest)
- [Unity Learn 教程](https://learn.unity.com/search?k=cinemachine)
- [平移和倾斜控制](./Reference/Pan%20Tilt.md)
