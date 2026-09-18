---
name: game-vfx
description: 用克制、可读、可调预算的特效强调状态和结果。
---

# game-vfx

## Purpose

用克制、可读、可调预算的特效强调状态和结果。

## Trigger

点击、命中、合并、奖励、解锁、区域完成或 Cocos 特效问题。

## Required Inputs

- 事件等级
- 目标位置/尺寸
- 粒子预算
- 遮挡风险
- 平台性能目标
- 渲染管线

## Workflow

1. 按事件等级选择形状、粒子、拖尾、闪光和持续时间。
2. 先做低成本可读版本，再增加层次。
3. 在密集场景检查遮挡、z-order 和叠加。
4. 测量粒子、材质、纹理和批次成本。
5. 交给 game-feel、game-rendering 和 Visual QA。

## Hard Gates

- 不能遮挡核心目标或 UI。
- OVERFEEDBACK_GATE 必须 PASS。
- 效果强度与事件等级一致。
- 平台预算不超标。

## Failure Conditions

- 粒子越多越好。
- 特效盖住目标、文字或交互点。
- 只在空场景测试。

## Evidence Required

- 事件分级表
- 密集场景录屏
- 性能采样
- 遮挡/层级截图

## Acceptance Criteria

- 玩家准确识别事件和目标。
- 特效可降级且降级后仍可读。

## Forbidden Shortcuts

- 套用其他引擎 Shader/VFX 并声明兼容 Cocos。
- 用全屏闪白和强震屏替代状态设计。