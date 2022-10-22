# SCH总成及后处理

## 操作

* 元器件自动编号 `Tools` - `Annotate Schematics...`
  * Order of Processing: 选择 `Across Then Down`
  * 更新编号 `Update Changes List`
  * 接受编号的更改 `Accept Changes(Create CEO)`
  * 执行改变 点击 `Validate VChanges` ，然后点击 `Execute Changes`
* 原理图电气规则检查设置 `Project` - `Project Options`
* 原理图电气规则检查 `Project` - `Compile Document *.SchDoc`
  * 在 `Message` 窗口查看检查结果
* 原理图BOM清单生成 `Reports` - `Bill of Materials`
  * 在 `Export Options` 的 `File Format` 选项中选择 `Microsoft Excel Worksheet (*.xls)`
  * 删除在 `Excel Options` 的 `Template` 选项
  * `Export` 生成BOM文件

## 步骤

* 创建工程 `File` - `New` - `Project` - `PCB Project` 并保存为 `EN-C200_RA0.PrjPCB`
* 右键 `EN-C200_RA0.PrjPCB` - `Add Existing to Project...` 将之前制作的所有PCB进行添加，包括 `EN-C200_RA0_MCU.SchDoc`, `EN-C200_RA0_NB-IoT.SchDoc`, `EN-C200_RA0_OLED.SchDoc`, `EN-C200_RA0_PWR.SchDoc`, `EN-C200_RA0_USB.SchDoc` 5个文件
  * 注意：效果是要打开工程文件 `EN-C200_RA0.PrjPCB` 后，能够看到所有上述5个文件。
* 生成原理图网表 `Design` - `Netlist For Project` - `Protel` ，将在文件夹 `Project Outputs for EN-C200_RA0` 中得到文件 __EN-C200_RA0.NET__
  * !!注意!! 是选择 `Netlist For Project`
* 生成原理图BOM表 得到文件 `EN-C200_RA0.xls`，更改其文件名为 __EN-C200_RA0_BOM.xls__
* 从 课程参考 中下载 【PCB 结构要素图_样例】 __EN-C200_RA0-dfx.rar`__，解压得到 __EN-C200_RA0.dxf__
* 保存后将 `EN-C200_RA0.PrjPCB`, `EN-C200_RA0_MCU.SchDoc`, `EN-C200_RA0_NB-IoT.SchDoc`, `EN-C200_RA0_OLED.SchDoc`, `EN-C200_RA0_PWR.SchDoc`, `EN-C200_RA0_USB.SchDoc` 6个文件打包压缩为 __EN-C200_RA0_SCH.zip__

## 上传的文件

* 原理图设计文件包 `EN-C200_RA0_SCH（*.zip:*.SchDoc,*.PrjPCB）`
  * 为打包好的压缩包，包括 `EN-C200_RA0.PrjPCB`, `EN-C200_RA0_MCU.SchDoc`, `EN-C200_RA0_NB-IoT.SchDoc`, `EN-C200_RA0_OLED.SchDoc`, `EN-C200_RA0_PWR.SchDoc`, `EN-C200_RA0_USB.SchDoc` 6个文件
* 原理图网表文件 `EN-C200_RA0.NET`
  * 为生成的原理图网表
* 原理图BOM `EN-C200_RA0_BOM.xls`
  * 为生成的原理图BOM表
* PCB结构要素图 `EN-C200_RA0.dxf`
  * 从参考文件的压缩包中解压得到
* Checklist（实训）
  * 全部通过即可
* Checklist（实训）
  * 全部通过即可
