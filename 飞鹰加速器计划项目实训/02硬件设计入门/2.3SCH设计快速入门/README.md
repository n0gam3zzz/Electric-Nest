# 2.3 SCH设计快速入门

* Updated in 2022/09/25 16:24

## NOTE

* 原理图
  * 定义
    * 表示电路板上各器件之间连接原理的图表，反映各电子元器件之间的电气连接关系
  * 组成
    * 一般包含电子元器件原理图符号，电气连接线，网络标号，字符标注等
* 原理图符号绘制注意事项
  * 层次总图设计
    * 采用自下而上层次总图方式绘制原理图时，层次模块必须由执行Design/Create Symbol from Sheet获得，而不能通过Place/SheetSymbol之后再手工编辑。超过两张（含两张)子图纸时采用层次总图
  * 分模块
    * 单张原理图用线把原理图划分好区域，再各个区域做好功能说明，多个功能模块也可以用多张原理图绘制
  * Net Label要求
    * Net Label命名应简单、直观，长度再10各字符以内为佳；
    * 应符合国家标准GB/T 1679《信号和连接线的代号》、GB/T 6988.1~6988.3《电气技术用文件的编制》的相关规定
    * 避免直接连接在引脚上或未连接上的情况
* 原理图绘制流程
  * 添加原理图符号库文件
  * 调用原理图符号
  * 电气连接
  * 编排位号
  * 规则检查
  * 导出BOM表（PCB中所有元气件的清单）

### 操作

#### `EN-C200-OPT_RA1.SchDoc`

* 旋转元器件
  * 选中元器件且没有放置时 `X` 可以水平翻转
  * 选中元器件且没有放置时 `Y` 可以水平翻转
* 走线
  * `Shift + Space` 切换走线(45°/90°/任意角度/自动走线)
  * `Backspace` 撤回上一步走线
  * `Delete` 删除走线
  * `左键` 改变走线
  * `右键` 退出走线
  * 交叉走线中添加结点 `Place - Manual Junction`
* 自动编号 `Tools` - `Annotate Schematics...`
  * `Update Changes List` 更改全部
  * `Accept Changes` 接受更改
  * `Validate Changes` 检查更改
  * `Execute Changes` 执行更改
* 电气图检查
  * 设置错误等级 `Project` - `Project Options...` - `Error Reporting`
  * 检查错误 `Project` - `Compile Document`
  * 显示错误信息 `View` - `System` - `Workspace Panels` - `Messages`
* 导出BOM表 `Reports` - `Bill Materials`
  * `Export` 导出

#### `EN-C200-OPT_RA1.PrjPCB`

* 原理图网表生成 `Design` - `Netlist For Project` - `Protel`
* PCB设计报告输出 `Reports` - `Board Information`

## 上传的文件

* 原理图设计文件 `EN-C200-OPT_RA1.SchDoc`
* 原理图网表文件 `EN-C200-OPT_RA0.NET`
* 单板原理图BOM `EN-C200-OPT_RA0_BOM.xls`
* PCB结构要素图 `EN-C200-OPT_RA0.dxf` 更改从参考文件中下载的 `光传感器扣板结构图.dxf` 文件名即可
* 光传感器扣板项目原理图设计checklist `全部通过即可`
