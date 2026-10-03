# 创建空白画布 (CreateCanvas)

创建指定宽高与背景颜色的空白或全透明图像画布，作为后续图形绘制、图层合并、印章盖章与文字排版的底图载体。

## 权限要求
> 无要求

## 子流程
> 不支持

## 运行参数

* `width` (Number)：画布的像素宽度（如 `800`、`1280`、`1920`），默认 `800`。
* `height` (Number)：画布的像素高度（如 `600`、`720`、`1080`），默认 `600`。
* `background_color` (String)：画布的填充背景色。支持 `transparent`（全透明）、`white`、`black`、HEX `#FFFFFF`、RGBA `rgba(255, 255, 255, 0.8)` 等。
* `output_path` (String)：可选。指定保存图像文件的磁盘路径（支持 PNG、JPG、BMP、WEBP 格式）。留空则仅在内存流转输出图像对象。

## 输出
> 返回创建好的图像对象实体，类型为 `image`。下游节点可直接引用或传递至其它绘制与视觉节点。

## 示例
```json
{
  "width": 1280,
  "height": 720,
  "background_color": "transparent",
  "output_path": "C:\\RPA\\output\\canvas.png"
}
```
