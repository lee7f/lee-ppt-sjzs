# 字号映射

用于从已确认设计稿还原 PPT 原生文字。目标是让字形高度接近设计稿，而不是让标题字号保守。

## 语义层级

先为每个文本框标注语义层级：`cover-title`、`cover-subtitle`、`page-title`、`section-title`、`subtitle`、`body`、`caption`、`data-large`、`data-small`、`label`、`page-number`。

同一语义层级的字体、字重、颜色、行高和字号规则必须一致。不要按单词或单行拆文本框；按语义文本块拆分，保持基线、容器边界和阅读顺序。

## 映射公式

记录源设计稿页面尺寸和目标 PPT 页面尺寸，使用归一化坐标映射边界：

```text
targetGlyphHeightPt = glyphHeightPx / sourcePageHeightPx * targetPageHeightPt
fontPtRaw = targetGlyphHeightPt * fontCalibrationFactor
fontPt = ceil(fontPtRaw)
```

`fontCalibrationFactor` 按字体、字重和渲染环境校准。导出 PPT 快照后用最多 2 轮修正：

```text
correctedFontPt = currentFontPt * targetGlyphHeightPx / renderedGlyphHeightPx
fontPt = ceil(correctedFontPt)
```

## 优先级

字号来源优先级为：已确认设计稿映射 > 已确认模板 > 项目语义字号表 > 无可靠视觉基准时的保底字号。存在已确认设计稿或模板时，以映射结果为准，不用保底字号覆盖。仅在没有可靠视觉基准时使用以下下限：

- `cover-title` 不低于 `50pt`
- `page-title` 不低于 `35pt`
- `subtitle` 不低于 `24pt`
- `body` 不低于 `16pt`
- `caption` 不低于 `12pt`
- `page-number` 不低于 `10pt`

封面标题、正文页标题、正文、数据数字和页码必须各选至少一个样本做渲染校准。字形高度误差以不超过 `5%` 为目标；受整数字号或字体渲染限制无法达到时，采用误差最小的整数值，并在交付反馈中标注实际偏差。

## 文本框

文本框边界来自确认稿归一化坐标。高度可随文字适配，锚点、宽度、对齐和阅读顺序保持不变；仅在处理文字溢出时允许在尺寸误差 `3%` 内调整宽度。原生文字行高固定 `1.2`、内边距固定 `0`；这两个参数不参与字号推导。

禁止自动缩小字体。标题或关键数字出现换行风险时，按顺序处理：校准字号、在尺寸误差 `3%` 内调整文本框宽度、调整字间距、人工换行、压缩文案、返回页纲或设计稿确认。固定行高 `1.2`、内边距 `0` 和整数字号优先于像素级完全复刻；在固定约束内采用误差最小的结果。

## QA

最终 QA 必须导出 PNG 并叠加对比确认稿，检查坐标、容器、基线和字形高度。内部映射可记录 `sourceBoundsNormalized`、`targetBounds`、`targetGlyphHeight`、`fontFamily`、`fontWeight`、`fontSize`、`calibrationFactor`、`renderedGlyphHeight` 和 `errorRate`，但不要展示给用户。
