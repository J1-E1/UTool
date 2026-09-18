# Game Creator - Visual Scripting Framework

![Unity](https://img.shields.io/badge/Unity-2021.3%20LTS%2B-blue.svg)
![Game Creator](https://img.shields.io/badge/Game%20Creator-2.x-green.svg)
![Status](https://img.shields.io/badge/status-stable-success.svg)
![Documentation](https://img.shields.io/badge/docs-complete-brightgreen.svg)

English | [简体中文](./README-CN.md) | [Return to Main](../README.md)

## Overview

Comprehensive visual scripting framework for Unity that enables no-code game development. Create complex gameplay mechanics, character behaviors, and interactive systems without writing code.

---

## What is Game Creator?

Game Creator provides a visual, node-based system for creating game logic through:
- **Triggers** - Events that activate actions (on click, on collision, etc.)
- **Actions** - Operations that execute in sequence
- **Conditions** - Logic gates for decision making
- **Variables** - Data storage and manipulation
- **State Machines** - Complex behavior management

---

## Core Systems

### 1. Game Creator Core
Basic framework components and visual scripting tools.

[View Core Documentation](./1%20GameCreator)

**Key Features:**
- Character system
- Camera system
- Visual scripting
- Trigger and action system

### 2. Inventory System
Complete inventory management with items, bags, and merchants.

[View Inventory Documentation](./2%20Inventory)

**Key Features:**
- Item creation and properties
- Equipment system
- Currency management
- Merchant shops
- Crafting/tinkering

### 3. Stats System
Character attributes, classes, and progression.

[View Stats Documentation](./4%20Stats)

**Key Features:**
- Character classes
- Attributes and traits
- Leveling system
- Status effects

### 4. Quest System
Quest creation and task management.

[View Quest Documentation](./5%20Quest)

**Key Features:**
- Quest creation
- Task tracking
- Quest chains
- Rewards system

### 5. Shooter Module
FPS and TPS shooting mechanics.

[View Shooter Documentation](./8%20Shooter2)

**Key Features:**
- Weapon system
- Aiming and sights
- Reload mechanics
- Projectile system

### 6. Melee Module
Melee combat system with skills and combos.

[View Melee Documentation](./9%20Melee)

**Key Features:**
- Weapon system
- Skill system
- Combo chains
- Reactions and parrying

### 7. Traversal Module
Advanced character movement and parkour.

[View Traversal Documentation](./10%20Traversal)

**Key Features:**
- Climbing system
- Vaulting
- Ledge grabbing
- Advanced movement

---

## Quick Start

### Installation

1. Import Game Creator from Unity Asset Store
2. Install required dependencies (if any)
3. Open the Game Creator welcome window
4. Follow the setup wizard

### Creating Your First Interaction

1. Add a **Trigger** component to a GameObject
2. Choose a trigger type (e.g., "On Start", "On Click")
3. Add **Actions** to the trigger (e.g., "Move Character", "Play Animation")
4. Test in Play mode

---

## Visual Scripting Basics

### Triggers

Triggers detect events and activate actions:
- **On Start** - Executes when the scene loads
- **On Click** - Executes when clicked
- **On Collision** - Executes when objects collide
- **On Key Down** - Executes when a key is pressed
- **On Variable Change** - Executes when a variable changes

### Actions

Actions perform operations in sequence:
- Character actions (move, jump, play animation)
- Camera actions (switch shots, shake, zoom)
- Audio actions (play sound, music control)
- Variable actions (set, increment, compare)
- Flow control (wait, loop, conditions)

### Conditions

Conditions evaluate logic and branch execution:
- Compare variables
- Check player state
- Evaluate distances
- Test inventory contents

---

## Best Practices

1. **Organize with Comments** - Use descriptive names for triggers and actions
2. **Use Variables** - Store reusable values in global or local variables
3. **Modular Design** - Break complex logic into smaller triggers
4. **Test Frequently** - Run play mode often to catch issues early
5. **Use Conditions** - Add logic gates to make behaviors dynamic

---

## Common Workflows

### Character Movement
1. Add Character component to a GameObject
2. Configure input settings
3. Add camera controller for third-person view
4. Test movement and adjust parameters

### Interactive Objects
1. Add collider to object
2. Add "On Interact" trigger
3. Add actions (play sound, change material, spawn item)
4. Configure interaction prompt

### Save System
1. Define which data to save (variables, inventory, etc.)
2. Add save/load actions to menu
3. Test save persistence across sessions

---

## System Requirements

- Unity 2021.3 LTS or later
- Game Creator 2.x package

---

## Resources

- [Official Documentation](https://docs.gamecreator.io/)
- [Community Forum](https://forum.gamecreator.io/)
- [Video Tutorials](https://www.youtube.com/c/GameCreatorUnity)
- [Discord Community](https://discord.gg/gamecreator)

---

## Support

For technical support, bug reports, and feature requests:
- Visit the official documentation
- Post in the community forum
- Contact support through the Asset Store
