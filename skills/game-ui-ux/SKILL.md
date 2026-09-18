---
name: game-ui-ux
description: 建立清晰、可读、可操作的界面，让核心目标和状态无需解释仍然明确。
---

# game-ui-ux

## Purpose

建立清晰、可读、可操作的界面，让核心目标和状态无需解释仍然明确。

## Trigger

HUD、按钮、弹窗、目标提示、资源栏、订单栏、教程或交互层级。

## Required Inputs

- 目标平台与分辨率
- 安全区
- 交互优先级
- 状态清单
- 视觉规格

## Workflow

1. 列出核心、次要和装饰信息。
2. 核心目标使用文字 + 图标 + 色彩，而不是只用颜色。
3. 建立层级、触控尺寸、状态变化和错误状态。
4. 在不同分辨率、长文本、极端数值和连续弹窗下检查。
5. 输出 UI Hard Gate 结果。

## Hard Gates

- UI_OVERLAP = 0。
- CLIPPED_TEXT = 0。
- OFFSCREEN_CRITICAL_UI = 0。
- UNLABELED_CORE_TARGET = 0。
- SAFE_AREA_VIOLATION = 0。

## Failure Conditions

- 核心目标只靠颜色表达。
- 文字被裁切、重叠或不可读。
- 关键按钮超出安全区。

## Evidence Required

- 目标分辨率截图
- 长文本与极端状态截图
- UI 问题清单
- Hard Gate 计数

## Acceptance Criteria

- 陌生玩家能找到核心目标和下一步。
- 关键状态在小屏和色盲场景仍可区分。
- 所有 UI Hard Gates 为 0。

## Forbidden Shortcuts

- 用更小字体解决拥挤。
- 把核心信息藏在颜色或悬停状态里。