# 串口打印与收发编程实践

[物联网终端软件实训(3)——USART与物联网模块接口通信实验代码 - 物联网技术 - EDA365电子论坛网](https://www.eda365.com/thread-227005-1-1.html)

## 1 操作

* 工程文件中（ _...\*\MDK-ARM_ 中选择文件 `*.uvprojx` 用 Keil uVision 软件打开）
  * 在 _Application\User_ 的 main.c等文件 中的 `/* USER CODE BRGIN */` 和 `/* USER CODE END */` 之间编写自己的代码

### 1.1 函数

```c
/**
 * @brief (在Blocking Mode下)发送数据
 * @param huart: (?)UART Handle
 * @param pData: 指向数据缓冲区的指针
 * @param Size: 要发送的数据长度
 * @param Timeout: 超时持续时间
 */
HAL_StatusTypeDef HAL_UART_Transmit(UART_HandleTypeDef *huart, uint8_t *pData, uint16_t Size, uint32_t Timeout);
```

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

### 1.4 USART2 设置

* Baud Rate 波特率
* Word Length 字长
* Parity 校验位
* Stop Bits 停止位
* Data Direction收发模式: 收发/仅接收/仅发送
* Over Sampling 过采样
* Single Sample 单采样

## 2 步骤

### 2.1 配置（`STM32CubeMX`）

* 打开 `STM32CubeMX` - 新建工程 - `Part Number Search` 中搜索 `STM32L431RC` - 选择第二个(Package: LQFP64)双击
* `Pinout` 选项卡
  * `RCC`：将 High Speed Clock (HSE) 和 Low Speed Clock (LSE) 设置为 `Crystal/Ceramic Resonator`
  * `RTC`：勾选 `Activate Clock Source`
  * `USART2`: Mode: `Asynchronous`
* `Clock Configuration` 选项卡 （设置见图）

![1](https://images2.imgbox.com/32/6e/ZmtxQs7H_o.png?download=true)

* `Configuration` 选项卡
  * 打开 `USART2`
    * Baud Rate 波特率: 9600 Bits/s
  * 打开 `NVIC`
    * `Priority Group`: `0 bits for pre-emption priority 4 bits for subpriority`
    * 勾选 `RCC global interrupt` 和 `USART2 global interrupt` 为 `Enable`

### 2.2 生成代码（`STM32CubeMX`）

* 点击 `Project` - `Settings`
  * Project 选项卡
    * `Project Name`: USART_TR
    * `Project Location`: (选择一个路径)
    * `Toolchain/IDE`: MDK-ARM V5
  * Code Generator 选项卡
    * 勾选 `Generate peripheral initialization as a pair of '.c/.h' files per peripheral`
* 设置好后，点击 `Project` - `Generate Code`

### 2.3 编写代码（编程实践）

* 在 _...\USART\_TR\MDK-ARM_ 中选择文件 `USART_TR.uvprojx` 用 Keil uVision 软件打开
  * 编译
* <1> 在 `usart.c` 找到 `/* USER CODE BEGIN 0 */` 和 `/* USER CODE END 0 */` 之间编写代码如下

```c
/* USER CODE BEGIN 0 */
#include <stdio.h>
#define USART2_REC_LEN 200 // USART2 接收数据的长度
uint8_t aRxBuffer[1]; // 接收一个字节的缓冲
uint8_t usart2_rec_buffer[500]; // USART2 接收数据的缓冲区
volatile uint16_t usart2_rcv_len=0; // 缓冲区起始数据的长度

int fputc(int ch, FILE *f) //  printf底层调用函数
{
  HAL_UART_Transmit(&huart2, (uint8_t *)&ch, 1, 0xff);
  return(0);
}
/* USER CODE END 0 */
```

* <2> 在 `usart.c` 找到 `/* USER CODE BEGIN 1 */` 和 `/* USER CODE END 1 */` 之间编写代码如下（重写回调函数）

```c
/* USER CODE BEGIN 1 */
void HAL_UART_RxCpltCallback(UART_HandleTypeDef *hUSART)
{
  /* Prevent unused argument(s) compilation warning */
  if(hUSART->Instance==USART2) // 判断来源为USART2
  {
    usart2_rec_buffer[usart2_rcv_len++] = aRxBuffer[0]; // 接收一个字符放到缓冲区并记录
  }
  HAL_UART_Receive_IT(&huart2, (uint8_t *)aRxBuffer, 1);
  /* NOTE : This function should not be modified, when the callback is needed,
            the HAL_UART_RxCpltCallback can be implemented in the user file.
   */
}
/* USER CODE END 1 */
```

* <3> 在 `usart.h` 找到 `/* USER CODE BEGIN Includes */` 和 `/* USER CODE END Includes */` 之间编写代码如下（进行外部全局变量的声明）

```c
/* USER CODE BEGIN Includes */
extern uint8_t aRxBuffer[];
extern uint8_t usart2_rec_buffer[];
extern volatile uint16_t usart2_rcv_len;
/* USER CODE END Includes */
```

* <4> 在 `main.c` 找到 `/* USER CODE BEGIN 2 */` 和 `/* USER CODE END 2 */` 之间编写代码如下

```c
HAL_UART_Receive_IT(&huart2, (uint8_t *)aRxBuffer, 1); // 使能串口中断
```

* <5> 在 `main.c` 找到 `/* USER CODE BEGIN 3 */` 和 `/* USER CODE END 3 */` 之间编写代码如下

```c
/* USER CODE BEGIN 3 */
printf("Welcome to Elec-Nest!\r\n"); // 直接在串口打印信息
HAL_Delay(3000); // 延迟3s
printf("\r\n *** welcome to Elec-Nest! ***\r\n");
printf("请发送一条消息，输入长度为10个字节。\r\n");
HAL_Delay(1000);
if(usart2_rcv_len >= 10) // 如果接受了十个字节的数据
{
  printf("发送的消息为：");
  HAL_UART_Transmit(&huart2, (uint8_t *)usart2_rec_buffer, usart2_rcv_len, 0xff); // 发送接收的数据
  memset(usart2_rec_buffer, 0, usart2_rcv_len); // 清空缓冲区（清十个字节）
  usart2_rcv_len = 0; // 重置接收长度
}
```

* !!!编译成功没有错误(Errors)后保存，将 _USART\_TR_ 文件夹下的 __除了__ _Drivers_ 文件夹以外的文件和文件夹打包成zip压缩包，更改文件名为 `EN-C200 串口打印与收发编程实践源代码.zip`

### 2.4 编写代码（创新实验）

* 自己随便改点就好。。。
  * 在之前基础上随便改的 `main.c` 例子见下

```c
/* USER CODE BEGIN 3 */
printf("Welcome");
HAL_Delay(3000);
printf("\r\n*** WELCOME ***\r\n");
printf("please input a 10 bit message:\r\n");
HAL_Delay(1000);
if(usart2_rcv_len >= 10)
{
  printf("MSG: ");
  HAL_UART_Transmit(&huart2, (uint8_t *)usart2_rec_buffer, usart2_rcv_len, 0xff);
  memset(usart2_rec_buffer, 0, usart2_rcv_len);
  usart2_rcv_len = 0;
  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_13, GPIO_PIN_SET);
}
```

* !!!编译成功没有错误(Errors)后保存，将 _USART\_TR_ 文件夹下的 __除了__ _Drivers_ 文件夹以外的文件和文件夹打包成zip压缩包，更改文件名为 `EN-C200 串口打印与收发创新实验源代码.zip`

## 3 可能出现的错误

### 3.1  Keil软件编译报错 `*\*.sct(7): error: L6236E: No section matches selector - no section to be FIRST/LAST.`

* 右键 _Application\User_ 点击 `Manage Project Items...` - `Add Files...`
* 找到文件 `startup_stm32l431xx.s` 添加即可

## 4 上传的文件

* 编程实践源码: `EN-C200 串口打印与收发编程实践源代码.zip`
* 创新实验源码: `EN-C200 串口打印与收发创新实验源代码.zip`
* 要求代码没有语法错误，编译没有错误
