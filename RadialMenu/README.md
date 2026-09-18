# Radial Menu - Circular Menu System

## Overview / 概述

**EN:** A flexible radial (circular) menu system for Unity that provides intuitive navigation and selection through circular button layouts. Perfect for weapon wheels, ability selectors, and context menus.

**CN:** Unity 的灵活径向（圆形）菜单系统，通过圆形按钮布局提供直观的导航和选择。非常适合武器轮盘、能力选择器和上下文菜单。

---

## Features / 特性

**EN:**
- **Customizable Styles** - Multiple pre-built visual styles
- **Dynamic Generation** - Create menu items at runtime
- **Pooling System** - Efficient object reuse for performance
- **Flexible Layout** - Adjustable spacing and positioning
- **Theme Support** - Easy style switching
- **Input Agnostic** - Works with mouse, touch, and gamepad

**CN:**
- **可定制样式** - 多种预构建视觉样式
- **动态生成** - 在运行时创建菜单项
- **池系统** - 高效的对象重用以提高性能
- **灵活布局** - 可调整间距和定位
- **主题支持** - 轻松切换样式
- **输入无关** - 支持鼠标、触摸和手柄

---

## Quick Start / 快速开始

**EN:**
1. Import Radial Menu package into your project
2. Add RadialMenu prefab to your canvas
3. Configure menu options and spacing
4. Assign button sprites and actions
5. Choose a visual style

**CN:**
1. 将 Radial Menu 包导入到项目中
2. 将 RadialMenu 预制体添加到画布
3. 配置菜单选项和间距
4. 分配按钮精灵和动作
5. 选择视觉样式

---

## Style Customization / 样式自定义

### Available Styles / 可用样式

**EN:**
The radial menu supports multiple visual styles that can be switched at runtime:
- **Blank Style** - Minimal design with customizable colors
- **Themed Styles** - Pre-designed themes for different game genres
- **Custom Styles** - Create your own button designs

**CN:**
径向菜单支持多种可在运行时切换的视觉样式：
- **空白样式** - 可自定义颜色的简约设计
- **主题样式** - 为不同游戏类型预设计的主题
- **自定义样式** - 创建自己的按钮设计

### Menu Options / 菜单选项

**EN:**
- Control the number of buttons displayed
- Adjust spacing between menu items
- Configure radius and scale
- Set rotation and starting angle

**CN:**
- 控制显示的按钮数量
- 调整菜单项之间的间距
- 配置半径和缩放
- 设置旋转和起始角度

---

## Pooling System / 池系统

**EN:**
The radial menu includes an efficient pooling system that:
- Reuses button objects instead of creating/destroying them
- Improves performance for frequently opened menus
- Reduces garbage collection pressure
- Supports custom pool sizes

**CN:**
径向菜单包含高效的池系统：
- 重用按钮对象而不是创建/销毁它们
- 提高频繁打开的菜单的性能
- 减少垃圾回收压力
- 支持自定义池大小

---

## Button States / 按钮状态

**EN:**
Each button supports multiple visual states:
- **Normal** - Default appearance
- **Highlighted** - Mouse hover or gamepad focus
- **Pressed** - Active click or selection
- **Selected** - Currently chosen option
- **Disabled** - Inactive or unavailable

**CN:**
每个按钮支持多种视觉状态：
- **正常** - 默认外观
- **高亮** - 鼠标悬停或手柄聚焦
- **按下** - 主动点击或选择
- **已选** - 当前选择的选项
- **禁用** - 非活动或不可用

---

## Usage Examples / 使用示例

### Creating Menu Items at Runtime / 运行时创建菜单项

```csharp
using UnityEngine;

public class RadialMenuController : MonoBehaviour
{
    public RadialMenu radialMenu;
    
    void Start()
    {
        // Add menu items dynamically
        radialMenu.AddMenuItem("Attack", OnAttackSelected);
        radialMenu.AddMenuItem("Defend", OnDefendSelected);
        radialMenu.AddMenuItem("Magic", OnMagicSelected);
        
        // Build the menu
        radialMenu.BuildMenu();
    }
    
    void OnAttackSelected()
    {
        Debug.Log("Attack selected!");
    }
    
    void OnDefendSelected()
    {
        Debug.Log("Defend selected!");
    }
    
    void OnMagicSelected()
    {
        Debug.Log("Magic selected!");
    }
}
```

### Switching Styles / 切换样式

```csharp
// Change the visual style
radialMenu.SetStyle(RadialMenuStyle.Blank);

// Or use a custom style
radialMenu.ApplyCustomStyle(myCustomStyleData);
```

---

## Common Use Cases / 常见用例

**EN:**
- **Weapon Selection** - Quick weapon switching in action games
- **Ability Wheels** - Choose skills and abilities in RPGs
- **Context Menus** - Right-click style menus for strategy games
- **Inventory Quick Access** - Fast item selection
- **Command Radials** - RTS unit commands

**CN:**
- **武器选择** - 动作游戏中的快速武器切换
- **能力轮盘** - RPG 中选择技能和能力
- **上下文菜单** - 策略游戏的右键菜单
- **库存快速访问** - 快速物品选择
- **命令径向** - RTS 单位命令

---

## Best Practices / 最佳实践

**EN:**
1. Keep the number of options between 4-8 for optimal usability
2. Use clear, recognizable icons for each option
3. Provide visual feedback for selection
4. Consider gamepad/controller input for console games
5. Test menu readability at different screen resolutions

**CN:**
1. 保持选项数量在 4-8 个之间以获得最佳可用性
2. 为每个选项使用清晰、可识别的图标
3. 为选择提供视觉反馈
4. 考虑主机游戏的手柄/控制器输入
5. 在不同屏幕分辨率下测试菜单可读性

---

## Configuration / 配置

### Inspector Settings / 检查器设置

**EN:**
- **Button Count** - Number of buttons in the radial
- **Radius** - Distance from center
- **Start Angle** - Initial rotation offset
- **Spacing** - Gap between buttons
- **Style** - Visual appearance preset

**CN:**
- **按钮数量** - 径向中的按钮数量
- **半径** - 距中心的距离
- **起始角度** - 初始旋转偏移
- **间距** - 按钮之间的间隙
- **样式** - 视觉外观预设

---

## Performance Tips / 性能提示

**EN:**
- Enable object pooling for frequently used menus
- Use sprite atlases for button graphics
- Limit the number of simultaneous radial menus
- Cache references to avoid repeated GetComponent calls

**CN:**
- 为频繁使用的菜单启用对象池
- 为按钮图形使用精灵图集
- 限制同时显示的径向菜单数量
- 缓存引用以避免重复的 GetComponent 调用

---

## System Requirements / 系统要求

**EN:**
- Unity 2019.4 or later
- Unity UI (Canvas system)

**CN:**
- Unity 2019.4 或更高版本
- Unity UI（画布系统）

---

## Resources / 资源

- Check the included example scenes for implementation details
- Refer to inline documentation for component properties

---

## Tips / 提示

**EN:**
- The radial menu works best with 4-8 options
- Use consistent icon sizes for visual harmony
- Consider color-coding options by category
- Test with both mouse and gamepad input

**CN:**
- 径向菜单在 4-8 个选项时效果最佳
- 使用一致的图标大小以保持视觉和谐
- 考虑按类别对选项进行颜色编码
- 使用鼠标和手柄输入进行测试
