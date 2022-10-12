# 布线DFX检查练习

## 操作

### 网表分析

* 将 `*.zip` 上传至 `Vayo-DFX 设计执行系统` - `任务` - `DFX分析`
* 上传至 `Vayo-DFX 设计执行系统` - `任务` - `DFX分析`
  * 选择规则集名称为 `EDA365`
  * 检查对象为 `布线`

### 修改PCB文档

* `Vayo-DFX 设计执行系统` 分析完成后选择 `打开工程`
* 选择 `DFX报告` 查看问题所在，同时打开 Alitum Designer，选择 `跳转模式` 选择问题进行对应的修改

## 步骤

* 下载 _参考数据一_ `EMIA_HM1521_ONLYLINE.pcbdoc` 更改文件名为 `EMIA_HM1521_ONLYLINE_V1.0.pcbdoc` 并打包成对应的zip文件
* 将 `EMIA_HM1521_ONLYLINE_V1.0.zip` 上传至 `Vayo-DFX 设计执行系统` 进行 `DFX分析`
* 修改完成后保存为 `PCB ASCII File` 并打包成对应的zip文件上传至 `Vayo-DFX 设计执行系统` 进行 `布线` 的 `DFX分析` 直到 __不出现问题__

### 具体修改

* __橙色和黄色警告忽略即可__
* 表层线路
  * 线间距: 调整线的粗细即可 (0.1524mm)
* 布线
  * 表贴器件焊盘上有孔: 将所在的Via删除即可
* 热设计（为橙色警告，忽略即可）
* 丝印
  * 文字压阻焊开窗: 把对应的丝印移开，不要挡住器件即可
* 阻焊（为橙色警告，忽略即可）

## 上传的文件

* DFX 布局问题处理 PCB `EMIA_HM1521_ONLYLINE_V1.0.pcbdoc`: 为修改至无问题的PCB文件
* PCB 布局 DFX 检查 `EMIA_HM1521_ONLYLINE_DFX_V1.0.zip`: 将 `EMIA_HM1521_ONLYPART_V1.0.pcbdoc` 打包成对应的zip文件后改名即可
* 上传文件后点击 `生成检查报告`
  * PCB名称: `EMIA_HM1521_ONLYLINE_DFX`
  * PCB版本: `1.0`
  * 规则集名称: `EDA365`
  * 选择`布线`
* 等待分析完毕没有问题即可提交
