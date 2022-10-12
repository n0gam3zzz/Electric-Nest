# Netlist任务练习

## 操作

### DFX分析

* 将 `*.zip` 上传至 `Vayo-DFX 设计执行系统` - `任务` - `开短路分析`
* 上传至 `Vayo-DFX 设计执行系统` - `任务` - `开短路分析`
* 点击 `打开工程` 以打开 `DFX Station`
  * `工具` - `网表检查`

### AD软件输出PCB数据

* ASCII PCB 输出
  * 另存为 `PCB ASCII File(*.pcbdoc)` 即可
* Gerber 光绘文件输出: `File` - `Fabrication Outputs` - `Gerber Files` 得到 `CAMtastic1.CAM` 文件
  * `Layers`: 点击 `Plot Layers` - `All On` (?)
  * `Drill Drawing`
    * `Drill Drawing Plots` - 勾选 `Plot all used layer pairs`
    * `Drill Guide Plots` - 勾选 `Plot all used layer pairs`
* NC 钻孔文件输出: `File` - `Fabrication Outputs` - `NC Drill Files` 得到 `CAMtastic2.CAM` 文件
  * `Format`: 2:5
* IPC-D-356 网表文件输出: `File` - `Assembly Outputs` - `Test Point Files` 得到 `CAMtastic3.CAM` 文件
  * 勾选 `IPC-D-356A`

#### 可能出现的错误

* 输出光绘文件时报错 `The Film is too small for this PCB`
  * 重新设置原点 `Edit` - `Origin` - `Reset`
  * 在输出光绘文件时点击选项 `Advanced` - `Film Size` 增大 `X (Horizontal)` 和 `Y (vertical)` 的值，直接各往后添加了一个 0 就行了

### 修改PCB文档

* `Vayo-DFX 设计执行系统` 分析完成后选择 `打开工程`
* 选择 `DFX报告` 查看问题所在，同时打开 Alitum Designer，选择 `跳转模式` 选择问题进行对应的修改

## 步骤

* 下载 _参考数据一_ `EMIA_HM1521_NETLIST.pcbdoc` 更改文件名为 `EMIA_HM1521_NETLIST_V1.0.pcbdoc`
* 在AD中输出 `EMIA_HM1521_NETLIST_V1.0.pcbdoc` 对应的 Gerber 光绘文件、NC 钻孔文件和 IPC356 网表文件，笔者生成了包括以下30个文件
  * `Assembly Testpoint Report for EMIA_HM1521_NETLIST_V1.0.ipc`
  * `Assembly Testpoint Report for EMIA_HM1521_NETLIST_V1.0.REP`
  * `EMIA_HM1521_NETLIST_V1-macro.APR_LIB`
  * `EMIA_HM1521_NETLIST_V1-RoundHoles.TXT`
  * `EMIA_HM1521_NETLIST_V1-SlotHoles.TXT`
  * `EMIA_HM1521_NETLIST_V1-SquareHoles.TXT`
  * `EMIA_HM1521_NETLIST_V1.0.apr`
  * `EMIA_HM1521_NETLIST_V1.0.DRL`
  * `EMIA_HM1521_NETLIST_V1.0.DRR`
  * `EMIA_HM1521_NETLIST_V1.0.EXTREP`
  * `EMIA_HM1521_NETLIST_V1.0.GBL`
  * `EMIA_HM1521_NETLIST_V1.0.GBO`
  * `EMIA_HM1521_NETLIST_V1.0.GBP`
  * `EMIA_HM1521_NETLIST_V1.0.GBS`
  * `EMIA_HM1521_NETLIST_V1.0.GD1`
  * `EMIA_HM1521_NETLIST_V1.0.GG1`
  * `EMIA_HM1521_NETLIST_V1.0.GKO`
  * `EMIA_HM1521_NETLIST_V1.0.GM13`
  * `EMIA_HM1521_NETLIST_V1.0.GM15`
  * `EMIA_HM1521_NETLIST_V1.0.GM2`
  * `EMIA_HM1521_NETLIST_V1.0.GPB`
  * `EMIA_HM1521_NETLIST_V1.0.GPT`
  * `EMIA_HM1521_NETLIST_V1.0.GTL`
  * `EMIA_HM1521_NETLIST_V1.0.GTO`
  * `EMIA_HM1521_NETLIST_V1.0.GTP`
  * `EMIA_HM1521_NETLIST_V1.0.GTS`
  * `EMIA_HM1521_NETLIST_V1.0.LDP`
  * `EMIA_HM1521_NETLIST_V1.0.REP`
  * `EMIA_HM1521_NETLIST_V1.0.RUL`
  * `Status Report.Txt`
* 将以上30个文件打包成 `EMIA_HM1521_NETLIST_V1.0.zip` 上传至 `Vayo-DFX 设计执行系统` 进行 `开短路分析`
* 分析完成后对PCB工程进行修改
  * 短路的区域将连接两种不同区域的导线 拉短 或 删除
  * 对于开路，找到没有相连的器件或区域使用导线相连
    * C57
* 修改完成后保存为 `PCB ASCII File (PCB ASCII Version 5.0)` 并打包成对应的zip文件上传至 `Vayo-DFX 设计执行系统` 进行 `开短路分析` 直到 __不出现问题__

## 上传的文件

* NETLIST 布局问题处理 PCB `EMIA_HM1521_NETLIST_V1.0.pcbdoc`: 为修改至无问题的PCB文件
* PCB Netlist 检查 `EMIA_HM1521_IPC_V1.0.zip`: 将前者的 `EMIA_HM1521_NETLIST_V1.0.zip` 改名即可
* 上传文件后点击 `生成检查报告`
  * PCB名称: `EMIA_HM1521_IPC` (随便写也没问题吧...不知道了)
  * PCB版本: `1.0`
* 分析完毕没有问题即可提交
