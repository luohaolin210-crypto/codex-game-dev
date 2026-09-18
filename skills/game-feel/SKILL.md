---
name: game-feel
description: 为关键操作建立输入、动画、声音、粒子、镜头和结果的统一反馈。
---

# game-feel

## Purpose

为关键操作建立输入、动画、声音、粒子、镜头和结果的统一反馈。

## Trigger

点击、拖动、合并、归档、完成订单、奖励、Combo、解锁、升级或区域完成。

## Required Inputs

- 动作语义
- 输入与结果状态
- 反馈等级
- 平台性能预算
- 录屏或构建

## Workflow

1. 将动作分为 MICRO、MEDIUM、MAJOR、CELEBRATION。
2. 为每级定义输入响应、动画、音效、粒子、镜头和结果。
3. 先保证输入响应和结果可读，再增加装饰。
4. 在连续操作、快速重复和失败路径中试玩。
5. 检查 OVERFEEDBACK_GATE。

## Hard Gates

- 每个关键动作有即时且可读的反馈。
- 反馈等级与动作重要性匹配。
- OVERFEEDBACK_GATE 必须 PASS。
- 反馈不得阻断下一次合理输入。

## Failure Conditions

- 小操作使用重大庆祝反馈。
- 震屏、击退或粒子遮挡操作。
- 动画锁死输入或延迟结果。

## Evidence Required

- 反馈分级表
- 关键动作录屏
- 目标设备试玩记录
- Overfeedback 检查

## Acceptance Criteria

- 玩家无需解释即可知道动作是否成功。
- 连续操作不会造成视觉、听觉或输入疲劳。
- 重大事件明显但不过量。

## Forbidden Shortcuts

- 所有事件使用同一套弹窗、音效或粒子。
- 只增加粒子和震屏，不验证可读性。