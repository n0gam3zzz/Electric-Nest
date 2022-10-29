# 单板PCB设计

## 操作

* __输出装配图文件__ `File` - `Smart PDF...`
  * `Choose Export Target`
    * 选择 `Current Document`
  * `Export a Bill of Materials`
    * 不勾选 `Export a Bill of Materials` 不生成BOM表
  * `PCB Printout Settings`
    * 右键 `Create Assembly Drawings`
    * 选择 `Area to Print` - `Specific Area`: 5190mil 2320mil 10136mil 4942mil
  * `Additional PDF Settings`
    * 选择 `PCB` - `Monochrome` (黑白)
  * `Final Steps`
    * 不勾选 `Save Settings to Output Job document`
  * 输出得到文件 `*.pdf`
* __光绘文件(Gerber)输出__ `File` - `Fabrication Outputs` - `Gerber Files`
  * `Layers`: 点击 `Plot Layers` - `All On`
  * `Drill Drawing`
    * `Drill Drawing Plots` - 勾选 `Plot all used layer pairs`
    * `Drill Guide Plots` - 勾选 `Plot all used layer pairs`
  * 输出文件夹中生成了以下24个文件
    * `EN-C200_RA2_DFX-macro.APR_LIB`
    * `EN-C200_RA2_DFX.apr`
    * `EN-C200_RA2_DFX.EXTREP`
    * `EN-C200_RA2_DFX.GBL`
    * `EN-C200_RA2_DFX.GBO`
    * `EN-C200_RA2_DFX.GBP`
    * `EN-C200_RA2_DFX.GBS`
    * `EN-C200_RA2_DFX.GD1`
    * `EN-C200_RA2_DFX.GG1`
    * `EN-C200_RA2_DFX.GKO`
    * `EN-C200_RA2_DFX.GM1`
    * `EN-C200_RA2_DFX.GM12`
    * `EN-C200_RA2_DFX.GM14`
    * `EN-C200_RA2_DFX.GM20`
    * `EN-C200_RA2_DFX.GM255`
    * `EN-C200_RA2_DFX.GPB`
    * `EN-C200_RA2_DFX.GPT`
    * `EN-C200_RA2_DFX.GTL`
    * `EN-C200_RA2_DFX.GTO`
    * `EN-C200_RA2_DFX.GTP`
    * `EN-C200_RA2_DFX.GTS`
    * `EN-C200_RA2_DFX.REP`
    * `EN-C200_RA2_DFX.RUL`
    * `Status Report.Txt`
* __钻孔文件(NC)输出__ `File` - `Fabrication Outputs` - `NC Drill Files`
  * 输出文件夹中生成了以下6个文件
    * `EN-C200_RA2_DFX-RoundHoles.TXT`
    * `EN-C200_RA2_DFX-SlotHoles.TXT`
    * `EN-C200_RA2_DFX.DRL`
    * `EN-C200_RA2_DFX.DRR`
    * `EN-C200_RA2_DFX.LDP`
    * `Status Report.Txt`
* __IPC网表输出__ `File` - `Fabrication Outputs` - `Test Point Report`
  * 勾选 `IPC-D-356A`
  * 输出文件夹中生成了以下3个文件
    * `Fabrication Testpoint Report for EN-C200_RA2_DFX.ipc`
    * `Fabrication Testpoint Report for EN-C200_RA2_DFX.REP`
    * `Status Report.Txt`
* __贴片坐标文件输出__
  * `File` - `Assembly Outputs` - `Generate pick and place files`
  * 输出文件夹中生成了以下2个文件
    * `Pick Place for EN-C200_RA2_DFX.txt`
    * `Status Report.Txt`

## 步骤

* （不需要）下载 项目文档 - 【原理图设计文件包】 - `EN-C200_RA0_SCH.zip` 并解压
* （不需要）下载 项目文档 - 【PCB结构要素图】 - `EN-C200_RA0.dxf`
* 下载 课程参考 - 【PCB设计实例】 - `EN-C200_RA2_DFX.pcbdoc`
* 对文件 `EN-C200_RA2_DFX.pcbdoc` 的原点进行重置 `Edit` - `Origin` - `Reset` 然后保存为 PCB ASCII Version
* 对文件 `EN-C200_RA2_DFX.pcbdoc` 进行①装配图文件输出、②光绘文件输出、③钻孔文件输出、④IPC网表输出和⑤贴片坐标文件输出

### 打包文件

* 文件夹 `ASM` 包括装配图文件
  * `EN-C200_RA2_DFX.pdf`
* 文件夹 `CAM` 包括输出文件夹的所有文件，共32个文件
  * `EN-C200_RA2_DFX-macro.APR_LIB`
  * `EN-C200_RA2_DFX-RoundHoles.TXT`
  * `EN-C200_RA2_DFX-SlotHoles.TXT`
  * `EN-C200_RA2_DFX.apr`
  * `EN-C200_RA2_DFX.DRL`
  * `EN-C200_RA2_DFX.DRR`
  * `EN-C200_RA2_DFX.EXTREP`
  * `EN-C200_RA2_DFX.GBL`
  * `EN-C200_RA2_DFX.GBO`
  * `EN-C200_RA2_DFX.GBP`
  * `EN-C200_RA2_DFX.GBS`
  * `EN-C200_RA2_DFX.GD1`
  * `EN-C200_RA2_DFX.GG1`
  * `EN-C200_RA2_DFX.GKO`
  * `EN-C200_RA2_DFX.GM1`
  * `EN-C200_RA2_DFX.GM12`
  * `EN-C200_RA2_DFX.GM14`
  * `EN-C200_RA2_DFX.GM20`
  * `EN-C200_RA2_DFX.GM255`
  * `EN-C200_RA2_DFX.GPB`
  * `EN-C200_RA2_DFX.GPT`
  * `EN-C200_RA2_DFX.GTL`
  * `EN-C200_RA2_DFX.GTO`
  * `EN-C200_RA2_DFX.GTP`
  * `EN-C200_RA2_DFX.GTS`
  * `EN-C200_RA2_DFX.LDP`
  * `EN-C200_RA2_DFX.REP`
  * `EN-C200_RA2_DFX.RUL`
  * `Fabrication Testpoint Report for EN-C200_RA2_DFX.ipc`
  * `Fabrication Testpoint Report for EN-C200_RA2_DFX.REP`
  * `Pick Place for EN-C200_RA2_DFX.txt`
  * `Status Report.Txt`
* 文件夹 `SMT` 包括输出文件夹中的其中3个文件
  * `EN-C200_RA2_DFX.GBP`
  * `EN-C200_RA2_DFX.GTP`
  * `Pick Place for EN-C200_RA2_DFX.txt`

## 上传的文件

* CAM文件包 `EN-C200_RA0_CAM.zip`: 将文件夹 `CAM` 压缩成zip文件后改名即可
* ASM文件包 `EN-C200_RA0_ASM.zip`: 将文件夹 `ASM` 压缩成zip文件后改名即可
* SMT文件包 `EN-C200_RA0_SMT.zip`: 将文件夹 `SMT` 压缩成zip文件后改名即可
* PCB加工工艺要求 `EN-C200_RA0 PCB加工工艺要求.xls`: 在右侧点击下载按钮将文件改名即可
* PCB DFX 检查 `EN-C200_RA0_DFX_V1.0.zip`: 将 `EN-C200_RA2_DFX.pcbdoc` 打包成对应的zip文件后改名即可
  * 点击 `生成检查报告`
    * PCB名称: `EN-C200_RA0_DFX`
    * PCB版本: `1.0`
    * 规则集名称: `EDA365`
    * 选择`全部`
* PCB工艺设计Checklist `EN-C200_RA0 单板PCB工艺设计Checklist.xlsx`: 在右侧点击下载按钮将文件改名即可
* 分析完毕即可提交
