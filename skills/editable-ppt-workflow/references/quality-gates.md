# 验收标准

## 新建 PPT

- 每页有一个可复述的结论型标题，封面和结尾页简洁。
- 文字与数据自洽；图表总和、比例、单位、时间范围和标题一致。
- 全稿的字体、色板、边距、页码和页脚一致；无占位符或虚构来源。
- 全稿所有字号均为向上取整后的整数 pt；不得出现小数字号。
- 所有页面已渲染检查：无溢出、截断、意外重叠、错误换行或低对比。
- 所有可见文字、数字和标签均能在 PowerPoint 中编辑。

## 视觉重建追加项

- 每页底层恰好一张铺满页面的无字 PNG，不能是带字原图。
- 文本层完全隐藏后，底图无中英文、数字、百分比、页码、假字、残影、遮盖块或补丁。
- 移动/隐藏任一文字框，原位置不会出现旧文字。
- 每个文本框都能追溯到原图的归一化边界和语义组；位置与尺寸按叠加比对通过，锚点偏移不超过页面对应边长的 1%，尺寸偏差不超过 3%。
- 同角色文字遵循从原图推导的字号、字重和行距体系；所有字号向上取整为整数 pt；不得为塞入内容而缩小字号或触发自动缩放。
- 当参考图与交付画布尺寸不一致时，坐标、边界和字号均按页面比例映射；不得复用原图的像素坐标或像素字号。标题和正文的渲染字形高度须完成校准，映射后的视觉高度误差不超过 5%。
- 每个多行段落、引用或列表说明均为一个完整文本框，保留原始换行与段落格式，不得逐行拆分。
- 文本框、段落与容器的水平/垂直对齐、内边距、基线和列间距已按原图锚点核对。
- 所有原始视觉元素均保留在底图，且没有被误拆成卡片、图标、图表或按钮等独立可见对象。
- `assets/`、`reference/`、`masks/`、`manifest.json` 和 `preview/contact-sheet.png` 齐全，文件名按页码递增且能对应。

## manifest 最小结构

```json
{
  "slideSize": {"width": 13.333, "height": 7.5, "unit": "in"},
  "slides": [{
    "number": 1,
    "reference": "reference/slide-01-reference.png",
    "background": "assets/slide-01-background.png",
    "mask": "masks/slide-01-text-mask.png",
    "layerModel": "one-background-image-plus-editable-text",
    "textBoxes": [{"text": "...", "role": "body", "groupId": "body-01", "sourceBoundsNormalized": {"x": 0, "y": 0, "w": 0.2, "h": 0.1}, "sourceLineCount": 2, "x": 0, "y": 0, "w": 1, "h": 1, "fontSize": 24, "fontSizeRule": "ceil-to-integer-pt", "color": "#111111", "bold": false, "align": "left", "verticalAlign": "top", "lineSpacing": 1.2, "margin": {"left": 0, "right": 0, "top": 0, "bottom": 0}}]
  }]
}
```
