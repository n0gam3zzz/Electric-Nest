# OLED模块电路原理图设计

## 操作

* 旋转元器件
  * 选中元器件且没有放置时 `X` 可以水平翻转
  * 选中元器件且没有放置时 `Y` 可以垂直翻转
  * 选中元器件且没有放置时 `Space` 可以逆时针旋转

## 步骤

### 下载文件

* 使用 [之前任务](https://github.com/n0gam3zzz/Electric-Nest/tree/main/飞鹰加速器计划项目实训/04硬件设计实训/4.1MCU小系统原理图设计) 课程参考 - 【EN-C200 AD 元器件库】 - `EN-C200_RA2_ADlib.rar` 解压缩得到 `EN-C200_RA0.PcbLib` 和 `EN-C200_RA0.SchLib`
* 下载 课程参考 - 【原理图设计样例】 - `OLED电路原理图设计样例.pdf`
  * __对照该文件进行原理图设计__
* 使用 [之前任务](https://github.com/n0gam3zzz/Electric-Nest/tree/main/飞鹰加速器计划项目实训/04硬件设计实训/4.1MCU小系统原理图设计) 课程参考 - 【BOM表样例】 `EN-C200_RA2-BOM.pdf`
  * __对照该文件进行元器件的封装更改__

### 创建工程文件 `EN-C200_RA0.PrjPCB`

* 创建工程 `File` - `New` - `Project` - `PCB Project` 并保存为 `EN-C200_RA0.PrjPCB`
* 右键 `EN-C200_RA0.PrjPCB` - `Add Existing to Project...` 将之前解压缩得到的 `EN-C200_RA0.PcbLib` 和 `EN-C200_RA0.SchLib` 添加
* 右键 `EN-C200_RA0.PrjPCB` - `Add new to Project` - `Schematic` 并保存为 `EN-C200_RA0_OLED.SchDoc`

### `EN-C200_RA0_OLED.SchDoc`

* 查看库: `View` - `Workspace Panels` - `System` - `Libraries`
* 只查看导入的库: `Libraries` 窗口 - `Libraries...` - `Installed` 选项卡 - 全部不勾选
* 放置原理图符号: `Place` - `Part...`, 点击 `OK` 放置
* 设置封装: 属性 `Properties` - `Models for *` - `Add...` - `Footprint` - `Browse` 寻找对应的封装
* 走线 `Place` - `Wire` （快捷键: `P` + `W`）
  * `Shift + Space` 切换走线(45°/90°/任意角度/自动走线)
  * `Backspace` 撤回上一步走线
  * `Delete` 删除走线
  * `左键` 改变走线
  * `右键` 退出走线
* 交叉走线中添加结点 `Place - Manual Junction`
* Off Sheet Connector (图中红色双箭头图形>>) `Place` - `Off Sheet Connector` (快捷键: `P` + `C`)
  * 属性中 `NET` 更改名字
  * 属性中 `Style` 更改朝向
* 放置网络标志 Net Label (导线上的棕色标志) `Place` - `Net Label` (快捷键: `P` + `N`)
* 放置文本框 `Place` - `Text Frame` (快捷键: `P` + `F`)
  * 显示边框: 勾选 `Show Border`
  * 填充: 勾选 `Draw Solid`
  * (文字颜色选13的蓝色)
* 元器件文本左下一个点
  * 双击文本打开文本属性 - 不勾选 `Autoposition`
* 原理图网表生成 __EN-C200_RA0_OLED.NET__ `Design` - `Netlist For Project` - `Protel`
  * 生成完成没有提示，注意可能输出在文件夹 `Project Outputs for EN-C200_RA0` 中

## 上传的文件

* 原理图设计文档: `EN-C200_RA0_OLED.SchDoc`
  * 为编辑好的原理图设计文件
* 原理图网表文件: `EN-C200_RA0_OLED.NET`
  * 为通过 `EN-C200_RA0_OLED.SchDoc` 生成的网表文件
