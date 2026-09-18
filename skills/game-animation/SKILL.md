---
name: game-animation
description: 让动画强化状态、重量、节奏和可操作性，而不是阻断输入。
---

# game-animation

## Purpose

让动画强化状态、重量、节奏和可操作性，而不是阻断输入。

## Trigger

角色、UI、按钮、物品、合并、奖励、转场、弹窗或交互反馈动画。

## Required Inputs

- 状态机/状态表
- 输入响应预算
- 动画时长
- 可跳过策略
- 平台性能预算

## Workflow

1. 定义前置、进行中、成功、失败、取消和中断状态。
2. 定义时长、缓动、位移和反馈。
3. 规定何时锁输入、何时允许打断。
4. 在快速操作和低帧率下试玩。
5. 检查与 game-feel、game-ui-ux 的冲突。

## Hard Gates

- 关键输入响应不被装饰动画延迟。
- 动画可中断、跳过或降级。
- 成功和失败状态不混淆。

## Failure Conditions

- 动画阻断合理操作。
- 位移或层级让目标消失。
- 低帧率下状态机卡死。

## Evidence Required

- 状态/动画表
- 关键路径录屏
- 低帧率测试
- 中断规则

## Acceptance Criteria

- 动作重量和状态清晰且玩家能继续操作。
- 不会造成重复点击、误触或节奏断裂。

## Forbidden Shortcuts

- 每个按钮都加相同弹跳。
- 用动画长度掩盖缺少反馈。