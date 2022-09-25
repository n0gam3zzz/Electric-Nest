# 2.2 PCB封装库创建

* Updated in 2022/09/25 10:30

## BH1750HVI分装信息

* 焊盘中心距为0.50mm
* 焊盘宽度为0.25mm
* 焊盘长度为0.55mm
* 两个焊盘之间为2.2mm

## 命名规范

* 命名：SOP6-20-105
* 高度：29.528mil
* 描述：16位输出型光强度传感器
*
* BGA127P + Number of Pin Columns X Number of Pin Rows - Pin Qty
  * BGA127P 引脚行数 X 引脚列数 - 引脚总数

## PCB创建操作

* 器件吸附在鼠标即没有放置时按下 `Tab` 可以编辑其属性
* `Q` 可以切换单位
* 在器件属性界面中，`Ctrl + Q` 可以切换单位
* `Space` 旋转器件
* 放置焊盘：Place - Pad
* 放置线：Place - Line
* 放置文本：Place - String

### 焊盘1

* Location
  * X: 0mm
  * Y: 0mm
* Properties
  * Designator: 1
  * Layer: Top Layer
* Size and Shape
  * X-Size: 0.25mm
  * Y-Size: 0.55mm
  * Shape: Rectangular

### 焊盘2

* Location
  * X: 0mm
  * Y: -0.5mm

### 焊盘3

* Location
  * X: 0mm
  * Y: -1mm

### 焊盘4

* Location
  * X: 2.75mm
  * Y: -1mm

### 焊盘5

* Location
  * X: 2.75mm
  * Y: -0.5mm

### 焊盘6

* Location
  * X: 2.75mm
  * Y: 0mm

### 线

* Layer: Top Overlay
* Width: 0.127mm

### 禁止布线区域

* Layer: Top Layer
* 选择引脚和线之间的矩形区域即可

### 引脚标识

* Text: 1
* Layer: Top Overlay
* Width: 0.127mm
* Height: 0.762mm

### 设置中心点

* Edit - Set Refrence - Center

## 上传的文件

* `WSOF6-20-10.PcbLib`
* `WSOF6-20-10.lia`
