---
name: cocos-creator-visual-adapter
description: 为 Cocos Creator 3.8.x 提供明确边界的视觉与性能适配检查。
---

# cocos-creator-visual-adapter

## Purpose

为 Cocos Creator 3.8.x 提供明确边界的视觉与性能适配检查。

## Trigger

Cocos Creator 3.8.x 项目中的 Material、Effect、Sprite、Label、UI、Tween、Animation、ParticleSystem、RenderTexture、batching、draw calls、texture budget 或 shader cost。

## Required Inputs

- Cocos Creator 3.8.x 版本
- 目标设备
- 场景与节点树
- 材质/Effect/Shader 文件
- 资源导入设置
- 性能采样

## Workflow

1. 确认实际 Cocos 版本、渲染后端和目标平台。
2. 分别检查 Material、Effect、Sprite、Label、UI、Tween、Animation、ParticleSystem、RenderTexture。
3. 测量 batching、draw calls、texture budget、shader cost 和移动端帧时间。
4. 在真实场景和最坏状态预览。
5. 输出 Cocos-specific 结论，其他引擎资料仅作参考。

## Hard Gates

- 兼容结论基于 Cocos Creator 3.8.x 实测或官方版本证据。
- 移动端最坏场景有性能数据。
- 材质、Effect、粒子和 RenderTexture 有降级方案。

## Failure Conditions

- 直接声明其他引擎 Shader/VFX 兼容。
- 只在编辑器预览。
- 没有版本号或目标设备。

## Evidence Required

- 版本信息
- Cocos 场景截图/录屏
- draw calls/帧时间/内存数据
- 资源导入与降级记录

## Acceptance Criteria

- Cocos 项目可复现、可测量、可降级。
- 问题能定位到节点、资源、材质、Effect 或批处理层。

## Forbidden Shortcuts

- 跨引擎复制 Shader/VFX 后直接交付。
- Build PASS 代替设备试玩。