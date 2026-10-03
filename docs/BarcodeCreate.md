# 生成条形码与二维码 (BarcodeCreate)

根据给定的文本字符串或编码数字，自动生成标准工业与商业一维条形码（Code 128、EAN-13、Code 39）或二维码（QR Code）。支持自定义分辨率、前景色与背景色、以及条码底部自动渲染明文文本标签。广泛应用于电商发货单打印、物料追踪、资产管理标签与移动扫码跳转场景。

## 权限要求
> 无要求

## 子流程
> 不支持

## 运行参数

* `barcode_type` (String)：码制类型，支持 `QRCode` (二维码)、`Code128` (高密度一维码)、`EAN13` (商品零售码)、`Code39` (工业防伪条码)。
* `content` (String)：待编码的文本、链接或数字字符串（如 `"SF1234567890"`、`"https://example.com"`）。
* `width` (Number)：输出图像像素宽度，默认 `200`。
* `height` (Number)：输出图像像素高度，二维码默认 `200`，一维条形码默认 `80`。
* `fg_color` (String)：编码条纹与文字的前景色，默认 `black`。
* `bg_color` (String)：条形码画布底色，默认 `white`；支持设置为 `transparent` 以获得透明底条码。
* `include_text` (Number)：是否在一维条形码下方自动居中渲染明文标签（`1` 开启，`0` 关闭），默认 `1`。
* `output_path` (String)：可选。输出条码图像的保存磁盘路径。

## 输出
> 返回生成的条形码或二维码图像对象，类型为 `image`。

## 示例
```json
{
  "barcode_type": "Code128",
  "content": "JD0092817345",
  "width": 320,
  "height": 90,
  "fg_color": "black",
  "bg_color": "white",
  "include_text": 1,
  "output_path": "C:\\RPA\\labels\\shipping_label.png"
}
```
