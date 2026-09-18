# Router Tests

验证自然语言任务能自动选择专项 Skills；如果仍需要人工每次指定 Skill，则 SKILL_ROUTING = FAIL。

| Input signal | Expected route |
| --- | --- |
| HUD 重叠 | game-ui-ux → mobile-game-layout → game-visual-qa |
| 下一关只是换皮 | game-design-director → gameplay-reality-check → game-retention-review |
| 合成没有爽感 | game-feel → game-vfx → game-audio-feedback |
| 画面不好看 | game-art-direction → game-asset-pipeline → game-visual-qa |
| Cocos 特效差 | game-vfx → game-rendering → cocos-creator-visual-adapter |
| 移动端 UI 被遮挡 | mobile-game-layout → game-ui-ux → game-visual-qa |
| 想知道玩法是否成立 | gameplay-reality-check → game-playtest |
| 需要首局和 10 分钟留存 | game-retention-review → game-playtest |

## Test protocol

1. 将每条输入作为独立任务交给 Router。
2. 记录主 Skill、支援 Skills、触发的 Hard Gates 和证据要求。
3. 不允许人工补写路由；人工只能检查路由结果。
4. 任何漏选、错选或没有证据要求都算失败。

## Result

SKILL_ROUTING = PASS 仅当上述案例全部路由正确；本文件定义测试，实际运行结果必须在版本验收记录中填写。
