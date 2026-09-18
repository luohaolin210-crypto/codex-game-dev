---
name: gameplay-reality-check
description: 在正式实现前验证玩法假设，防止把代码完成误判为好玩。
---

# gameplay-reality-check

## Purpose

在正式实现前验证玩法假设，防止把代码完成误判为好玩。

## Trigger

任何新核心玩法、关卡机制、奖励循环或大规模内容扩展。

## Required Inputs

- Gameplay Hypothesis
- Expected Player Behavior
- Why It May Be Fun
- Cheapest Prototype
- Success Signal
- Failure Signal
- Human Validation

## Workflow

1. 明确 Gameplay Hypothesis 和预期玩家行为。
2. 写出为什么可能有趣以及最大未知点。
3. 制作 Cheapest Prototype，只验证核心选择。
4. 定义 Success Signal、Failure Signal 和停止条件。
5. 进行 Human Validation，记录陌生玩家行为。

## Hard Gates

- 七项输入必须完整。
- 必须存在真人验证计划或已完成验证。
- 原型必须快速暴露风险。

## Failure Conditions

- 只有自动化测试、Mock 或 Headless 结果。
- 没有失败信号或成功信号。
- 玩法依赖口头说明。

## Evidence Required

- 假设卡
- 可操作原型
- 原始试玩观察
- 成功/失败信号记录

## Acceptance Criteria

- 陌生真人能独立完成目标或明确表达问题。
- 观察行为与预期基本一致。

## Forbidden Shortcuts

- 代码完成 = 玩法成立。
- 自动化测试通过 = 好玩。
- 开发者熟悉度冒充用户理解。