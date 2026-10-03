# 绘制几何图形 (DrawShape)

在图像上绘制直线、带箭头指示线、圆形、椭圆或自定义多边形闭合区域，支持自定义线条粗细、描边颜色与内部填充色。常用于操作指引箭头、截图标注圈画与复杂图形绘制。

## 权限要求
> 无要求

## 子流程
> 不支持

## 运行参数

* `image` (Image)：待绘制的目标底图，支持变量引用、文件路径或 Base64。
* `shape_type` (String)：绘制的几何形状种类，支持 `line` (直线)、`arrow` (指示箭头)、`circle` (圆形)、`ellipse` (椭圆)、`polygon` (闭合多边形)。
* `points` (String)：几何形状的坐标数据。直线/箭头为 `"x1, y1, x2, y2"`；圆形为 `"center_x, center_y, radius"`；椭圆为 `"center_x, center_y, rx, ry"`；多边形为分号分隔的顶点列表 `"x1,y1; x2,y2; x3,y3"`。
* `color` (String)：轮廓与线条颜色（支持 HEX、RGBA、名称），默认 `red`。
* `thickness` (Number)：线条像素宽度，默认 `2`。
* `fill_color` (String)：针对闭合图形（圆形、椭圆、多边形）的内部填充颜色，默认 `transparent` 不填充。
* `output_path` (String)：可选。输出图像保存路径。

## 输出
> 返回绘制完成后的图像对象实体，类型为 `image`。

## 示例
```json
{
  "image": "$screenshot",
  "shape_type": "arrow",
  "points": "50, 50, 260, 260",
  "color": "#3B82F6",
  "thickness": 3
}
```
