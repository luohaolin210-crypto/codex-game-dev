---
name: game-rendering
description: 在视觉质量与平台预算之间建立可测量的渲染决策。
---

# game-rendering

## Purpose

在视觉质量与平台预算之间建立可测量的渲染决策。

## Trigger

材质、Shader、Sprite、Label、RenderTexture、批处理、draw calls、纹理或移动端性能问题。

## Required Inputs

- 目标设备
- 渲染管线
- 场景截图
- draw calls/帧时间
- 纹理尺寸与格式
- shader cost

## Workflow

1. 建立目标设备和预算基线。
2. 定位纹理、材质、Shader、批次、透明层、RenderTexture 或 UI 瓶颈。
3. 用最小改动验证收益。
4. 在真实场景、最拥挤状态和冷启动测量。
5. 记录视觉取舍和回归风险。

## Hard Gates

- 结论来自目标场景和目标设备。
- 优化不能破坏目标可读性。
- 纹理、Shader、draw calls 和内存预算有记录。

## Failure Conditions

- 只看编辑器或空场景帧率。
- 降低分辨率掩盖错误层级。
- 引用其他引擎兼容结论。

## Evidence Required

- 前后性能数据
- 目标设备记录
- 最坏场景截图/录屏
- 渲染预算表

## Acceptance Criteria

- 最坏场景达到目标帧率或明确延期。
- 优化项说明成本、收益和视觉影响。

## Forbidden Shortcuts

- 没有数据就宣称性能优化完成。
- 混为一谈 Cocos、Unity、Godot 的渲染行为。