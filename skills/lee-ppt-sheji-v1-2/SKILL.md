---
name: lee-ppt-sheji-v1-2
description: Use when creating editable PPTX decks with V1.2 concise staged workflow, separate stage documents, demand typing, source parsing, style demos, page plans, layer options, and acceptance checks.
---

# 可编辑 PPT 工作流 V1.2

目标始终是交付真正可编辑的 `.pptx`，不是页面图片。涉及图像生成、风格 Demo、整套 image 设计稿、底图、插画生成或修复时，按需调用 `imagegen`。

## 工作原则

- 先图文一体设计，后拆层交付。
- image 设计稿是确认依据；拆层素材是最终结构。
- 不得先做无字底图，再硬贴文案替代设计稿确认。
- 资料中没有的补全必须标注为“AI 规划”。
- 问用户时保持简短，能少则少。

## 阶段门禁

涉及新建、重排、重做、大幅改版 PPT 时，必须按阶段推进。每阶段完成后暂停，等用户确认。

只有用户明确说“跳过流程，直接生成最终 PPT”或同等含义，才允许跳过阶段门禁。

阶段文档按需读取：

1. [阶段 1：资料入口确认](references/stage-1-intake.md)
2. [阶段 2：综合信息确认](references/stage-2-confirmation.md)
3. [阶段 3：风格 Demo 确认](references/stage-3-style-demo.md)
4. [阶段 4：整套 image 设计稿](references/stage-4-image-draft.md)
5. [阶段 5：拆层与素材整理](references/stage-5-layering.md)
6. [阶段 6：PPTX 制作与验收](references/stage-6-delivery.md)

执行到某阶段前，必须读取对应阶段文档。

## 文本硬规范

- 所有 PPT 原生文字行高统一为 `1.2`。
- 文本框默认跟随文字大小。
- 文本框内边距统一为 `0`。
- 相同层级文字使用相同字体、字号、字重、颜色和行高。
- 封面和封底不计入正文页码。
- 正文第一页从 `01` 或 `1` 开始。
- 带文案 image 设计稿必须带页码。
- 无字底图不得包含文字、数字、页码或 logo 文案。
- 最终 PPTX 页码使用 PPT 原生文本层或母版元素。

## 回复规则

- 阶段 1 的入口回复优先级最高，必须按 `references/stage-1-intake.md` 的指定文案执行。
- 用户仅调用技能且未提供资料时，只输出：`请先补充资料；若没有资料，我将按主题引导。`，并在下一行输出：`【回复约定】后续回复 0 表示确认、接受 AI 建议或进入下一步。`
- 上述无资料入口不得添加阶段名、已启用技能、后续流程、上传方式、资料格式或任何额外句子。
- 除阶段 1 入口和阶段 2 外，每次回复开头声明当前阶段。
- 阶段 2 必须使用标题：`阶段 2：综合确认结果`。
- 阶段 1 仅在无资料入口、已经开始 QA 收集或边界确认时，可提示一次：`【回复约定】后续回复 0 表示确认、接受 AI 建议或进入下一步。`
- 后续不得重复解释 `0` 的含义。
- 用户确认后，用一句话归纳已确认信息，并进入下一阶段。

## 禁止事项

- 未确认核心内容或附件前，不得规划页数。
- 未确认阶段 3 风格 Demo，不得生成整套 image 设计稿或 PPTX。
- 未确认整套带文案 image 设计稿，不得制作 PPTX。
- 未确认拆层维度，不得拆层或制作 PPTX。
- 不得用低保真脚本草图冒充高质量 Demo。
- 不得只用文字说明让用户定风格。
- 不得把风格 Demo 图直接铺成每页背景。
- 图标只输出 SVG。
- 插画只输出 PNG。
- 素材文件夹不得按页创建子文件夹。

## 交付结构

```text
delivery/
├── <topic>-editable.pptx
├── preview-pages/
├── preview-contact-sheet.png
├── page-plan.md
├── backgrounds-no-text/
├── illustrations-png/
├── icons-svg/
├── source-or-reference/
└── manifest.json
```

最终说明只报告：产物位置、页数、采用风格 / 关键假设、已完成验证、主要过程文件夹位置。
