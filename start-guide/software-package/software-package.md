---
title: '软件包介绍'
sidebar_position: 1
---

# 软件包介绍

STM32N647 开发板软件包（下面简称：软件包）是正点原子针对 STM32N647 开发板提供的一套软件包，软件包中包含了 STM32N647 开发板所需的 External loader、FSBL 示例和大量的应用示例，并且均提供了对应的源码，方便用户进行学习、开发和使用。


## 软件包文件结构

软件包的文件结构如下：

```shell
Software_Package/
|-- Drivers
|-- External_Loader
|-- FSBL
|-- Middlewares
|-- Projects
`-- STM32Cube_FW_N6_V1.0.0
```

### STM32Cube_FW_N6_V1.0.0

STM32Cube_FW_N6_V1.0.0 目录下存放的是由 ST 提供的面向 STM32N6 系列的 STM32Cube MCU 软件包（[**STM32CubeN6**](https://www.st.com.cn/zh/embedded-software/stm32cuben6.html)），可通过 [**这里**](https://www.st.com.cn/zh/embedded-software/stm32cuben6.html#get-software) 获取更新的完整软件版本。

STM32CubeN6 MCU 包内含 STM32Cube 硬件抽象层 (HAL) 和底层 (LL) API，以及一套一致的中间件组件，包括 Azure® RTOS USBX、FileX、LevelX、ThreadX、NetX Duo、USB Power Delivery、H.264 视频编码器 API、OpenBootloader、MCUboot、外部存储器管理器和加载器、图像信号处理 (ISP) 库。

### External_Loader

External_Loader 目录下存放的是适用于 STM32N647 开发板的 External loader 及其工程，其文件结构如下：

:::note[External loader 介绍]

External loader 是 STM32CubeProgrammer、STM32CubeIDE 等工具访问、操作 MCU 外部存储器所需的文件，可用于读取、烧录和擦除 MCU 外部存储器中的数据。

:::

```shell
External_Loader/
`-- MX25UM25645G_ATK-CNN647B
    |-- Binary
    |   `-- MX25UM25645G_ATK-CNN647B_ExtMemLoader.stldr
    `-- ......
```

External_Loader 目录下列出的是适用于 STM32N647 开发板的 External loader 工程。

:::tip[External loader 工程的命名规则]

以 `MX25UM25645G_ATK-CNN647B` 为例：

- `MX25UM25645G`：外部ROM型号

- `ATK-CNN647B`：核心板型号

:::

工程目录下的 Binary 文件夹中存放的是该工程对应生成的 External loader 文件。

:::warning[External loader 文件使用注意事项]

External loader 文件需拷贝到特定的路径下，才能被 STM32CubeProgrammer、STM32CubeIDE 等工具正确调用，具体路径如下：

- STM32CubeProgrammer：`<STM32CubeProgrammer 安装路径>/bin/ExternalLoader`

- STM32CubeIDE：`<STM32CubeIDE 安装路径>/plugins/com.st.stm32cube.ide.mcu.externaltools.cubeprogrammer.xxx/tools/bin/ExternalLoader`

:::

### FSBL

FSBL 目录下存放的是适用于 STM32N647 开发板的示例 FSBL 固件及其工程，其文件结构如下：

:::note[FSBL 介绍]

FSBL（First Stage Boot Loader） 固件是 STM32N6 启动后被加载运行的第一段用户程序，主要用于完成相应的初始化工作，并启动应用程序。

:::

```shell
FSBL/
`-- MX25UM25645G_W958D8NBYA5I_Example
    |-- Binary
    |   `-- fsbl.hex
    `-- ......
```

FSBL 目录下列出的是适用于 STM32N647 开发板的示例 FSBL 工程。

:::tip[示例 FSBL 工程的命名规则]

以 `MX25UM25645G_W958D8NBYA5I_Example` 为例：

- `MX25UM25645G`：外部ROM型号

- `W958D8NBYA5I`：外部RAM型号（若支持）

:::

工程目录下的 Binary 文件夹中存放的是该工程对应生成的 FSBL 固件文件。

### Projects

Projects 目录下存放的是适用于 STM32N647 开发板的应用示例及其工程，其文件结构如下：

```shell
Projects/
|-- 01_LED
|-- 02_Buzzer
|-- 03_Button
|-- 04_Button_EXTI
|-- 05_Serial
|-- 06_IWDG
|-- 07_WWDG
|-- 08_Basic_Timer
|-- 09_General_Purpose_Timer
|-- 10_Advanced_Control_Timer
|-- 11_TPAD
|-- 12_OLED
|-- 13_MPU
|-- 14_TFTLCD
|-- 15_RGBLCD
|-- 16_USMART
|-- 17_RTC
|-- 18_RNG
|-- 19_DMA
|-- 20_ADC
|-- 21_DTS
|-- 22_PWMDAC
|-- 23_EEPROM
|-- 24_AP3216C
|-- 25_RS485
|-- 26_FDCAN
|-- 27_Touch
|-- 28_Remote
|-- 29_DS18B20
|-- 30_DHT11
|-- 31_QMI8658A
|-- 32_QMC6308
|-- 33_Wireless
|-- 34_WS2812B
|-- 35_Sensor
|-- 36_Memory_Management
|-- 37_SD_NAND
|-- 38_SD_Card
|-- 39_FatFs
|-- 40_Chinese_Show
|-- 41_Picture_Show
|-- 42_JPEG
|-- 43_Camera
|-- 44_Music_Player
|-- 45_Recorder
|-- 46_SPDIF
|-- 47_Video_Player
|-- 48_FPU
|-- 49_DSP
|-- 50_Handwriting_Recognition
|-- 51_T9_Pinyin
|-- 52_USB_Device_Card_Reader
|-- 53_USB_Device_Sound_Card
|-- 54_USB_Device_Virtual_Serial
|-- 55_USB_Host_Disk
|-- 56_USB_Host_HID
|-- 57_ThreadX_Thread
|-- 58_ThreadX_Semaphore
|-- 59_ThreadX_Timer
|-- 60_ThreadX_Queue
|-- 61_NetXDuo_TCP_Client
`-- 99_Applications
```

Projects 目录下列出的是适用于 STM32N647 开发板的应用示例工程。

工程目录下的 Binary 文件夹中存放的是该工程对应生成的应用示例固件文件。

:::note[99_Applications 示例工程说明]

99_Applications 目录下存放是的较为综合的应用示例工程，软件包 FSBL 目录下的示例 FSBL 程序无法满足这些应用示例的需求，因此，99_Applications 目录下的应用示例工程均由其特定的 FSBL + Appli 工程组成，应用示例工程目录下的 Binary 文件夹中也存放了改工程对应生成的 FSBL 和 应用示例固件文件。

:::

### Drivers

Drivers 目录下存放的是 STM32N647 开发板特定的硬件驱动文件，其文件结构如下：

```shell
Drivers/
`-- BSP
    |-- ADC
    |-- AP3216C
    |-- ATIM
    |-- BEEP
    |-- BTIM
    |-- DHT11
    |-- DS18B20
    |-- DTS
    |-- EEPROM
    |-- ES8388
    |-- EXTI
    |-- FDCAN
    |-- GTIM
    |-- HyperRAM
    |-- IMX335
    |-- IWDG
    |-- JPEGCODEC
    |-- KEY
    |-- LCD
    |-- LED
    |-- NORFlash
    |-- NRF24L01
    |-- OLED
    |-- OV5640
    |-- PWMDAC
    |-- QMC6308
    |-- QMI8658A
    |-- REMOTE
    |-- RGBLCD
    |-- RNG
    |-- RS485
    |-- RTC
    |-- SD_CARD
    |-- SD_NAND
    |-- SPDIFRX
    |-- SYS
    |-- TOUCH
    |-- TPAD
    |-- UART
    |-- WS2812B
    |-- WS2812B_IO
    |-- WWDG
    `-- YT8512C
```

BSP 目录下存放了 STM32N647 开发板上几乎所有外设的驱动文件，包括 NORFlash、HyperRAM、显示屏、摄像头、音频等。

### Middlewares

Middlewares 目录下存放的是软件包中工程适用到的中间件文件，其文件结构如下：

```shell
Middlewares/
|-- AI
|-- ATKNCR
|-- FATFS
|-- MALLOC
|-- MJPEG
|-- NETXDUO
|-- PICTURE
|-- STM32_IMAGE_PROCESSING_LIBRARY
|-- STM32_MW_CAMERA
|-- STM32_MW_ISP
|-- STM32_VISION_MODELS_PP
|-- T9INPUT
|-- TEXT
|-- THREADX
|-- USBX
|-- USMART
|-- WAVDEC
`-- WAVENC
```

这些中间件主要用于工程中特定功能的实现，例如：USB协议栈、WAV编解码、文件系统等。