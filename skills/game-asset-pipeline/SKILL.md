---
name: game-asset-pipeline
description: 把资产从定义到批准变成可追踪、可重复的流水线。
---

# game-asset-pipeline

## Purpose

把资产从定义到批准变成可追踪、可重复的流水线。

## Trigger

新增或替换角色、场景、图标、UI、音频、VFX、材质或字体。

## Required Inputs

- 资产用途
- 视觉规格
- 目标尺寸/比例
- 命名规则
- 平台预算
- 验收截图

## Workflow

1. Define：填写用途、尺寸和预算。
2. Reference：绑定参考板和禁止项。
3. Produce：生成或制作源资产。
4. Normalize：统一尺寸、命名、格式、枢轴、压缩和导入设置。
5. In-game Preview：在真实场景预览。
6. Compare：与参考和同类资产对比。
7. Approve：记录批准、退回原因和版本。

## Hard Gates

- 七步不可跳过。
- 缺失、错误比例、错误枢轴、错误格式和过预算资产不得批准。
- 必须有游戏内预览。

## Failure Conditions

- 文件存在但场景里比例或层级错误。
- 依赖默认导入设置。
- 同类资产规格不一致。

## Evidence Required

- 资产清单
- 导入前后对比
- 游戏内截图
- 预算与批准记录

## Acceptance Criteria

- 新成员可按清单复现接入流程。
- 目标设备和真实场景中可读、可控、可回滚。

## Forbidden Shortcuts

- 源文件正确就跳过 In-game Preview。
- 一张合成图代替所有验证。