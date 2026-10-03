# 叠加贴图与印章 (DrawImage)

在目标底图上按九宫格方位或指定像素偏移叠加贴图、Logo、电子印章、签名或子图截图。支持精确缩放比例、多图层 Alpha 透明度混合与边缘平滑。常用于电子发票盖章、报告添加企业标识以及多图拼贴。

## 权限要求
> 无要求

## 子流程
> 不支持

## 运行参数

* `image` (Image)：背景底图，支持图像对象变量、文件路径或 Base64。
* `overlay` (Image)：待叠加覆盖的前景图像（如印章 PNG、Logo、签名图片）。
* `x` (Number)：距离基准对齐点的水平像素偏移，默认 `0`。
* `y` (Number)：距离基准对齐点的垂直像素偏移，默认 `0`。
* `anchor` (String)：贴图定位基准方位，可选 `TopLeft`、`TopCenter`、`TopRight`、`CenterLeft`、`Center`、`CenterRight`、`BottomLeft`、`BottomCenter`、`BottomRight`（右下角，常用于盖章）。
* `opacity` (Real)：叠加透明度，支持 `0.0 ~ 1.0` 浮点数，默认 `1.0`。
* `scale` (Real)：贴图缩放比例（如 `0.5`、`1.2`）或绝对像素尺寸（如 `"150,150"`）。
* `output_path` (String)：可选。输出图像保存路径。

## 输出
> 返回合并盖章后的图像对象，类型为 `image`。

## 示例
```json
{
  "image": "$invoice_doc",
  "overlay": "C:\\RPA\\assets\\official_seal.png",
  "anchor": "BottomRight",
  "x": -30,
  "y": -30,
  "opacity": 0.9,
  "scale": "180,180",
  "output_path": "C:\\RPA\\output\\stamped_invoice.png"
}
```
