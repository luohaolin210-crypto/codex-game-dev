---
name: game-visual-qa
description: 独立检查游戏视觉质量、布局、层级、一致性和平台可读性。
---

# game-visual-qa

## Purpose

独立检查游戏视觉质量、布局、层级、一致性和平台可读性。

## Trigger

每个版本、场景改动、资产替换、UI 改动、特效改动或发布候选。

## Required Inputs

- 目标分辨率/设备
- 视觉规格
- 关键路径截图/录屏
- 资产清单
- 安全区和 UI 清单

## Workflow

1. 检查 hierarchy、alignment、spacing、overlap、clipping、readability、target clarity、visual consistency、asset scale、wrong z-order、broken texture、safe area、crowded area、empty area。
2. 分别检查第一屏、核心操作、成功、失败和最拥挤状态。
3. 记录截图、位置、严重度和复现条件。
4. 与 game-ui-ux、mobile-game-layout、game-art-direction 交叉回归。
5. 输出独立 Visual Quality 结论。

## Hard Gates

- UI_OVERLAP = 0。
- CLIPPED_TEXT = 0。
- OFFSCREEN_CRITICAL_UI = 0。
- UNLABELED_CORE_TARGET = 0。
- SAFE_AREA_VIOLATION = 0。
- 核心目标不能只靠颜色表达。

## Failure Conditions

- 只检查静态首屏。
- 忽略拥挤区、空白区或错误 z-order。
- 用美术偏好代替可复现证据。

## Evidence Required

- 逐项检查表
- 目标设备截图/录屏
- 问题定位信息
- 前后对比

## Acceptance Criteria

- 关键路径没有布局、裁切、层级、贴图或可读性阻断项。
- 所有 Hard Gates 有计数且为 0。

## Forbidden Shortcuts

- 截图好看就跳过运行中状态。
- 用代码测试替代视觉质量。