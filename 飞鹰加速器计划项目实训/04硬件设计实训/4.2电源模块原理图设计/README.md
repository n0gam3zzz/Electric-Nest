# 电源模块原理图设计

## 操作

* 旋转元器件
  * 选中元器件且没有放置时 `X` 可以水平翻转
  * 选中元器件且没有放置时 `Y` 可以垂直翻转
  * 选中元器件且没有放置时 `Space` 可以逆时针旋转

## 步骤

### 下载文件

* 使用 [上一个任务](https://github.com/n0gam3zzz/Electric-Nest/tree/main/飞鹰加速器计划项目实训/04硬件设计实训/4.1MCU小系统原理图设计) 课程参考 - 【EN-C200 AD 元器件库】 - `EN-C200_RA2_ADlib.rar` 解压缩得到 `EN-C200_RA0.PcbLib` 和 `EN-C200_RA0.SchLib`
* 下载 课程参考 - 【原理图设计样例】 - `电源电路原理图设计样例.pdf`
  * __!!对照该文件进行原理图设计!!__

### 创建工程文件 `EN-C200_RA0.PrjPCB`

* 创建工程 `File` - `New` - `Project` - `PCB Project` 并保存为 `EN-C200_RA0.PrjPCB`
* 右键 `EN-C200_RA0.PrjPCB` - `Add Existing to Project...` 将之前解压缩得到的 `EN-C200_RA0.PcbLib` 和 `EN-C200_RA0.SchLib` 添加
* 右键 `EN-C200_RA0.PrjPCB` - `Add new to Project` - `Schematic` 并保存为 `EN-C200_RA0_PWR.SchDoc`

### `EN-C200_RA0_PWR.SchDoc`

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
* 原理图网表生成 __EN-C200_RA0_MCU.NET__ `Design` - `Netlist For Project` - `Protel`
  * 生成完成没有提示，注意可能输出在文件夹 `Project Outputs for EN-C200_RA0` 中

#### 放置元器件

* __!!注意修改元器件的Designator和Comment属性!!__
* `A03401` 1个
  * Designator: Q2
  * Comment: AO3401
  * Footprint: SOT23
* `BX0034` 1个
  * Designator: J15
  * Comment: Battery Holder No. 7th
  * Footprint: BX0034
* `CAP NP` 共11个
  * Designator: (C1 左上角1个; C2 ~ C4, C76, C77 右上角6个; C8, C70 左2个; C7, C9 中2个)
  * Comment: 22uF(C1, C2, C4, C8, C9, C70, C76, C77); 0.1uF(C3, C5); 5.6pF(C7)
  * Footprint: SC0805(22uF), SC0603(0.1uF和5.6uF)
* `CON10A` 1个
  * Designator: J24
  * Comment: 2x5 2.54mm Male
  * Footprint: SIP-2X5P-100
* `DIODE` 共2个
  * Designator: D1, D5
  * Comment: SM340A
  * Footprint: SD1714
* `HEADER3` 1个
  * Designator: J25
  * Comment: SIP3-2.54/NC
  * Footprint: SIP-3P
* `LED` 3个
  * Designator: LED1, LED2(左上2个); LED3(右下1个)
  * Comment: LTST-C191KRKT(LED1, LED3); LTST-C191KGKT(LED2)
  * Footprint: HSD0603-LED
* `MPF6661` 1个
  * Designator: Q1
  * Comment: AO3400
  * Footprint: SOT23
* `RESISTOR` 共11个
  * Designator: R1, R2(左上2个); R4, R5(中间2个); R58, R59(左下2个); R3, R9, R53, R35, R36(右下5个)
  * Comment: 4.7K(R1, R2, R9); 1K(R3, R36, R58); 249K(R4); 54.9K(R5); 10K(R35); 0/NC(R53); 100K(R59)
  * Footprint: SR0603
* `RT8059` 1个
  * Designator: U2
  * Comment: RT8059GJ5
  * Footprint: SOT23-5
* `SW_PUSH6` 1个
  * Designator: S1
  * Comment: K8-8585D-L2
  * Footprint: SW2X3-100
* `TOROID IRON` 2个
  * Designator: L1, L2
  * Comment: 10uH(L1); 2.2uH(L2)
  * Footprint: SPL0505B(L1); SL1008(L2)
* `TP` 4个
  * Designator: TP1, TP2, TP3, TP7
  * Comment: NC
  * Footprint: TP32-SMD
* `TP5400` 1个
  * Designator: U1
  * Comment: TP5400
  * Footprint: SOP8-50-150B

## 上传的文件

* 原理图设计文档: `EN-C200_RA0_PWR.SchDoc`
  * 为编辑好的原理图设计文件
* 原理图网表文件: `EN-C200_RA0_PWR.NET`
  * 为通过 `EN-C200_RA0_PWR.SchDoc` 生成的网表文件
