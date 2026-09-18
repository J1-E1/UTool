# Radial Menu - Circular Menu System

![Unity](https://img.shields.io/badge/Unity-2019.4%20LTS%2B-blue.svg)
![Status](https://img.shields.io/badge/status-stable-success.svg)
![Documentation](https://img.shields.io/badge/docs-complete-brightgreen.svg)

English | [简体中文](./README-CN.md) | [Return to Main](../README.md)

## Overview

Flexible radial menu system for Unity with intuitive circular button layouts. Perfect for weapon wheels, ability selectors, and context menus.

---

## Features

- **Customizable Styles** - Multiple visual styles
- **Dynamic Generation** - Create items at runtime
- **Pooling System** - Efficient object reuse
- **Flexible Layout** - Adjustable spacing
- **Input Agnostic** - Mouse, touch, gamepad support

---

## Quick Start

1. Import Radial Menu package
2. Add RadialMenu prefab to canvas
3. Configure menu options
4. Assign button sprites and actions
5. Choose visual style

---

## Style Customization

### Available Styles

- **Blank Style** - Minimal design
- **Themed Styles** - Pre-designed themes
- **Custom Styles** - Create your own

### Menu Options

- Control button count
- Adjust spacing
- Configure radius and scale
- Set rotation and angle

---

## Button States

- Normal - Default appearance
- Highlighted - Mouse hover or focus
- Pressed - Active click
- Selected - Currently chosen
- Disabled - Inactive

---

## Usage Example

```csharp
public class RadialMenuController : MonoBehaviour
{
    public RadialMenu radialMenu;
    
    void Start()
    {
        radialMenu.AddMenuItem("Attack", OnAttackSelected);
        radialMenu.AddMenuItem("Defend", OnDefendSelected);
        radialMenu.BuildMenu();
    }
    
    void OnAttackSelected() => Debug.Log("Attack!");
}
```

---

## Common Use Cases

- Weapon Selection
- Ability Wheels
- Context Menus
- Inventory Quick Access
- Command Radials

---

## Best Practices

1. Keep options between 4-8
2. Use clear icons
3. Provide visual feedback
4. Test with gamepad

---

## Configuration

- **Button Count** - Number of buttons
- **Radius** - Distance from center
- **Start Angle** - Initial rotation
- **Spacing** - Gap between buttons

---

## Requirements

- Unity 2019.4+
- Unity UI (Canvas)
