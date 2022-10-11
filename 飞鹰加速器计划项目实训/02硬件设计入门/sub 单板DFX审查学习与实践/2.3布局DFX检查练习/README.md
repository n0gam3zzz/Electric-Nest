# 布局DFX检查练习

## 操作

### DFX分析

* 将 `*.zip` 上传至 `Vayo-DFX 设计执行系统` - `任务` - `DFX分析`
* 上传至 `Vayo-DFX 设计执行系统` - `任务` - `DFX分析`
  * 选择规则集名称为 `EDA365`
  * 检查对象为 `布局`

### AD软件输出PCB数据

* ASCII PCB 输出
  * 另存为 `*.psbdoc` 为PCB ASCII文件即可
* Gerber 输出
  * `File` - `Fabrication Outputs` - `Gerber Files` 得到 `CAMtastic1.CAM` 文件
* NC 输出
  * `File` - `Fabrication Outputs` - `NC Drill Files` 得到 `CAMtastic2.CAM` 文件
* IPC-D-356 输出
  * `File` - `Assembly Outputs` - `Test Point Files` 得到 `CAMtastic3.CAM` 文件

### 修改PCB文档

* `Vayo-DFX 设计执行系统` 分析完成后选择 `打开工程`
* 选择 `DFX报告` 查看问题所在，同时打开 Alitum Designer，选择 `跳转模式` 选择问题进行对应的修改

## 步骤

* 下载 _参考数据一_ `EMIA_HM1521_ONLYPART.pcbdoc` 更改文件名为 `EMIA_HM1521_ONLYPART_V1.0.pcbdoc` 并打包成对应的zip文件
* 将 `EMIA_HM1521_ONLYPART_V1.0.zip` 上传至 `Vayo-DFX 设计执行系统` 进行 `DFX分析`
* 分析完成后对PCB工程进行修改
  * 间距过小的拉大即可
  * 两个光学点，一个放在左上，一个放在左下即可
* 修改完成后保存为 `PCB ASCII File` 并打包成对应的zip文件上传至 `Vayo-DFX 设计执行系统` 进行 `DFX分析` 直到 __不出现问题__

## 上传的文件

* DFX 布局问题处理 PCB `EMIA_HM1521_ONLYPART_V1.0.pcbdoc`: 为修改至无问题的PCB文件
* PCB 布局 DFX 检查 `EMIA_HM1521_ONLYPART_DFX_V1.0.zip`: 将 `EMIA_HM1521_ONLYPART_V1.0.pcbdoc` 打包成对应的zip文件后改名即可
* 点击检查
  * PCB名称: `EMIA_HM1521_ONLYPART_DFX`
  * PCB版本: `1.0`
  * 规则集名称: `EDA365`
  * 选择`布局`
