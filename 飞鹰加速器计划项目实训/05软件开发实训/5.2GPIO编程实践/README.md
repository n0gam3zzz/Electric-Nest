# GPIO编程实践

## 1 操作

* 工程文件中（ _...\*\MDK-ARM_ 中选择文件 `*.uvprojx` 用 Keil uVision 软件打开）
  * 在 _Application\User_ 的 main.c 中的 `/* USER CODE BRGIN */` 和 `/* USER CODE END */` 之间编写自己的代码

### 1.1 函数

```c
void HAL_GPIO_WritePin(GPIO_TypeDef* GPIOx, uint16_t GPIO_Pin, GPIO_PinState PinState);
```

* 写入管脚
  * GPIOx: GPIOx，其中 x 可以是(A~H)，用于选择STM32L4系列的GPIO外围
  * GPIO_Pin: 设置GPIO管脚的位号
  * PinState: 为枚举常量——高电平 GPIO_PIN_SET、低电平 GPIO_PIN_RESET

```c
__weak void HAL_Delay(uint32_t Delay);
```

* 设置延迟时间
  * Delay: 延迟时间(ms)

### 1.2 通过 STM-32 ST-LINK Utility 进行硬件烧制与测试

* 首先要连接上单板
* 在 STM-32 ST-LINK Utility中点击 `Target` - `Connect`，与单板建立连接
* 点击 `File` - `Open file...` 打开需要下载的 `*.hex` 文件
* 点击 `Target` - `Program & Verify...` 点击 `Start` 即可开始烧制，并得到结果

### 1.3 通过 Keil uVision 进行硬件烧制与测试

* 首先要连接上单板
* 在 Keil uVision 中编程好并编译好后，打开 `Project` - `Options for Target '*'...`
* 进入 `Debug` 选项卡，选择 `Use ST-Link Debugger`，点击右方的 `Settings` 打开
* 在 `Debug` 选项卡中，Unit中应显示 `ST-LINK/V2` ；进入 `Flash Download` ，勾选 `Reset and Run`，这样在下载之后就可以直接运行查看效果
* 点击确定关闭两个窗口，点击 `下载` 即可开始烧制，并得到结果

## 2 步骤

* 打开 `STM32CubeMX` - 新建工程 - `Part Number Search` 中搜索 `STM32L431RC` - 选择第二个(Package: LQFP64)双击
* `Pinout` 选项卡
  * `RCC`：将 High Speed Clock (HSE) 和 Low Speed Clock (LSE) 设置为 `Crystal/Ceramic Resonator`
  * `RTC`：勾选 Activate Clock Source
  * 右方配置图中，设置 PC13 管脚为 GPIO_Output
* `Clock Configuration` 选项卡 （设置见图）

![1](https://images2.imgbox.com/32/6e/ZmtxQs7H_o.png?download=true)

* 点击 `Project` - `Settings`
  * Project
    * `Project Name`: LED_Link
    * `Project Location`: (选择一个路径)
    * `Toolchain/IDE`: MDK-ARM V5
  * Code Generator
    * 勾选 `Generate peripheral initialization as a pair of '.c/.h' files per peripheral`
* 设置好后，点击 `Project` - `Generate Code`
* 在 _...\LED\_Link\MDK-ARM_ 中选择文件 `LED_Link.uvprojx` 用 Keil uVision 软件打开
  * 编译
  * 编译完成后，在 _Drivers/STM32L4xx\_HAL\_Driver_ 中，展开 `stm32l4xx_hal_gpio.c` 找到 `stm32l4xx_hal_gpio.h`，拖到最后找到接口函数
  * 将 `HAL_GPIO_WritePin` 函数复制到 `main.c` 中的 `/* USER CODE BEGIN 3 */` 之后
  * 编写代码如下

```c
  /* USER CODE BEGIN 3 */
  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_13, GPIO_PIN_SET);
```

* !!!编译成功后保存，将 _LED\_Link_ 文件夹下的 __除了__ _Drivers_ 文件夹以外的文件和文件夹打包成zip压缩包，更改文件名为 `EN-C200 GPIO编程实践源代码.zip`
* 同样是上面修改代码的位置，编写代码如下

```c
  /* USER CODE BEGIN 3 */
  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_13, GPIO_PIN_SET);
  HAL_Delay(500);
  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_13, GPIO_PIN_RESET);
  HAL_Delay(500);
```

* !!!编译成功后保存，将 _LED\_Link_ 文件夹下的 __除了__ _Drivers_ 文件夹以外的文件和文件夹打包成zip压缩包，更改文件名为 `EN-C200 GPIO创新实验源代码.zip`

## 3 可能出现的错误

### 3.1  Keil软件编译报错 `LED_Link\LED_Link.sct(7): error: L6236E: No section matches selector - no section to be FIRST/LAST.`

* 右键 _Application\User_ 点击 `Manage Project Items...` - `Add Files...`
* 找到文件 `startup_stm32l431xx.s` 添加即可

## 4 上传的文件

* 编程实践源码: `EN-C200 GPIO编程实践源代码.zip`
* 创新实验源码: `EN-C200 GPIO创新实验源代码.zip`
* 要求代码没有语法错误，编译没有出错
