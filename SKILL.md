---
name: shared-game-dev
description: Route game-development tasks to dedicated specialist skills, then enforce evidence-based gates for gameplay, visuals, UI, performance, retention, and playtest quality.
---

# Shared Game Dev Router

本文件是游戏项目的总路由器。任何游戏任务先经过路由，再调用一个或多个专项 Skill；不得要求用户每次手工指定 Skill。

## Routing algorithm

1. 识别任务中的对象、风险和验收证据。
2. 选择一个主 Skill；选择必要的支援 Skills。
3. 按依赖顺序执行：设计假设 → 原型/实现 → 反馈与视觉 → 平台适配 → QA/试玩。
4. 汇总四类独立结论：CODE QUALITY、GAMEPLAY QUALITY、VISUAL QUALITY、REAL PLAYTEST。
5. 缺少对应证据时，不得把该项判为通过。

## Route map

| Signal | Primary | Supporting |
| --- | --- | --- |
| HUD 重叠、文字被裁切、移动端布局 | game-ui-ux | mobile-game-layout, game-visual-qa |
| 下一关只是换皮、区域差异不足 | game-design-director | gameplay-reality-check, game-retention-review |
| 合成/点击/拖动没有爽感 | game-feel | game-vfx, game-audio-feedback |
| 画面不好看、风格不统一 | game-art-direction | game-asset-pipeline, game-visual-qa |
| Cocos 特效差、材质或性能问题 | game-vfx | game-rendering, cocos-creator-visual-adapter |
| 新玩法想法、核心循环、关卡结构 | game-design-director | gameplay-reality-check |
| 动画拖沓、操作被阻断 | game-animation | game-feel, game-visual-qa |
| 留存、首局、3/10 分钟体验 | game-retention-review | gameplay-reality-check, game-playtest |
| 试玩、真实用户反馈、版本验收 | game-playtest | game-visual-qa, game-retention-review |
| 资源导入、命名、尺寸、压缩、缺失素材 | game-asset-pipeline | game-art-direction, game-rendering |

## Mandatory gates

- SKIN_SWAP_GATE：如果新内容只改变背景、名字、数量或数值，而操作、判断、决策、风险、反馈基本不变，必须为 FAIL。
- UI_OVERLAP = 0
- CLIPPED_TEXT = 0
- OFFSCREEN_CRITICAL_UI = 0
- UNLABELED_CORE_TARGET = 0
- SAFE_AREA_VIOLATION = 0
- OVERFEEDBACK_GATE：过度震屏、击退、粒子遮挡、动画阻断操作或小操作使用重大庆祝反馈时为 FAIL。
- 核心目标不得只靠颜色表达；优先采用文字 + 图标 + 色彩。

## Evidence contract

每次路由必须留下：触发信号、选中的 Skills、关键假设、运行/试玩证据、四类质量结论、未通过闸门和下一步。代码完成、自动化测试通过、Mock、Headless 或 Build PASS 均不能替代真人试玩。

## Final status

只有所有必要专项 Skill 的 Hard Gates 通过，并且四类结论分别有证据，才能输出 GAME DEV SKILL PACK PHASE 2 = PASS。否则输出 FAIL 或 NOT INTEGRATED，并说明缺失项。