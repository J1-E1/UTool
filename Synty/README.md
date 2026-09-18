# Synty Studios Assets - Low Poly Resources

## Overview / 概述

**EN:** Synty Studios provides high-quality low-poly asset packs for Unity. This section contains notes, optimization tips, and best practices for using Synty assets in your projects.

**CN:** Synty Studios 为 Unity 提供高质量的低多边形资产包。本节包含在项目中使用 Synty 资产的笔记、优化技巧和最佳实践。

---

## What is Synty? / 什么是 Synty？

**EN:**
Synty Studios specializes in creating stylized low-poly 3D assets for Unity developers. Their asset packs are known for:
- Consistent art style across different packs
- Performance-optimized meshes
- Modular components for customization
- Wide variety of themes (fantasy, sci-fi, modern, etc.)

**CN:**
Synty Studios 专注于为 Unity 开发者创建风格化的低多边形 3D 资产。他们的资产包以以下特点著称：
- 不同包之间的一致艺术风格
- 性能优化的网格
- 用于自定义的模块化组件
- 多种主题（奇幻、科幻、现代等）

---

## Asset Categories / 资产类别

### Characters / 角色
- Modular character systems
- Multiple customization options
- Animation-ready rigs

### Environments / 环境
- Buildings and structures
- Natural elements (trees, rocks, etc.)
- Props and decorations

### Vehicles / 载具
- Ground vehicles
- Air vehicles
- Sci-fi spacecraft

---

## Documentation / 文档

### Settings / 设置
Configuration and import settings for Synty assets.

Synty 资产的配置和导入设置。

[View Settings Documentation](./Setting/DOC.md)

### Sidekick / 辅助工具
Tools and utilities for working with Synty assets.

使用 Synty 资产的工具和实用程序。

[View Sidekick Documentation](./SIdeKick/Doc.md)

### Animation / 动画
Animation setup and tips for Synty characters.

Synty 角色的动画设置和技巧。

[View Animation Notes](./Animation/Note.md)

---

## Best Practices / 最佳实践

### Performance Optimization / 性能优化

**EN:**
1. **Use Static Batching** - Mark non-moving objects as static
2. **Combine Meshes** - Use mesh combining for objects that share materials
3. **Occlusion Culling** - Enable for large scenes
4. **LOD Groups** - Implement Level of Detail for distant objects
5. **Atlas Textures** - Combine textures when possible

**CN:**
1. **使用静态批处理** - 将不移动的对象标记为静态
2. **合并网格** - 对共享材质的对象使用网格合并
3. **遮挡剔除** - 为大场景启用
4. **LOD 组** - 为远处对象实现细节层次
5. **图集纹理** - 尽可能合并纹理

### Material Setup / 材质设置

**EN:**
- Use the Standard Shader or URP/HDRP equivalents
- Enable GPU instancing for repeated objects
- Adjust smoothness for desired look
- Use emission for glowing elements

**CN:**
- 使用标准着色器或 URP/HDRP 等效项
- 为重复对象启用 GPU 实例化
- 调整平滑度以获得所需外观
- 为发光元素使用自发光

### Character Customization / 角色自定义

**EN:**
Synty's modular character systems allow:
- Swapping head, body, and accessory parts
- Mixing different asset pack components
- Creating unique character variations
- Runtime customization support

**CN:**
Synty 的模块化角色系统允许：
- 交换头部、身体和配饰部件
- 混合不同资产包组件
- 创建独特的角色变体
- 运行时自定义支持

---

## Common Issues & Solutions / 常见问题与解决方案

### Import Settings / 导入设置

**EN:**
**Problem:** Models appear too dark or shiny
**Solution:** Adjust material smoothness and enable proper lighting

**Problem:** Animations don't play correctly
**Solution:** Check animation import settings and rig configuration

**Problem:** Textures look blurry
**Solution:** Increase max texture size in import settings

**CN:**
**问题：** 模型看起来太暗或太亮
**解决方案：** 调整材质平滑度并启用适当的照明

**问题：** 动画无法正确播放
**解决方案：** 检查动画导入设置和绑定配置

**问题：** 纹理看起来模糊
**解决方案：** 在导入设置中增加最大纹理大小

---

## Lighting Tips / 照明技巧

**EN:**
- Use baked lighting for static scenes
- Add ambient occlusion for depth
- Use color grading to enhance the low-poly aesthetic
- Consider stylized post-processing effects

**CN:**
- 为静态场景使用烘焙照明
- 添加环境光遮蔽以增加深度
- 使用颜色分级增强低多边形美学
- 考虑风格化的后处理效果

---

## Asset Pack Compatibility / 资产包兼容性

**EN:**
Synty assets from different packs can be mixed because:
- Consistent poly count and style
- Standardized pivot points
- Similar texture resolutions
- Matching color palettes

**CN:**
来自不同包的 Synty 资产可以混合使用，因为：
- 一致的多边形数量和风格
- 标准化的轴心点
- 相似的纹理分辨率
- 匹配的调色板

---

## Recommended Asset Packs / 推荐资产包

### For Different Game Types / 不同游戏类型

**Fantasy Games / 奇幻游戏**
- Polygon Fantasy Kingdom
- Polygon Fantasy Rivals
- Polygon Dungeon Pack

**Modern/Military / 现代/军事**
- Polygon Battle Royale
- Polygon Apocalypse
- Polygon Modern Interiors

**Sci-Fi / 科幻**
- Polygon Sci-Fi Space
- Polygon Sci-Fi City
- Polygon Heist

**Nature/Environment / 自然/环境**
- Polygon Nature Pack
- Polygon Farm Pack
- Polygon Prototype Pack

---

## Resources / 资源

**EN:**
- [Synty Store](https://syntystore.com/)
- [Unity Asset Store - Synty](https://assetstore.unity.com/publishers/5217)
- [Synty YouTube Channel](https://www.youtube.com/c/SyntyStudios)
- Community Forums and Discord

**CN:**
- [Synty 商店](https://syntystore.com/)
- [Unity Asset Store - Synty](https://assetstore.unity.com/publishers/5217)
- [Synty YouTube 频道](https://www.youtube.com/c/SyntyStudios)
- 社区论坛和 Discord

---

## Quick Tips / 快速提示

**EN:**
1. Always read the documentation included with each asset pack
2. Use prefabs provided rather than placing raw models
3. Study the demo scenes for implementation examples
4. Keep asset packs organized in separate folders
5. Consider performance when combining multiple packs

**CN:**
1. 始终阅读每个资产包附带的文档
2. 使用提供的预制体而不是放置原始模型
3. 研究演示场景以获取实现示例
4. 将资产包组织在单独的文件夹中
5. 组合多个包时考虑性能

---

## License Information / 许可证信息

**EN:**
Synty assets are typically licensed for use in commercial and non-commercial projects. Always verify the specific license terms for your purchased assets.

**CN:**
Synty 资产通常授权用于商业和非商业项目。始终验证您购买的资产的特定许可条款。
