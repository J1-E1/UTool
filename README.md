# UTool - Unity Tools & Plugins Knowledge Base

## Comprehensive documentation for Unity development tools and frameworks

![Unity](https://img.shields.io/badge/Unity-6.0%2B-blue.svg)
![Documentation](https://img.shields.io/badge/docs-comprehensive-brightgreen.svg)
![Language](https://img.shields.io/badge/language-EN%20%7C%20CN-orange.svg)
![License](https://img.shields.io/badge/license-Educational-lightgrey.svg)
![Status](https://img.shields.io/badge/status-active-success.svg)

English | [简体中文](./README-CN.md)

A curated knowledge base for Unity development, covering popular tools, plugins, and frameworks. This repository provides organized notes, API references, configuration guides, and best practices for commonly-used Unity assets.

## Table of Contents

- [Components](#-components)
- [Quick Start](#-quick-start)
- [Documentation Structure](#-documentation-structure)
- [Contributing](#-contributing)
- [License](#-license)

## 🎮 Components

### Camera & Cinematography

**[Cinemachine](./Cinemachine)** - Advanced virtual camera system
- Procedural camera behavior and shot composition
- Virtual cameras with priority-based blending
- Timeline integration and smooth transitions

### Game Development Frameworks

**[Game Creator](./Game%20Creator)** - Visual scripting framework
- No-code game development with triggers and actions
- Complete systems: Inventory, Stats, Quests, Combat
- Modular architecture with shooter, melee, and traversal modules

### UI Frameworks

**[MlskyUI](./MlskyUI)** - Modern UI component library
- Dark and Modern theme support
- Pre-built components: buttons, modals, sliders
- Gamepad support and localization

**[Radial Menu](./RadialMenu)** - Circular menu system
- Customizable radial button layouts
- Object pooling for performance
- Multiple visual styles

### Programming Utilities

**[UniTask](./UniTask)** - Zero-allocation async/await
- High-performance async operations
- Unity-specific async patterns
- Cancellation token support

### Art & Assets

**[Synty Studios](./Synty)** - Low-poly asset collections
- Modular character systems
- Environment and prop packs
- Performance optimization guides

## 🚀 Quick Start

### Browse Documentation

1. Navigate to a component folder from the list above
2. Read the `README.md` for overview and quick start
3. Explore detailed documentation files for specific features
4. Check code examples and implementation patterns

### Component Selection Guide

- **For camera work** → Cinemachine
- **For rapid prototyping** → Game Creator
- **For UI systems** → MlskyUI or Radial Menu
- **For async programming** → UniTask
- **For art assets** → Synty Studios

## 📂 Documentation Structure

Each component follows this organization:

```
Component/
├── README.md              # Overview, features, quick start
├── SubSystem/             # Detailed feature documentation
│   └── feature.md
└── images/                # Screenshots and diagrams
    └── descriptive-name.png
```

### Documentation Features

- **Bilingual content** - Key concepts explained in English and Chinese
- **Code examples** - Ready-to-use snippets with inline comments
- **Visual references** - Screenshots for UI and configuration
- **Best practices** - Performance tips and common patterns

### Unity Version Compatibility

This documentation primarily targets **Unity 6.0+**, but individual components have varying requirements:

| Component | Minimum Unity Version | Notes |
|-----------|----------------------|-------|
| Cinemachine | 2021.3 LTS+ | Built-in package in Unity 6.0+ |
| Game Creator | 2021.3 LTS+ | Requires modern Unity features |
| MlskyUI | 2020.3 LTS+ | Compatible with older versions |
| RadialMenu | 2019.4 LTS+ | Wide compatibility range |
| UniTask | 2020.3 LTS+ | Requires .NET Standard 2.1 |
| Synty Assets | 2019.4+ | Universal compatibility |

**Recommendation:** Use Unity 2021.3 LTS or Unity 6.0 for best compatibility across all components.

## 🤝 Contributing

Contributions are welcome! When adding documentation:

1. Follow the existing structure and naming conventions
2. Include both English and Chinese sections where applicable
3. Use descriptive names for images (not timestamps)
4. Test all code examples before committing
5. Update the main README if adding new components

## 📝 License

This repository contains educational notes and references. Please respect the original licenses of the documented tools and assets.

---

**Note:** This is a documentation repository. Actual asset packages must be obtained from their official sources (Unity Asset Store, GitHub, etc.).

---

<p align=”center”>
  <sub>Built for the Unity developer community</sub>
</p>