# MCU小系统原理图设计

## 操作

* 旋转元器件
  * 选中元器件且没有放置时 `X` 可以水平翻转
  * 选中元器件且没有放置时 `Y` 可以垂直翻转
  * 选中元器件且没有放置时 `Space` 可以逆时针旋转

## 步骤

### 下载文件

* 下载 课程参考 - 【EN-C200 AD 元器件库】 - `EN-C200_RA2_ADlib.rar`
  * 解压缩得到 `EN-C200_RA0.PcbLib` 和 `EN-C200_RA0.SchLib`
* 下载 课程参考 - 【原理图设计样例】 - `EN-C200_MCU电路原理图设计样例.pdf`
  * __对照该文件进行原理图设计__

### 创建工程文件 `EN-C200_RA0.PrjPCB`

* 创建工程 `File` - `New` - `Project` - `PCB Project` 并保存为 `EN-C200_RA0.PrjPCB`
* 右键 `EN-C200_RA0.PrjPCB` - `Add Existing to Project...` 将之前解压缩得到的 `EN-C200_RA0.PcbLib` 和 `EN-C200_RA0.SchLib` 添加
* 右键 `EN-C200_RA0.PrjPCB` - `Add new to Project` - `Schematic` 并保存为 `EN-C200_RA0_MCU.SchDoc`

### `EN-C200_RA0_MCU.SchDoc`

* 查看库: `View` - `Workspace Panels` - `System` - `Libraries`
* 只查看导入的库: `Libraries` 窗口 - `Libraries...` - `Installed` 选项卡 - 全部不勾选
* 放置原理图符号: `Place` - `Part...`, 点击 `OK` 放置
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
* Net Label 网络标志(导线上的棕色标志) `Place` - `Net Label` (快捷键: `P` + `N`)
* 原理图网表生成 __EN-C200_RA0_MCU.NET__ `Design` - `Netlist For Project` - `Protel`
  * 生成完成没有提示，注意可能输出在文件夹 `Project Outputs for EN-C200_RA0` 中

#### 放置元器件

* `CAP NP` 共36个
  * Designator: (C11, C12右上角2个; C13, C14, C17, C19左上角4个; C15, C16, C18, C20, C21, C68, C69主芯片两侧7个; C22~C26左下角5个; C49~C60, C62~C67右下角18个)
  * Comment: 0.1uF(C11, C15, C16, C18, C20, C21, C23~C26), 22uF(C12), 2.7pF(C13, C14), 20pF(C17, C19), 33pF(C49~C60, C62~C67), 0.01uF(C22)
* `CON10A` 共2个，其一水平翻转
  * Designator: J3, J6
  * Comment: 2x5 2.54mm Male(J3), 2x5 2.54mm Male DC3(J6)
* `CRYSTAL2P` 为原理图中左上角1个
  * Designator: Y1
  * Comment: 32.768KHz
* `CRYSTAL4P` 为原理图中左上角1个
  * Designator: Y2
  * Comment: 8MHz
* `HEADER8` 为原理图中下方共2个，其一水平翻转
  * Designator: J7, J8
  * Comment: SIP8-2.54mm Female
* `LED` 为原理土中左上角1个
  * Designator: LED4
  * Comment: LTST-C191KGKT
* `PUSH-KEY` 为原理图左下角5个
  * Designator: (S2~S6)
  * Comment: SKQMASE010
* `RESISTOR` 共6个
  * Designator: (R28, R10主芯片左上角1个右下角1个; R12~R15左下角4个)
  * Comment: 4.7K(R28), 100K(R10), 10K(R12~R15)
* `STM32L431Rx` 主芯片，共1个，注意要水平翻转
  * Desifnator: U3
* `TP`共9个
  * Designator: TP42~TP50
  * Comment: NC

## 上传的文件

* 原理图设计文档: `EN-C200_RA0_MCU.SchDoc`
  * 为编辑好的原理图设计文件
* 原理图网表文件: `EN-C200_RA0_MCU.NET`
  * 为通过 `EN-C200_RA0_MCU.SchDoc` 生成的网表文件
