# 按键中断编程实践

[物联网终端软件实训(2)——按键中断编程实践 - 物联网技术 - EDA365电子论坛网](https://www.eda365.com/thread-223668-1-1.html)

## 1 操作

* 工程文件中（ _...\*\MDK-ARM_ 中选择文件 `*.uvprojx` 用 Keil uVision 软件打开）
  * 在 _Application\User_ 的 main.c 中的 `/* USER CODE BRGIN */` 和 `/* USER CODE END */` 之间编写自己的代码

### 1.1 函数

```c
void HAL_GPIO_TogglePin(GPIO_TypeDef* GPIOx, uint16_t GPIO_Pin)
```

* 切换指定的GPIO接口
  * GPIOx: GPIOx，其中 x 可以是(A~H)，用于选择STM32L4系列的GPIO外围
  * GPIO_Pin: 设置GPIO管脚的位号

### 1.2 通过 STM-32 ST-LINK Utility 进行硬件烧制与测试

* 首先要连接上单板
* 在 STM-32 ST-LINK Utility中点击 `Target` - `Connect`，与单板建立连接
* 点击 `File` - `Open file...` 打开需要下载的 `*.hex` 文件
* 点击 `Target` - `Program & Verify...` 点击 `Start` 即可开始烧制，并得到结果

### 1.3 通过 Keil uVision 进行硬件烧制与测试

* 首先要连接上单板
* 在 Keil uVision 中编程好并编译好后，打开 `Project` - `Options for Target '*'...`
* 进入 `Debug` 选项卡，选择 `Use ST-Link Debugger`，点击右方的 `Settings` 打开
* 在 `Debug` 选项卡中，Unit中应显示 `ST-LINK/V2` ；进入 `Flash Download` ，勾选 `Reset and Run`，点击 `Add` 选择 `STM32L4xx 256 KB Flash` 添加。这样在下载之后就可以直接运行查看效果
* 点击确定关闭两个窗口，点击 `下载` 即可开始烧制，并得到结果

## 2 步骤

### 2.1 配置（`STM32CubeMX`）

* 打开 `STM32CubeMX` - 新建工程 - `Part Number Search` 中搜索 `STM32L431RC` - 选择第二个(Package: LQFP64)双击
* `Pinout` 选项卡
  * `RCC`：将 High Speed Clock (HSE) 和 Low Speed Clock (LSE) 设置为 `Crystal/Ceramic Resonator`
  * `RTC`：勾选 Activate Clock Source
  * 右方配置图中，设置 PC13 管脚为 GPIO_Output，设置 PC0 管脚为 GPIO_EXIT0
* `Clock Configuration` 选项卡 （设置见图）

![1](https://images2.imgbox.com/32/6e/ZmtxQs7H_o.png?download=true)

* `Configuration` 选项卡
  * 打开 `GPIO`
    * 选择 `PC0`，设置 `GPIO Pull-up/Pull-down` 为 `Pull-up`
    * 转到 `NVIC` 选项卡，勾选 `EXTI line0 interrupt` 的 `Enable`

### 2.2 生成代码（`STM32CubeMX`）

* 点击 `Project` - `Settings`
  * Project 选项卡
    * `Project Name`: Key_Interrupt
    * `Project Location`: (选择一个路径)
    * `Toolchain/IDE`: MDK-ARM V5
  * Code Generator 选项卡
    * 勾选 `Generate peripheral initialization as a pair of '.c/.h' files per peripheral`
* 设置好后，点击 `Project` - `Generate Code`

### 2.3 编写代码

* 在 _...\Key\_Interrupt\MDK-ARM_ 中选择文件 `Key_Interrupt.uvprojx` 用 Keil uVision 软件打开
  * 编译
  * 在 `gpio.c` 找到 `/* USER CODE BEGIN 2 */` 编写代码如下

```c
/* USER CODE BEGIN 2 */
void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin)
{
  if (GPIO_Pin & GPIO_PIN_0)
  {
    HAL_GPIO_TogglePin(GPIOC,GPIO_PIN_13);
  }
}
/* USER CODE END 2 */
```

* !!!编译成功后保存，将 _Key\_Interrupt_ 文件夹下的 __除了__ _Drivers_ 文件夹以外的文件和文件夹打包成zip压缩包，更改文件名为 `EN-C200 按键中断控制编程实践源代码.zip`
* 同样是上面修改代码的位置，编写代码如下

```c
/*我没新写了，俩压缩文件一样的也过了*/
```

* !!!编译成功后保存，将 _Key\_Interrupt_ 文件夹下的 __除了__ _Drivers_ 文件夹以外的文件和文件夹打包成zip压缩包，更改文件名为 `EN-C200 按键中断控制创新实验源代码.zip`

## 3 可能出现的错误

### 3.1  Keil软件编译报错 `*\*.sct(7): error: L6236E: No section matches selector - no section to be FIRST/LAST.`

* 右键 _Application\User_ 点击 `Manage Project Items...` - `Add Files...`
* 找到文件 `startup_stm32l431xx.s` 添加即可

## 4 上传的文件

* 编程实践源码: `EN-C200 按键中断控制编程实践源代码.zip`
* 创新实验源码: `EN-C200 按键中断控制创新实验源代码.zip`
* 要求代码没有语法错误，编译没有出错
