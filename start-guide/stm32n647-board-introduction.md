---
title: 'STM32N647 开发板介绍'
sidebar_position: 3
---

# STM32N647 开发板介绍

<!-- ![stm32n647 board show](./img/stm32n647-board-show.png) -->

STM32N647 开发板是正点原子以 STM32N647X0H3Q 为核心推出的开发板，开发板提供了强大的 AI 算力和 CPU 处理能力支持，可进行人工智能与机器听视觉的应用开发，同时，开发板板载丰富的存储器资源、多种传感器外设和通讯接口，非常适合用于 STM32N6 系列芯片的学习、开发和验证。

## 底板硬件资源

![dnn647 hardware](./img/dnn647-hardware.png)

| 硬件 | 描述 |
| --- | --- |
| STM32N647 核心板 | [**详细介绍**](#核心板硬件资源) |
| 调试接口 | 可用于 MCU 的在线调试和固件烧录 |
| 复位按键 | 作用与 MCU、NOR Flash、HyperRAM 和外接的 LCD 的复位 |
| 用户按键 | 用户可编程按键 |
| 用户 LED | 用户可编程 LED |
| DC 电源接口 | DC 电源输入接口（6V ~ 15V） |
| 电源开关 | 用于控制板卡电源 |
| 电源指示 LED | 指示板卡供电情况 |
| 电源引出接口 | 对外引出 5V 和 3.3V 电源 |
| 光环境传感器 | 可用于采集环境光强度及接近距离 |
| 红外接收 | 用于接收红外遥控信号 |
| 触摸按键 | 用于实现电容触摸按键 |
| 蜂鸣器 | 用于发出固定的提示音 |
| 可调电位器 | 用于控制输入 ADC 的电压 |
| USB UART 接口 | 用于与上位机的串口通信 |
| MIPI 摄像头接口 | 用于连接正点原子 MIPI 摄像头模块 |
| LCD 接口 | 用于连接正点原子 2.8 寸、3.5 寸、4.3 寸、7 寸等不用尺寸和分辨率的 MCU LCD 屏模块 |
| TF 卡接口 | 用于连接 TF 卡 |
| USB HOST 接口 | USB 2.0 接口，支持低速、全速和高速模块<br />支持 USB Host 模式 |
| USB SLAVE 接口 | USB 2.0 接口，支持低速、全速和高速模式<br />支持 USB Host 和 USB Device 模式 |
| 以太网接口 | 用于连接以太网，最高支持百兆以太网 |
| CAN 接口 | 用于进行 CAN 通信 |
| RS485 接口 | 用于进行 RS485 通信 |
| RS232 公座接口 | 用于进行 RS232 通信 |
| RS232 母座接口 | 用于进行 RS232 通信 |
| WIRELESS 模块接口 | 用于连接正点原子 WIRELESS 等 SPI 模块 |
| DVP 摄像头、OLED 接口 | 用于连接正点原子 OV5640 摄像头、OLED 等模块 |
| 1-Wire 接口 | 用于连接正点原子 DHT11、DS18B20 等传感器 |
| 多功能接口 | 用于 PWM DAC、ADC、触摸按键等功能的实现 |
| 音频输入接口 | 用于音频 Line 输入 |
| 音频输出接口 | 用于音频输出 |
| ATK MODULE 接口 | 用于连接正点原子 ATK MODULE 模块 |
| 光纤音频接口 | 用于音频输入 |

## 核心板硬件资源

![cnn647b hardware](./img/cnn647b-hardware.png)

| 硬件 | 描述 |
| --- | --- |
| STM32N647X0H3Q | ST 推出的基于ARM Cortex-M55 的高性能 MCU<br />800MHz 主频<br />内置 4.2MB SRAM<br />内置 600GPOS Neural-ART 加速器<br />内置 NeoChrom GPU、JPEG 编解码器、H-264 编码器<br />[**详细介绍**](./stm32n6-introduction.md) |
| NORFlash | 容量 32MB，Octo SPI 接口 |
| HyperRAM | 容量 32MB，HyperBus 接口 |
| SD NAND | 容量 16Gb，4 Bits SD 接口 |
| EEPROM | 容量 2Kb，I2C 接口 |
| LED | 蓝色 LED 为电源指示灯<br />红色 LED 为用户指示灯 |
| 按键 | 黑色按键为复位按键，作用与 MCU、NOR Flash、HyperRAM 和外接的 LCD<br />白色按键用户按键 |
| LCD 接口 | 用于连接正点原子 4.3 寸、7 寸、10.1 寸等不同尺寸和分辨率的 RGB LCD 屏模块 |
| USB 接口 | USB 2.0 接口，支持低速、全速和高速模式<br />支持 USB Host 和 USB Device 模式 |
| SWD 调试接口 | 可用于 MCU 的在线调试和固件烧录 |
| 串口接口 | 可用以与上位机或其他串口设备进行数据通讯 |