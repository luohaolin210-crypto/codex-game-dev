# Codex Game Dev

<p align="center">
  <strong>一个可直接从 Codex 调用的游戏开发 Skill Pack</strong>
  <br />
  Router、专项 Skills、质量闸门和可复用模板
</p>

<p align="center">
  <a href="../README.md">项目说明</a>
  ·
  <a href="../SKILL.md">Router 入口</a>
  ·
  <a href="quality-gates.md">质量闸门</a>
  ·
  <a href="workflow.md">工作流</a>
</p>

---

## 这份教程解决什么问题

本仓库不是完整的“AI 游戏工作室”模板，也没有角色层级、自动 Hook 或固定斜杠命令。

它提供一套更小、更明确的调用面：

- 用一个 Router 判断当前任务应该调用哪些 Skill。
- 用专项 Skill 处理设计、UI、视觉、反馈、性能、留存和试玩。
- 用质量闸门约束“看起来完成”与“有证据完成”的区别。
- 用模板把简报、视觉规格和试玩报告留下来。



## 目录

- [包含什么](#包含什么)
- [开始使用](#开始使用)
- [调用入口](#调用入口)
- [专项 Skill 调用](#专项-skill-调用)
- [路由示例](#路由示例)
- [项目结构](#项目结构)
- [工作方式](#工作方式)
- [质量闸门](#质量闸门)
- [输出格式](#输出格式)
- [如何扩展](#如何扩展)

## 包含什么

| 组成 | 入口 | 用途 |
|------|------|------|
| Router | `SKILL.md` | 从自然语言任务选择主 Skill 和支援 Skills |
| 专项 Skills | `skills/*/SKILL.md` | 处理具体的游戏开发问题 |
| 文档 | `docs/` | 工作流、路由测试和质量标准 |
| 模板 | `templates/` | 游戏简报、视觉规格和试玩报告 |
| Pilot 摘要 | `pilots/` | 已脱敏的质量审计示例 |

## 开始使用

### 方式一：在当前仓库中调用

在 Codex 中打开本仓库或将它作为当前工作目录，然后直接说：

```text
读取 SKILL.md。
根据我的游戏开发任务选择主 Skill 和支援 Skills，
先给出路由、关键假设、证据要求和质量闸门。
暂时不要修改文件。
```

### 方式二：作为项目级 Skill 安装

将本仓库放入目标项目的 Skill 目录，使 Router 位于 Skill 根目录：

```text
<game-project>/
└── .agents/
    └── skills/
        └── shared-game-dev/
            ├── SKILL.md
            ├── docs/
            ├── skills/
            └── templates/
```

如果你还希望直接点名专项 Skill，可以额外暴露需要的目录：

```text
.agents/skills/
├── shared-game-dev/
├── game-design-director/
├── game-ui-ux/
└── game-playtest/
```

不需要一次安装全部专项 Skill。通常先安装 Router，再按项目需要暴露专项 Skill 即可。

## 调用入口

本仓库没有固定的 `/command` 系统。调用方式是自然语言 + Skill 名称。

### Router 调用

```text
请使用 shared-game-dev 处理这个问题：

移动端 HUD 在窄屏上重叠，按钮文字也被裁切。
先给出主 Skill、支援 Skills、执行顺序和需要的证据。
```

Router 应先返回类似：

```text
主 Skill：game-ui-ux
支援 Skills：mobile-game-layout, game-visual-qa
顺序：UI 层级 → 移动端布局 → 视觉回归
```

### 继续执行

路由确认后，再发送：

```text
按这个路由执行最小改动。
每一步都记录修改内容、验证方式、缺失证据和未通过的闸门。
```

### 只做分析

```text
只做审查，不修改文件。
请读取 shared-game-dev 和相关专项 Skill，
输出问题、风险、证据缺口和下一步。
```

## 专项 Skill 调用

专项 Skill 的文件位置是：

```text
skills/<skill-name>/SKILL.md
```

可以直接在请求中点名：

| 任务信号 | 主 Skill | 常用支援 |
|----------|----------|----------|
| HUD 重叠、文字裁切、安全区 | `game-ui-ux` | `mobile-game-layout`, `game-visual-qa` |
| 新玩法、新区域、核心循环 | `game-design-director` | `gameplay-reality-check` |
| 合成、点击、拖动缺少反馈 | `game-feel` | `game-vfx`, `game-audio-feedback` |
| 画面风格不统一 | `game-art-direction` | `game-asset-pipeline`, `game-visual-qa` |
| Cocos 特效、材质、渲染 | `game-vfx` | `game-rendering`, `cocos-creator-visual-adapter` |
| 首局、3/10 分钟体验、留存 | `game-retention-review` | `gameplay-reality-check`, `game-playtest` |
| 版本验收、真实反馈 | `game-playtest` | `game-visual-qa`, `game-retention-review` |

示例：

```text
读取 game-design-director 和 gameplay-reality-check。
检查下一关是否只是换背景、名称和数值。
必须给出 SKIN_SWAP_GATE 结论，并指出新内容是否改变了玩家决策。
```

## 路由示例

### UI 问题

```text
顶部 HUD 重叠，窄屏按钮被裁切。
```

```text
game-ui-ux
→ mobile-game-layout
→ game-visual-qa
```

### 内容差异问题

```text
第二个区域看起来只是换皮，玩家没有新选择。
```

```text
game-design-director
→ gameplay-reality-check
→ game-retention-review
```

### 操作反馈问题

```text
两个物品合并时没有明显的成功反馈。
```

```text
game-feel
→ game-vfx
→ game-audio-feedback
```

### 渲染问题

```text
Cocos Creator 中的特效遮挡目标，移动端也可能卡顿。
```

```text
game-vfx
→ game-rendering
→ cocos-creator-visual-adapter
```

## 项目结构

```text
SKILL.md                         # Router 入口
docs/
  calling-guide.md               # 本教程
  quality-gates.md               # 质量闸门
  router-tests.md                # 路由案例
  workflow.md                    # 游戏项目工作流
skills/
  game-design-director/
  game-ui-ux/
  game-playtest/
  ...                            # 其他专项 Skill
templates/
  game-brief.md                  # 游戏简报
  visual-spec.md                 # 视觉规格
  playtest-report.md             # 试玩报告
pilots/                          # 脱敏后的示例审计摘要
```

## 工作方式

一次完整调用分成五步：

1. 识别任务对象、风险和验收证据。
2. 选择主 Skill 与支援 Skills。
3. 按依赖顺序处理设计、实现、反馈、平台和 QA。
4. 分别输出 CODE QUALITY、GAMEPLAY QUALITY、VISUAL QUALITY、REAL PLAYTEST。
5. 记录失败闸门、证据缺口和下一步。

Router 只负责组织工作，不会替用户证明游戏“好玩”。

## 质量闸门

每次涉及 UI 或移动端时，检查：

```text
UI_OVERLAP = 0
CLIPPED_TEXT = 0
OFFSCREEN_CRITICAL_UI = 0
UNLABELED_CORE_TARGET = 0
SAFE_AREA_VIOLATION = 0
```

每次涉及新内容时，检查：

```text
SKIN_SWAP_GATE
```

如果新内容只改变背景、名称、数量或数值，而没有改变玩家的操作、判断、决策、风险或反馈，必须判定为 FAIL。

每次涉及反馈时，检查：

```text
OVERFEEDBACK_GATE
```

粒子、震屏、击退、动画或音效不得遮挡目标、阻断合理输入，或让小操作使用过大的庆祝效果。

## 输出格式

建议要求 Codex 用以下结构收尾：

```text
ROUTE
- Primary:
- Supporting:

ASSUMPTIONS
- ...

EVIDENCE
- Runtime:
- Visual:
- Playtest:
- Missing:

QUALITY
- CODE QUALITY:
- GAMEPLAY QUALITY:
- VISUAL QUALITY:
- REAL PLAYTEST:

GATES
- Passed:
- Failed:
- Deferred:

NEXT
1. ...
2. ...
3. ...
```

只有必要的专项 Skill 有对应证据，且 Hard Gates 已通过或明确延期时，才可以输出：

```text
GAME DEV SKILL PACK PHASE 2 = PASS
```

这表示流程和证据闭环完成，不等于真人已经证明游戏好玩。

## 如何扩展

- 新增专项 Skill：在 `skills/<skill-name>/SKILL.md` 定义触发信号、输入、流程、Hard Gates、证据和验收标准。
- 新增路由：在根级 `SKILL.md` 的 Route map 中加入主 Skill 与支援 Skill。
- 新增模板：放入 `templates/`，并在工作流或 Router 中明确使用时机。
- 新增验收标准：优先写入 `docs/quality-gates.md`，避免只存在于一次对话中。

扩展后至少检查：

- 路由是否能从自然语言信号触发。
- 专项 Skill 是否有明确的证据要求。
- 自动化结果是否与真人试玩结论分开。
- 新增内容是否真正改变了玩家决策。
