# Radial Menu - 径向菜单系统

![Unity](https://img.shields.io/badge/Unity-2019.4%20LTS%2B-blue.svg)
![Status](https://img.shields.io/badge/status-稳定-success.svg)
![Documentation](https://img.shields.io/badge/docs-完整-brightgreen.svg)

[English](./README.md) | 简体中文 | [返回主页](../README-CN.md)

## 概述

Unity 的灵活径向菜单系统，具有直观的圆形按钮布局。非常适合武器轮盘、能力选择器和上下文菜单。

---

## 特性

- **可定制样式** - 多种视觉样式
- **动态生成** - 运行时创建菜单项
- **池系统** - 高效对象重用
- **灵活布局** - 可调整间距
- **输入无关** - 支持鼠标、触摸、手柄

---

## 快速开始

1. 导入 Radial Menu 包
2. 添加预制体到画布
3. 配置菜单选项
4. 分配按钮精灵和动作
5. 选择视觉样式

---

## 样式自定义

### 可用样式

- **空白样式** - 简约设计
- **主题样式** - 预设计主题
- **自定义样式** - 自定义设计

### 菜单选项

- 控制按钮数量
- 调整间距
- 配置半径和缩放
- 设置旋转和角度

---

## 按钮状态

- 正常 - 默认外观
- 高亮 - 鼠标悬停或聚焦
- 按下 - 主动点击
- 已选 - 当前选择
- 禁用 - 非活动

---

## 使用示例

```csharp
public class RadialMenuController : MonoBehaviour
{
    public RadialMenu radialMenu;
    
    void Start()
    {
        radialMenu.AddMenuItem("攻击", OnAttackSelected);
        radialMenu.AddMenuItem("防御", OnDefendSelected);
        radialMenu.BuildMenu();
    }
    
    void OnAttackSelected() => Debug.Log("攻击！");
}
```

---

## 常见用例

- 武器选择
- 能力轮盘
- 上下文菜单
- 库存快速访问
- 命令径向

---

## 最佳实践

1. 保持选项在 4-8 个
2. 使用清晰图标
3. 提供视觉反馈
4. 测试手柄输入

---

## 配置

- **按钮数量** - 按钮数量
- **半径** - 距中心距离
- **起始角度** - 初始旋转
- **间距** - 按钮间隙

---

## 系统要求

- Unity 2019.4 或更高版本
- Unity UI（画布系统）
