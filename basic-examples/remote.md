---
title: '红外遥控器实验'
sidebar_position: 28
---

# 红外遥控器实验

Remote

## 前言

本章，我们将介绍STM32对红外遥控器的信号解码。STM32板子上标配的红外接收头和一个小巧的红外遥控器。我们将利用STM32的输入捕获功能，解码开发板标配的红外遥控器的编码信号，并将编码后的键值在LCD模块中显示出来。

本实验开机在LCD上显示一些信息之后，即进入等待红外触发，如过接收到正确的红外信号，则解码，并在LCD上显示键值和所代表的意义，以及按键次数等信息。LED0闪烁用于提示程序正在运行。

本实验对应的工程文件夹为：`<STM32N647 开发板软件包路径>/Projects/28_Remote`。

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

4. 将 STM32N647 开发板配套的红外遥控器对准 STM32N647 开发板的 `U17` 红外接收器。

5. 将 STM32N647 开发板的 BOOT 模式配置为 `Flash boot` 模式

:::tip[STM32N647 开发板 BOOT 模式配置说明]

通过 STM32N647 开发板 `P6` 的跳线帽配置其 BOOT 模式：

`Development boot`：B1 接 3V3

`Flash boot`：B0、B1 都接 GND

:::

6. 将对应接口的电源线接入 STM32N647 开发板底板的 USB Type-C 接口或 DC 接口，为其进行供电，并将 `K1` 自锁开关切换到开启状态。

## 实验现象

将程序下载到开发板后，可以看到LED0不停的闪烁，提示程序已经在运行了。LCD显示的内容如下图所示：

![img](./img/30.png)

此时我们通过遥控器按下不同的按键，则可以看到LCD上显示了不同按键的键值以及按键次数和对应的遥控器上的符号。LCD显示的内容如下图所示：

![img](./img/31.png)