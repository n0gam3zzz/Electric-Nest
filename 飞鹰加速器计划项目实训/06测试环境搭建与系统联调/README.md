# 华为云设备接入操作（板子程序不用动）

## 产品

* 产品名称: SmartLight
* 所属资源空间: DefaultApp_639dze1e （默认选择）
* 协议类型: LWM2M/CoAP
* 数据格式: 二进制码流
* 厂商名称: EN
* 所属行业: 智慧城市-公共服务
* 设备类型: 智能路灯

## 模型定义 - 添加服务

* 服务名称: Light Service

### 属性

* 属性名称: ambientLevel
* 数据类型: int
* 访问权限: 可读 可写
* 步长: 1
* 单位: Lux

### 命令

* 命令名称: SWITCH_LIGHT

#### 参数

* 参数名称: switchLight
* 数据类型: string
* 长度: 3
* 枚举值: ON,OFF

## 插件开发 - 图形化开发

* 新增好消息和字段后，添加 属性 ambientLevel，添加 命令 SWITCH_LIGHT
* 将自动连接：SmartLightInfo→ambientLevel - LightService，SWITCH_LIGHT→switchLight - SWITCH_LIGHT

### 新增消息1

* 消息名: SmartLightInfo
* 消息类型: 数据上报

#### 添加字段

* 字段名称: ambientLevel
* 数据类型: int16u
* 默认值: 0x0000

### 新增消息2

* 消息名: SWITCH_LIGHT
* 消息类型: 命令下发

#### 添加字段

* 字段名称: switchLight
* 数据类型: string
* 长度: 3
* 默认值: 0x4F4646

## 在线调试 - 新增测试设备

* 设备类型: 真实设备
* 设备名称: EN-C200-02
* 设备标识码: 868411054538236 （板子上有）

## 注意

* 完成后将设备删除
