# 2.4 PCB设计快速入门

* Updated in 2022/10/02 10:29

## PCB设计流程

* 板框绘制
  * 创建PCB文件
  * 绘制单板板框
  * 绘制结构特殊区域及倒角拼板
  * 放置固定器件
* 网表导入
  * 设置库路径
  * 导入网表
* 设计规划
  * 梳理功能要求
  * 确认设计要求
* 布局
  * 模块布局
  * 整体布局
  * 确定层叠
  * 规则设置
  * 整版扇出
* 布线
  * 关键信号线
  * 整板布线
  * ICT测试点增加
  * 电源地处理
  * 等长线处理
  * 布线优化
* 丝印调整
  * 设置字符格式
  * 调整器件字符
  * 添加特殊字符
  * 添加特殊丝印
* 生产文件输出
  * ASM文件输出
  * Gerber文件输出
  * 钻孔文件输出
  * IPC网表文件输出
  * 贴片坐标文件输出

## 操作

### `EN-C200-OPT_RA0.PcbDoc`/`PCB1.PcbDoc`

* 导入结构图
  * `File` - `Import...` - 选择 `*.dxf` 导入
  * 导入设置 `Scale`: `mm`
  * 图层设置 `Layer Mappings` 设置 `OUTLINE` 在 `PCB Layer` 为 `Mechanical 1`
* 设置原点 `Edit` - `Origin` - `Set`
* 格点设置 `Design` - `Board Options`
  * `Component Grid`: 5mil
  * 勾选 `Snap To Board Out`
  * `Visible Grid` - `Markers`: `Dots`
* 走线 - 倒角
  * 选择图层 `Mechanical 1` 进行操作
  * `Place` - `Line` 选择粗度为5mil
  * 指定XY位移 `Edit` - `Move` - `Move Selection by X, Y...`
* _切换显示单层图层或显示全部图层_ `Shift` + `S`
* 选择图层上的所有部分 `Edit` - `Select` - `All on Layer`
* 定义板框 `Design` - `Board Shape` - `Define from selected objects`
* 粘贴属性 `Edit` - `Paste Special...`
* 导入网表 `Design` - `Import Changes From *.PrjPcb`
  * 检查变化 `Validate Changes`
  * 执行变化 `Execute Changes`
* 寻找类似的部件 选择一个器件右键 `Find Similar Objects...`
* 锁定部件 选中器件双击 - 勾选 `Locked`
* 移动选项 选中器件 `M`
  * 翻转 `Flip Selection`
* 查找器件在对应文件中的位置 `Tools` - `Cross Probe` 选择器件 `Ctrl` + `左键单击`
* 取消单独查看 `Shift` + `C` 当不能选择其余器件时
* 对齐 选中一些器件 `A` 弹出对齐菜单
* 层叠设置 `Design` - `Layer Stack Manager`
  * `Core`: 设置板厚 62.992mil 和介电常数 4.2
* 规则设置 `Design` - `Rules...` _(13:31~21:15)_
* 规则检查 `Tools` - `Design Rule Check...`
* 布线 `Place` - `Interactive Routing`
  * 自动打孔 `2`
* 放置孔 `Place` - `Via`
* 绘制多边形 - 铜皮 `Place` - `Polygon Pour`
  * 调整 选中 `M` - `Polygon Vertices`
* 对齐
  * 向右对齐 `Ctrl` + `Shift` + `R`
  * 向左对齐 `Ctrl` + `Shift` + `L`
  * 向顶部对齐 `Ctrl` + `Shift` + `T`
  * 向底部对齐 `Ctrl` + `Shift` + `B`
  * 水平分布 `Ctrl` + `Shift` + `H`
  * 垂直分布 `Ctrl` + `Shift` + `V`
* 调整丝印
  * `L` 打开图层菜单 点击`All Layers Off`
  * 顶层丝印：勾选`Top Solder`、`Top Overlay`、`Mechanical 1`
  * 顶层丝印：勾选`Bottom Solder`、`Bottom Overlay`、`Mechanical 1`
* 输出装配图文件 __PCB1.pdf__/__EN-C200-OPT_RA0.pdf__ `File` - `Smart PDF...`
  * 选择 `Current Document`
  * 不勾选 不生成BOM表 `Export a Bill of Materials`
  * 选择 `Bottom Overlay` 右键 `Create Assembly Drawings`
  * 选择 `Top Layer` 、 `Multi-Layer` 、 `Mechanical 2` 删除
  * 选择 `Top Overlay` 右键 `Insert Layer` 插入 `Top Solder` 层
  * 选择 `Bottom Layer` 、 `Multi-Layer` 、 `Mechanical 2` 删除
  * 选择 `Bottom Overlay` 右键 `Insert Layer` 插入 `Bottom Solder` 层
  * 在 `Bottom Assembly Drawing` 勾选 `Mirror`
  * 选择 `PCB` - `Monochrome`(黑白)
  * 不勾选 `Save Settings to Output Job document`
* 光绘文件(Gerber)输出 __CAMtastic1.Cam__ _(3:47)_ `File` - `Fabrication Outputs` - `Gerber Files`
  * `Layers`: 点击 `Plot Layers` - `All On` 然后取消勾选后四个图层
  * `Drill Drawing`
    * `Drill Drawing Plots` - 勾选 `Plot all used layer pairs`
    * `Drill Guide Plots` - 勾选 `Plot all used layer pairs`
* 钻孔文件(NC)输出 __CAMtastic2.Cam__ `File` - `Fabrication Outputs` - `NC Drill Files`
  * `Format`: 2:4
* IPC网表输出 __CAMtastic3.Cam__ `File` - `Fabrication Outputs` - `Test Point Report`
  * 勾选 `IPC-D-356A`
* 贴片坐标文件输出 __Pick Place for PCB1.TXT__/__Pick Place for EN-C200-OPT_RA0.TXT__
  * `File` - `Assembly Outputs` - `Generate pick and place files`

### 打包文件

* 文件夹 `ASM` 装配图文件
  * `PCB1.pdf`
* 文件夹 `CAM` 包括输出文件夹中的全部内容
  * `Fabrication Testpoint Report for PCB1.ipc`
  * `Fabrication Testpoint Report for PCB1.REP`
  * `PCB1-macro.APR_LIB`
  * `PCB1.apr`
  * `PCB1.DRL`
  * `PCB1.DRR`
  * `PCB1.EXTREP`
  * `PCB1.GBL`
  * `PCB1.GBO`
  * `PCB1.GBP`
  * `PCB1.GBS`
  * `PCB1.GD1`
  * `PCB1.GG1`
  * `PCB1.GM1`
  * `PCB1.GTL`
  * `PCB1.GTO`
  * `PCB1.GTP`
  * `PCB1.GTS`
  * `PCB1.LDP`
  * `PCB1.REP`
  * `PCB1.RUL`
  * `PCB1.TXT`
  * `Pick Place for PCB1.txt`
  * `Status Report.Txt`
* 文件夹 `SMT` 输出文件夹中的
  * `PCB1.GBP`
  * `PCB1.GTP`
  * `Pick Place for PCB1.txt`

## 上传的文件

* 单板PCB设计文件 `EN-C200-OPT_RA0.PcbDoc`
  * 即 `PCB1.PcbDoc`
* 单板CAM包文件 `EN-C200-OPT_RA0_CAM（*.rar/*.zip）`
  * 将文件夹 CAM 打包成压缩包
* 单板ASM包文件 `EN-C200-OPT_RA0_ASM（*.rar/*.zip）`
  * 将文件夹 ASM 打包成压缩包
* 单板SMT包文件 `EN-C200-OPT_RA0_SMT（*.rar/*.zip）`
  * 将文件夹 SMT 打包成压缩包
* PCB加工工艺要求 `EN-C200-OPT_RA0 PCB加工工艺要求.xls`
  * 从输出文档中下载，即 `T3303_xxx单板PCB加工工艺要求_模板 V1.0.xls`
* PCB DFX 检查 `EN-C200-OPT_RA0_DFX_V1.0（*.zip/*.var）`
* PCB Netlist 检查 `EN-C200-OPT_RA0_IPC_V1.0.zip`
* 光传感器扣板项目PCB设计checklist `全部通过即可`
