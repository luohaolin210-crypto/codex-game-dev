---
name: game-playtest
description: 把测试层级与证据分开，确保代码、自动化和真人体验不互相冒充。
---

# game-playtest

## Purpose

把测试层级与证据分开，确保代码、自动化和真人体验不互相冒充。

## Trigger

版本验收、试玩、Bug 复现、玩法验证、视觉检查或发布前检查。

## Required Inputs

- 目标体验
- 版本号
- 测试矩阵
- 观察问题表
- 成功条件
- 可运行构建

## Workflow

1. 按 automated test → agent inspection → automated interaction → developer playtest → unfamiliar human playtest → real platform/device playtest 执行。
2. 每层记录能证明什么、不能证明什么。
3. 观察陌生真人行为，不主动解释。
4. 把问题按 Code、Gameplay、Visual、Real Playtest 分开。
5. 汇总阻断项和下一轮三件事。

## Hard Gates

- 需要真人的结论必须有真人记录。
- 真实平台问题不能由 Headless 或 Mock 代替。
- 四项最终验收分开输出。

## Failure Conditions

- Mock = 真人验收。
- Headless = 真人试玩。
- Build PASS = 游戏好玩。
- 只由开发者自己试玩。

## Evidence Required

- 每层测试结果
- 真人试玩观察
- 目标设备录屏/截图
- 分层问题清单

## Acceptance Criteria

- 每个结论对应正确层级证据。
- 阻断问题有复现步骤和优先级。

## Forbidden Shortcuts

- 把自动化覆盖率当作可玩性。
- 只看日志不看玩家行为。