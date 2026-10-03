# 绘制文字 (DrawText)

在图像指定坐标渲染单行或多行格式化文字，支持自定义字号、文字颜色、背景底色横幅、描边轮廓边缘与系统字体回退。适用于为图片添加标题、水印、动态批注及报告卡片。

## 权限要求
> 无要求

## 子流程
> 不支持

## 运行参数

* `image` (Image)：待绘制的目标底图，支持图像对象变量、文件路径或 Base64。
* `text` (String)：待绘制的文本字符串。支持 `\n` 换行符自动排版渲染多行文字。
* `x` (Number)：文字起始水平坐标（像素），默认 `10`。
* `y` (Number)：文字起始垂直坐标（像素），默认 `10`。
* `font_size` (Number)：字体大小（像素），默认 `16`。
* `font_color` (String)：文字前景色（支持 HEX 如 `#FFFFFF`、RGBA 或名称），默认 `black`。
* `font_path` (String)：可选。自定义字体文件路径（`.ttf`、`.otf`、`.ttc`）。留空则自动回退至系统内置字体。
* `background_color` (String)：可选。文字后方的矩形背景衬底颜色（如 `rgba(0, 0, 0, 0.6)`），留空则透明无底色。
* `stroke_color` (String)：可选。文字轮廓描边颜色（如 `white` 或 `black`），使文字在复杂背景上依然保持清晰可读。
* `output_path` (String)：可选。输出图像保存路径。

## 输出
> 返回渲染文字后的图像对象实体，类型为 `image`。

## 示例
```json
{
  "image": "$screenshot",
  "text": "财务凭证核验通过\n操作员: 工号0891\n时间: 2026-09-04 15:30",
  "x": 20,
  "y": 20,
  "font_size": 18,
  "font_color": "#FFFFFF",
  "background_color": "rgba(31, 41, 55, 0.75)",
  "stroke_color": "black",
  "output_path": "C:\\RPA\\verified.png"
}
```
