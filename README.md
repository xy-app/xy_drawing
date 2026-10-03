# 🎨 图片绘制与条形码 (Graphics & Barcode)

[![Plugin Version](https://img.shields.io/badge/version-0.50.5-blue.svg)](manifest.json)
[![Group](https://img.shields.io/badge/group-Draw-purple.svg)](#)
[![Platform](https://img.shields.io/badge/platform-All-green.svg)](#)
[![License](https://img.shields.io/badge/license-Freeware-brightgreen.svg)](#)

专为自动化报表、计算机视觉后处理、凭证生成与数据安全设计的图形与图像合成套件。提供空白画布创建、几何图形绘制、文字排版、图层贴图盖章、全图防泄密倾斜水印、区域打码脱敏及一维/二维条码生成能力。

---

## 📖 简介 (Overview)

`xy_drawing` 是一站式轻量、高效的纯图形渲染与图像后期合成套件：
- **目标检测可视化**：支持在输入图像上画标注矩形框、置信度标签及半透明填充。
- **动态凭证与图像排版**：支持多行文字绘制、字体回退、描边轮廓以及基于九宫格（Anchor）的图层贴图与公章合成。
- **数据安全脱敏与防伪**：提供全图平铺倾斜防泄密文字水印、纯色遮罩遮挡、马赛克像素化及柔化模糊处理。
- **条形码与二维码生成**：内置标准二维码、Code 128、EAN-13 与 Code 39 条码生成器，支持自定义色系与明文标注。

---

## ✨ 核心特性 (Features)

- **画布与底图管理 (CreateCanvas)**：支持自定义分辨率、透明通道（Alpha）及 HEX/RGBA 背景色，可作为独立合成底图。
- **检测框标绘 (DrawRect)**：专为目标检测与 UI 自动化高亮设计，内置边框粗细、颜色、半透明蒙版及浮动标签（Label）。
- **几何图元库 (DrawShape)**：支持线段（Line）、指示箭头（Arrow）、圆形（Circle）、椭圆（Ellipse）及闭合多边形（Polygon）。
- **专业文字排版 (DrawText)**：支持自定义字体文件、多行换行、文字描边与背景底色色块包裹。
- **九宫格图层叠加 (DrawImage)**：支持前景贴图按比例或固定尺寸缩放，结合 9 种对齐锚点与透明度混合（Opacity）。
- **全屏防泄密水印 (DrawWatermark)**：企业级防截屏泄密方案，支持角度倾斜、双向平铺步长及半透明色彩配置。
- **隐私脱敏处理 (FillColor)**：针对敏感数据提供 `solid`（纯色遮罩）、`mosaic`（马赛克）与 `blur`（柔化模糊）。
- **条形码/二维码生成 (BarcodeCreate)**：无缝生成主流一维条形码及二维码，支持自定义像素尺寸与高对比度色彩。

---

## 🛠️ 动作指令全景速查 (Action Catalog)

| 动作标识 (Tag) | 功能名称 | 描述 | 输出类型 |
| :--- | :--- | :--- | :--- |
| `CreateCanvas` | 创建空白画布 | 创建指定宽高与背景色的空白/透明底图画布 | `image` |
| `DrawRect` | 绘制矩形框 | 绘制带边框、填充底色及置信度标签的检测框/标注框 | `image` |
| `DrawShape` | 绘制几何图形 | 绘制线段、指示箭头、圆形、椭圆及多边形闭合轮廓 | `image` |
| `DrawText` | 绘制文字 | 在指定位置排版渲染文本，支持描边、背景色块与外挂字体 | `image` |
| `DrawImage` | 叠加贴图与印章 | 在底图按九宫格基准叠加贴图、Logo 或电子公章（支持混合与缩放） | `image` |
| `DrawWatermark` | 全图平铺水印 | 整图按倾斜角和步距平铺半透明防泄密文字水印 | `image` |
| `FillColor` | 区域填充与打码脱敏 | 对指定区域进行纯色遮罩、马赛克像素化或模糊隐私脱敏 | `image` |
| `BarcodeCreate` | 生成条形码与二维码 | 批量生成二维码、Code 128、EAN-13 及 Code 39 图像 | `image` |

---

## 📚 详细参数说明与参考 (Detailed Reference)

### 1. `CreateCanvas` - 创建空白画布
创建一张崭新的空白或透明背景底图，供后续图层堆叠。
- **输入参数：**
  * `width` (Number)：画布宽度像素（默认 `800`）。
  * `height` (Number)：画布高度像素（默认 `600`）。
  * `background_color` (String)：支持颜色英文名、HEX 或 RGBA（默认 `transparent`）。
  * `output_path` (String)：可选。指定保存文件的磁盘路径。
- **输出类型：** `image`

### 2. `DrawRect` - 绘制矩形框
在图像上标绘带标签的高亮检测矩形框。
- **输入参数：**
  * `image` (Image)：输入底图。
  * `rect` (String)：目标矩形坐标与尺寸（`"x, y, w, h"` 或 JSON）。
  * `border_color` (String)：外边框颜色（默认 `red`）。
  * `border_thickness` (Number)：边框像素粗细（默认 `2`）。
  * `fill_color` (String)：内部填充色（默认 `transparent`）。
  * `label` (String)：可选。矩形顶部显示的文字标签。
  * `output_path` (String)：可选输出路径。
- **输出类型：** `image`

### 3. `DrawShape` - 绘制几何图形
- **输入参数：**
  * `image` (Image)：输入底图。
  * `shape_type` (String)：`line`, `arrow`, `circle`, `ellipse`, `polygon`。
  * `points` (String)：几何形状坐标点。
  * `color` (String)：线条轮廓颜色（默认 `red`）。
  * `thickness` (Number)：线条宽度（默认 `2`）。
  * `fill_color` (String)：闭合内部填充色。
  * `output_path` (String)：可选输出路径。
- **输出类型：** `image`

### 4. `DrawText` - 绘制文字
- **输入参数：**
  * `image` (Image)：输入底图。
  * `text` (String)：待渲染的多行或单行文字。
  * `x`, `y` (Number)：文字左上角起始坐标。
  * `font_size` (Number)：字号大小（默认 `16`）。
  * `font_color` (String)：文字前景色（默认 `black`）。
  * `font_path` (String)：可选自定义字体文件路径。
  * `background_color` (String)：可选文字背景衬底颜色。
  * `stroke_color` (String)：可选轮廓描边颜色。
  * `output_path` (String)：可选输出路径。
- **输出类型：** `image`

### 5. `DrawImage` - 叠加贴图与印章
- **输入参数：**
  * `image` (Image)：底图。
  * `overlay` (Image)：待叠加的前景贴图/印章。
  * `x`, `y` (Number)：对齐偏移像素。
  * `anchor` (String)：九宫格锚点（默认 `TopLeft`）。
  * `opacity` (Real)：图层不透明度（`0.0 ~ 1.0`，默认 `1.0`）。
  * `scale` (Real)：贴图缩放比例或绝对像素尺寸。
  * `output_path` (String)：可选输出路径。
- **输出类型：** `image`

### 6. `DrawWatermark` - 全图平铺水印
- **输入参数：**
  * `image` (Image)：底图。
  * `text` (String)：水印文本内容。
  * `font_size` (Number)：字号大小（默认 `20`）。
  * `color` (String)：半透明文字颜色（如 `rgba(128, 128, 128, 0.25)`）。
  * `angle` (Number)：倾斜角度（默认 `-30`）。
  * `spacing_x`, `spacing_y` (Number)：网格平铺间距。
  * `font_path` (String)：可选字体路径。
  * `output_path` (String)：可选输出路径。
- **输出类型：** `image`

### 7. `FillColor` - 区域填充与打码脱敏
- **输入参数：**
  * `image` (Image)：底图。
  * `rect` (String)：打码目标区域。
  * `mode` (String)：脱敏模式（`solid`, `mosaic`, `blur`）。
  * `color` (String)：纯色模式下的填充色。
  * `block_size` (Number)：马赛克或模糊核大小（默认 `10`）。
  * `output_path` (String)：可选输出路径。
- **输出类型：** `image`

### 8. `BarcodeCreate` - 生成条形码与二维码
- **输入参数：**
  * `barcode_type` (String)：码制类型（`QRCode`, `Code128`, `EAN13`, `Code39`）。
  * `content` (String)：待编码内容。
  * `width`, `height` (Number)：图像宽高像素。
  * `fg_color`, `bg_color` (String)：条形码前后背景色。
  * `include_text` (Number)：是否附带下方明文文本（`1` 开启, `0` 关闭）。
  * `output_path` (String)：可选输出路径。
- **输出类型：** `image`

---

## 📦 插件配置定义 (Manifest Reference)

```json
{
  "plugin_id": "xy_drawing",
  "name": "图片绘制与条形码 (Graphics & Barcode)",
  "version": "0.50.5",
  "group": "Draw",
  "group_icon": "🎨",
  "description": "提供空白画布创建、几何图形绘制、文字排版、图层贴图盖章、全图防泄密倾斜水印、区域打码脱敏及一维/二维条码生成能力",
  "actions": [...]
}
```
 
---

## 📄 许可证 (License)

本插件遵循免费专有许可协议 (Freeware)。供 小友+ 用户免费下载与使用，未经官方书面授权，严禁对二进制文件进行逆向工程、反编译或二次打包转售。
