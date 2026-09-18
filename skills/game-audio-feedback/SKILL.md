---
name: game-audio-feedback
description: 用声音确认操作、状态、重量和奖励，并建立不疲劳的反馈层级。
---

# game-audio-feedback

## Purpose

用声音确认操作、状态、重量和奖励，并建立不疲劳的反馈层级。

## Trigger

点击、拖动、合并、归档、订单完成、奖励、Combo、解锁、升级、区域完成或音量问题。

## Required Inputs

- 事件等级
- 音量层级
- 重复频率
- 音频资产规格
- 平台混音预算
- 静音/降级策略

## Workflow

1. 将声音按 MICRO、MEDIUM、MAJOR、CELEBRATION 分级。
2. 定义起音、变化、结束和重复策略。
3. 处理快速重复、同时发生、失败和静音状态。
4. 与视觉和动画反馈对齐但不完全重复。
5. 在耳机、扬声器、低音量和静音状态验证。

## Hard Gates

- 关键结果有可辨认声音或明确无声替代。
- 重复操作不刺耳、不堆叠、不疲劳。
- 声音层级不掩盖核心音频。

## Failure Conditions

- 所有事件同一音效。
- 小操作使用重大庆祝音。
- 音频与实际结果不同步。

## Evidence Required

- 音频事件表
- 连续操作录音
- 不同输出设备测试
- 静音降级记录

## Acceptance Criteria

- 玩家能用声音辅助判断结果。
- 声音不会因重复或叠加降低可玩性。

## Forbidden Shortcuts

- 只加音效不检查时序。
- 用音量和低频掩盖缺少游戏感。