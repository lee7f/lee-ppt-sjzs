# editable-ppt-workflow

一个用于 Codex 的可编辑 PPT 工作流技能，适合把文案、旧 PPT、截图、PDF 或品牌素材重新梳理为高质量、可追溯、可编辑的 PowerPoint 文件。

## 适用场景

- 重新设计 PPT 内容结构和页面风格
- 将旧 PPT 内容重组为更清晰的汇报、路演、培训或提案材料
- 将参考图、截图或视觉稿拆解为“无字底图 + 可编辑文字层”的 PPTX
- 需要先通过 Image 生成带真实文案的风格 Demo，再制作可编辑 PPTX

## 核心原则

先图文一体设计，后拆层交付。

无字底图不是设计起点，而是用户确认带文案设计稿后的最终拆层结果。

## 当前流程

1. 阶段 1：核心内容或附件确认
2. 阶段 2：基础信息整合确认
   - 目标场景
   - 受众
   - 品牌要求
   - 页面比例
   - 内容页数
3. 阶段 3：风格偏好与关键页 Demo 可视化确认
4. 阶段 4：主风格锁定
5. 阶段 5：整套图片排版预览
6. 阶段 6：无字底图拆层
7. 阶段 7：可编辑 PPTX 制作

## 阶段 2 交互方式

阶段 2 虽然整合为一个阶段，但仍然逐题问答，每次只问一个问题，等待用户回答后再进入下一题。

固定顺序：

```text
目标场景 → 受众 → 品牌要求 → 页面比例 → 内容页数
```

用户可以直接回复编号、组合编号、简短文字，或用 `0` 采纳当前 AI 推荐 / 默认值。

## 交付结构

```text
delivery/
├── <topic>-editable.pptx
├── backgrounds-no-text/
├── preview-pages/
├── preview-contact-sheet.png
├── source-or-reference/
└── manifest.json
```

## 安装方式

将 `skills/editable-ppt-workflow` 文件夹复制到 Codex 技能目录。

也可以下载 `editable-ppt-workflow.zip`，解压后把其中的 `editable-ppt-workflow` 文件夹放入技能目录。

## 文件说明

- `skills/editable-ppt-workflow/SKILL.md`：技能主规则
- `skills/editable-ppt-workflow/references/project-intake.md`：项目填写单与推荐选择表
- `skills/editable-ppt-workflow/references/quality-gates.md`：质量检查参考
- `editable-ppt-workflow.zip`：可分享压缩包

## 许可证

当前未附加开源许可证。若发布为公开仓库，请在发布前确认许可证策略。
