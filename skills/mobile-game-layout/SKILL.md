---
name: mobile-game-layout
description: 针对移动端安全区、触控、比例变化和拥挤状态优化布局。
---

# mobile-game-layout

## Purpose

针对移动端安全区、触控、比例变化和拥挤状态优化布局。

## Trigger

移动端发布、竖屏/横屏切换、刘海屏、全面屏或触控问题。

## Required Inputs

- 设备/分辨率矩阵
- 安全区参数
- 拇指可达区域
- 横竖屏策略
- 关键操作列表

## Workflow

1. 建立设备矩阵并标注安全区。
2. 定义核心操作和拇指可达区域。
3. 检查锚点、伸缩、文字换行和弹窗层级。
4. 在最窄、最高和异形比例下运行。
5. 与 game-ui-ux 和 game-visual-qa 交叉验收。

## Hard Gates

- SAFE_AREA_VIOLATION = 0。
- OFFSCREEN_CRITICAL_UI = 0。
- 核心触控目标不互相遮挡。
- 旋转或恢复窗口后状态不丢失。

## Failure Conditions

- 只在开发者设备上验证。
- 用固定像素放置关键 UI。
- 系统区域遮挡核心操作。

## Evidence Required

- 设备矩阵截图/录屏
- 安全区标注
- 触控路径记录
- 极端比例验收

## Acceptance Criteria

- 目标设备矩阵核心路径均可完成。
- 关键按钮可单手触达且不会误触。

## Forbidden Shortcuts

- 只用模拟器一个尺寸验收。
- 把桌面布局等比缩小到手机。