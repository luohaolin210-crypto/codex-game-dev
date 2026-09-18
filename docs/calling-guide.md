# Codex Game Dev 调用教程

本教程说明如何在 Codex 中使用本仓库的游戏开发能力库。

参考结构：[pa4uslf/Codex-Game-Studios](https://github.com/pa4uslf/Codex-Game-Studios)

两者定位不同：

- Codex Game Studios 是包含角色、工作流、规则和协调机制的完整工作室模板。
- 本仓库是轻量的游戏开发 Skill Pack：一个 Router、若干专项 Skills、质量闸门、工作流和模板。
- 本仓库不会自动创建团队、自动运行所有流程，也不会替代真人试玩。

## 1. 获取能力库

### 直接让 Codex 阅读仓库

适合先试用或只想在当前任务中调用：

```text
读取 codex-game-dev/SKILL.md。
根据我的游戏任务，选择主 Skill 和支援 Skills，
列出关键假设、需要的证据和未通过的质量闸门。
先不要修改文件。
```

### 安装到游戏项目

把本仓库放进目标游戏项目的 Codex skills 目录，并确保入口文件位于 Skill 根目录：

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

也可以安装到个人 Skill 目录。目录名称建议使用 `shared-game-dev`，这样入口名称和 `SKILL.md` 的 front matter 一致。

如果希望直接调用某一个专项 Skill，再把对应目录暴露到项目或个人 Skill 目录：

```text
.agents/skills/
├── shared-game-dev/       # Router
├── game-ui-ux/            # 可选：直接调用
├── game-playtest/         # 可选：直接调用
└── game-design-director/  # 可选：直接调用
```

不确定时只安装 Router 即可。Router 会根据任务信号读取和组合专项 Skill。

## 2. 推荐的第一次调用

在游戏项目根目录启动 Codex 后，发送：

```text
读取 shared-game-dev。
先检查当前项目处于什么阶段，然后为本次任务选择：
1. 主 Skill
2. 支援 Skills
3. 关键设计假设
4. 需要留下的运行、视觉或试玩证据

只做分析和计划，不修改项目文件。
```

得到路由后，再明确授权实现：

```text
按刚才的路由实现最小可验证改动。
每完成一个阶段都说明：
- 改了什么
- 如何验证
- 哪些证据仍然缺失
- 哪些质量闸门仍未通过
```

## 3. 直接调用 Router

Router 入口是：

```text
SKILL.md
```

调用格式可以很自然，不需要记命令名：

```text
请按 shared-game-dev 路由这个问题：
移动端顶部 HUD 文字重叠，部分按钮在窄屏被裁切。
先给出主 Skill、支援 Skills、检查顺序和证据要求。
```

预期路由：

```text
game-ui-ux
→ mobile-game-layout
→ game-visual-qa
```

Router 的工作顺序是：

1. 识别对象、风险和验收证据。
2. 选择一个主 Skill 和必要的支援 Skills。
3. 按依赖顺序执行：设计假设 → 原型/实现 → 反馈与视觉 → 平台适配 → QA/试玩。
4. 分开输出 CODE QUALITY、GAMEPLAY QUALITY、VISUAL QUALITY、REAL PLAYTEST。
5. 记录未通过闸门和下一步。

## 4. 直接调用专项 Skill

专项 Skill 位于：

```text
skills/<skill-name>/SKILL.md
```

### UI 与移动端布局

```text
读取 game-ui-ux、mobile-game-layout 和 game-visual-qa。
检查当前 HUD 的层级、重叠、裁切、核心目标标识和安全区。
输出问题清单、复现条件和 UI Hard Gate 结果。
```

### 新玩法或新区域

```text
读取 game-design-director 和 gameplay-reality-check。
评估“下一关只是换背景和数值”这个风险。
必须执行 SKIN_SWAP_GATE，并说明新内容改变了哪个玩家决策、风险或反馈。
```

### 合成、点击或拖动缺少爽感

```text
读取 game-feel、game-vfx 和 game-audio-feedback。
把核心动作分为 MICRO、MEDIUM、MAJOR 或 CELEBRATION，
检查输入响应、动画、音效、粒子、镜头和结果是否服务于同一个反馈。
同时执行 OVERFEEDBACK_GATE。
```

### 试玩与版本验收

```text
读取 game-playtest、game-visual-qa 和 game-retention-review。
为当前版本设计从自动化检查到真人试玩的证据矩阵。
明确每种证据能证明什么，不能证明什么。
```

## 5. 常用任务模板

### 设计阶段

```text
读取 shared-game-dev 和 templates/game-brief.md。
把下面的想法整理成一页游戏简报：
[描述想法]

先指出最大的不确定性，再给出最小垂直切片。
不要扩展到完整内容生产。
```

### 视觉方向

```text
读取 game-art-direction、game-asset-pipeline 和 templates/visual-spec.md。
为当前项目建立视觉规格，覆盖题材、情绪、材质、色彩、层级、构图和资产命名。
标出哪些判断需要截图或目标设备验证。
```

### 试玩记录

```text
读取 game-playtest 和 templates/playtest-report.md。
根据以下试玩记录整理报告：
[记录玩家做了什么、卡在哪里、说了什么]

把问题分成 Code、Gameplay、Visual、Real Playtest，
不要把自动化通过写成“游戏好玩”。
```

## 6. 质量闸门

调用后至少检查这些硬闸门：

```text
UI_OVERLAP = 0
CLIPPED_TEXT = 0
OFFSCREEN_CRITICAL_UI = 0
UNLABELED_CORE_TARGET = 0
SAFE_AREA_VIOLATION = 0
```

另外必须检查：

- SKIN_SWAP_GATE：新内容不能只换背景、名称、数量或数值。
- OVERFEEDBACK_GATE：反馈不能遮挡、阻断输入或让小操作使用过大的庆祝效果。
- 核心目标不能只靠颜色表达，应优先使用文字、图标和色彩组合。
- 自动化测试、Mock、Headless 或 Build PASS 不能替代真人试玩。

## 7. 一次完整调用示例

```text
我正在做一个移动端合成游戏，当前问题是：
玩家完成第一个区域后，第二个区域只是换了背景和家具名称；
同时合成成功的反馈不够明显。

请使用 shared-game-dev：
1. 先路由主 Skill 和支援 Skills。
2. 用 gameplay-reality-check 和 game-design-director 执行 SKIN_SWAP_GATE。
3. 用 game-feel、game-vfx 和 game-audio-feedback 检查合成反馈。
4. 给出最小改动方案，不要直接扩展大量内容。
5. 输出 CODE QUALITY、GAMEPLAY QUALITY、VISUAL QUALITY、REAL PLAYTEST 四项结论。
6. 列出需要我实际试玩或在真机验证的项目。
```

## 8. 如何判断调用是否完成

不要只看“代码改完了”。一次合格的调用应留下：

- 触发信号和实际路由
- 主 Skill 与支援 Skills
- 关键设计假设
- 可复现的运行或试玩步骤
- 四类质量结论
- 未通过的闸门
- 下一轮最多三项优先任务

只有必要的专项 Skill 都有证据、Hard Gates 通过或被明确延期时，才能报告：

```text
GAME DEV SKILL PACK PHASE 2 = PASS
```

这个状态表示流程和证据闭环完成，不等于游戏已经被真人证明好玩。
