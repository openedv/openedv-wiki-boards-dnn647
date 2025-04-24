---
title: 'RTC'
sidebar_position: 17
---

# RTC

RTC实时时钟实验

## 前言

本章，我们将介绍STM32N647的内部实时时钟（RTC）。我们将使用LCD模块来显示日期和时间，实现一个简单的实时时钟，并可以设置闹铃，另外还将介绍BKP的使用。

本实验通过LCD显示RTC时间，并可以通过usmart设置RTC时间，从而调节时间，或设置RTC闹钟，还可以写入或者读取RTC后备区域SRAM。LED1每两秒闪烁一次，表示进入WAKE UP中断。LED0闪烁，提示程序运行。

本实验对应的工程文件夹为：`<STM32N647 开发板软件包路径>/Projects/17_RTC`。

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

4. 将 STM32N647 开发板的 BOOT 模式配置为 `Flash boot` 模式

:::tip[STM32N647 开发板 BOOT 模式配置说明]

通过 STM32N647 开发板 `P6` 的跳线帽配置其 BOOT 模式：

`Development boot`：B1 接 3V3

`Flash boot`：B0、B1 都接 GND

:::

5. 将对应接口的电源线接入 STM32N647 开发板底板的 USB Type-C 接口或 DC 接口，为其进行供电，并将 `K1` 自锁开关切换到开启状态。

## 实验现象

将程序下载到开发板后，可以看到LED0不停的闪烁，提示程序已经在运行了，同时LED1每两秒闪烁一次，说明周期性唤醒中断工作正常。然后，可以看到LCD模块开始显示时间，如下图所示：

![img](./img/15.png)

如果时间和日期不正确，可以利用上一章介绍的usmart工具，通过串口来设置，并且可以设置闹钟时间等，如下图所示：

![img](./img/16.png)

按照图中编号15、16、17顺序，设置闹钟A、设置日期、设置时间。然后等待我们设置的时间到来后，串口打印ALARM A!这个字符串，证明我们的闹钟A程序正常运行了！