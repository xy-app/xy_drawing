# 全图平铺水印 (DrawWatermark)

在整张图像上以指定倾斜角度、网格间距和半透明度平铺防泄密文字水印。广泛应用于企业级 RPA 场景中的员工敏感数据查看、电子合同防翻拍留痕、以及系统自动归档文档的版权保护。

## 权限要求
> 无要求

## 子流程
> 不支持

## 运行参数

* `image` (Image)：待打水印的原始底图，支持变量、文件路径或 Base64。
* `text` (String)：平铺水印内容，如 `"内部机密 · 请勿外传"`、`"张三 - 2026/09/04"` 等。
* `font_size` (Number)：文字字号大小（像素），默认 `20`。
* `color` (String)：带透明度的水印颜色（如 `rgba(128, 128, 128, 0.25)`），建议透明度在 15%~30% 之间。
* `angle` (Number)：水印文字倾斜角度（度数，负数为逆时针倾斜，如 `-30`、`-45`），默认 `-30`。
* `spacing_x` (Number)：网格平铺水平像素跨度，默认 `240`。
* `spacing_y` (Number)：网格平铺垂直像素跨度，默认 `160`。
* `font_path` (String)：可选。自定义字体路径，留空默认回退至系统内置字体。
* `output_path` (String)：可选。输出图像保存路径。

## 输出
> 返回添加全屏防伪水印后的图像对象，类型为 `image`。

## 示例
```json
{
  "image": "$contract_page",
  "text": "某某科技内部机密 - 审批单据专用",
  "font_size": 22,
  "color": "rgba(100, 116, 139, 0.22)",
  "angle": -35,
  "spacing_x": 260,
  "spacing_y": 180,
  "output_path": "C:\\RPA\\output\\watermarked_contract.png"
}
```
