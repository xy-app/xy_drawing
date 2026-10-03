# 绘制矩形框 (DrawRect)

在目标底图上绘制指定粗细边框、内部填充色及可选文字标签的矩形框。广泛用于 AI 目标检测结果可视化标注（如识别框）、OCR 检测范围高亮显示以及流程指引标注。

## 权限要求
> 无要求

## 子流程
> 不支持

## 运行参数

* `image` (Image)：待绘制的底图，支持图像对象变量、本地文件绝对路径或 Base64 字符串。
* `rect` (String)：目标矩形的位置与尺寸。支持 `"x, y, width, height"`（如 `"100, 100, 200, 150"`）或 JSON 数组/对象。
* `border_color` (String)：矩形外边框颜色，支持 `red`、`green`、`blue`、`#FF0000`、`rgba(255, 0, 0, 1.0)` 等，默认 `red`。
* `border_thickness` (Number)：边框线条的像素宽度（如 `1`、`2`、`3`、`5`），默认 `2`。
* `fill_color` (String)：矩形内部的背景填充色。默认 `transparent` 不填充；可设置为半透明（如 `rgba(255, 0, 0, 0.2)`）以实现高亮区域蒙版效果。
* `label` (String)：可选。在矩形框顶部附带绘制标签文字及背景横幅（如 `"person: 0.98"`、`"发票抬头"`）。
* `output_path` (String)：可选。若指定则将合成后的图像保存至磁盘路径；留空直接输出内存图像对象。

## 输出
> 返回绘制并合成后的图像对象，类型为 `image`。

## 示例
```json
{
  "image": "$capture_window.image",
  "rect": "150, 200, 300, 80",
  "border_color": "#00FF00",
  "border_thickness": 3,
  "fill_color": "rgba(0, 255, 0, 0.15)",
  "label": "登录按钮: 0.99",
  "output_path": "C:\\RPA\\annotated.png"
}
```
