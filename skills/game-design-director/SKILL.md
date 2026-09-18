---
name: game-design-director
description: 把想法变成可验证的玩家体验，检查核心循环、内容差异和系统边界。
---

# game-design-director

## Purpose

把想法变成可验证的玩家体验，检查核心循环、内容差异和系统边界。

## Trigger

新玩法、关卡、区域、系统、数值目标或下一关设计。

## Required Inputs

- game brief
- 核心循环
- 玩家目标
- 现有内容对照表

## Workflow

1. 写出玩家反复执行的动作循环和每次循环的变化。
2. 定义操作、判断、决策、风险、反馈和奖励。
3. 用 Skin-Swap Gate 对新旧内容逐项对比。
4. 只为能改变玩家行为的差异投入实现成本。
5. 交给 Gameplay Reality Check 和 Playtest 验证。

## Hard Gates

- SKIN_SWAP_GATE 必须为 PASS。
- 关键内容必须改变至少一个玩家决策和一个反馈结果。
- 目标、失败条件和重新开始方式可被玩家理解。

## Failure Conditions

- 新区域只换背景、名称、数量或数值。
- 功能列表增加但核心循环不变。
- 开发者解释替代了游戏内目标。

## Evidence Required

- 循环图
- 旧/新内容差异表
- 可玩的最小原型
- 试玩记录

## Acceptance Criteria

- 玩家能说出新内容带来的新决策。
- 连续三次循环有可感知变化。
- Skin-Swap Gate 记录为 PASS。

## Forbidden Shortcuts

- 用地图更大、敌人更多、数值更高冒充新玩法。
- 代码完成即宣布设计成立。