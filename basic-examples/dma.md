---
title: 'DMA'
sidebar_position: 19
---

# DMA

DMA实验

## 前言

本章，我们将介绍STM32N647的DMA。我们将利用DMA来实现串口数据传送，并在LCD模块上显示当前的传送进度。

每次按下按键KEY0，串口1就会以DMA方式发送数据，同时在LCD上面显示传送进度。打开串口调试助手，可以收到DMA发送的内容。LED0闪烁用于提示程序正在运行。

本实验对应的工程文件夹为：`<STM32N647 开发板软件包路径>/Projects/19_DMA`。

## 实验准备

1. 将 STM32N647 开发板软件包中提供的示例 FSBL 固件烧录到 STM32N647 开发板上。

:::tip[FSBL 烧录说明]

本实验使用的 FSBL 为 STM32N647 开发板软件包中的示例 FSBL，请根据 [**示例 FSBL介绍**](../start-guide/software-package/software-package.md#fsbl) 中的说明烧录对应 `fsbl.hex`。

不同的的实验中，若使用相同的 FSBL，则无需重复烧录。

:::

2. 将工程文件夹下 `Binary` 目录下的 `appli.hex` 依次烧录到 STM32N647 开发板上。

:::tip[烧录说明]

烧录顺序不影响烧录结果。

[**使用 `STM32CubeProgrammer` 烧录**](../start-guide/start-development/step-by-step.md#step-3-使用-stm32cubeprogrammer-烧录)。

:::

3. 将 LCD 通过 FPC 延长线接入 STM32N647 开发板核心板的 `RGBLCD` 接口。

:::info[LCD 适配说明]

本实验例程仅支持 `正点原子 RGB 触摸屏模块`。

:::

4. 使用 USB Type-C 数据线将串口调试助手的物理机与 STM32N647 开发板的 `USB UART` 接口连接。

5. 将 STM32N647 开发板的 BOOT 模式配置为 `Flash boot` 模式

:::tip[STM32N647 开发板 BOOT 模式配置说明]

通过 STM32N647 开发板 `P6` 的跳线帽配置其 BOOT 模式：

`Development boot`：B1 接 3V3

`Flash boot`：B0、B1 都接 GND

:::

6. 将对应接口的电源线接入 STM32N647 开发板底板的 USB Type-C 接口或 DC 接口，为其进行供电，并将 `K1` 自锁开关切换到开启状态。

## 实验现象

将程序下将程序下载到开发板后，可以看到LED0不停的闪烁，提示程序已经在运行了。LCD显示的内容如下图所示：

![img](./img/18.png)

我们打开串口调试助手，然后按KEY0，可以看到串口显示如下图所示：

![img](./img/19.png)

至此，我们整个DMA实验就结束了，希望大家通过本章的学习，掌握STM32N647的DMA使用。DMA是个非常好的功能，它不但能减轻CPU负担，还能提高数据传输速度，合理的应用DMA，往往能让你的程序设计变得简单。