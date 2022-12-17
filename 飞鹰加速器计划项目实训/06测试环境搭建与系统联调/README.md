# 1 华为云设备接入操作（板子程序不用动）

## 1.1 产品创建

* 产品名称: SmartLight
* 所属资源空间: DefaultApp_639dze1e （默认选择）
* 协议类型: LWM2M/CoAP
* 数据格式: 二进制码流
* 厂商名称: EN
* 所属行业: 智慧城市-公共服务
* 设备类型: 智能路灯

## 1.2 模型定义 - 添加服务

* 服务名称: Light Service
* 属性
  * 属性名称: ambientLevel
  * 数据类型: int
  * 访问权限: 可读 可写
  * 步长: 1
  * 单位: Lux
* 命令
  * 命令名称: SWITCH_LIGHT
  * 参数
    * 参数名称: switchLight
    * 数据类型: string
    * 长度: 3
    * 枚举值: ON,OFF

## 1.3 插件开发 - 图形化开发

* 新增好消息和字段后，添加 属性 ambientLevel，添加 命令 SWITCH_LIGHT
* 将自动连接：SmartLightInfo→ambientLevel - LightService，SWITCH_LIGHT→switchLight - SWITCH_LIGHT

### 1.3.1 新增消息1

* 消息名: SmartLightInfo
* 消息类型: 数据上报
* 添加字段
  * 字段名称: ambientLevel
  * 数据类型: int16u
  * 默认值: 0x0000

### 1.3.2 新增消息2

* 消息名: SWITCH_LIGHT
* 消息类型: 命令下发
* 添加字段
  * 字段名称: switchLight
  * 数据类型: string
  * 长度: 3
  * 默认值: 0x4F4646

## 1.4 在线调试 - 新增测试设备

* 设备类型: 真实设备
* 设备名称: EN-C200-02
* 设备标识码: 868411054538236 （板子上有）
* (X)成功接入设备后信息
  * 固件版本: Quectel@Hi15RM1-HLB_V1.0@BC35GJCR01A04_ONT,V150R100C20B300SP7,V150R100C20B300SP7@5,8,3

## 2 在线调试操作

* 进入调试：在 设备列表 中点击“更多”进入“调试”
* 按下板子的重启按钮，提示按 KEY1 后按下 KEY1 即可测得光强并上传得到数据
* 在调试界面中的命令下发中选择命令（ON/OFF）即可下发命令，成功下发命令后板子上的LED灯将亮/灭。

## 3 (X)注意

* 完成后将设备删除
