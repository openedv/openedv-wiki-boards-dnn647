---
title: '跑马灯实验'
sidebar_position: 1
---

# 跑马灯实验

LED

## 前言

本章将通过一个经典的跑马灯程序，带大家开启STM32N647之旅。通过本章的学习，我们将了解到STM32N647的IO口作为输出使用的方法。我们将通过代码控制开发板上的LED灯：LED0、LED1交替闪烁，实现类似跑马灯的效果。

本实验的LED0和LED1每过500ms一次交替闪烁，实现类似跑马灯的效果。

本实验对应的工程文件夹为：`<STM32N647 开发板软件包路径>/Projects/01_LED`。

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

3. 将 STM32N647 开发板的 BOOT 模式配置为 `Flash boot` 模式

:::tip[STM32N647 开发板 BOOT 模式配置说明]

通过 STM32N647 开发板 `P6` 的跳线帽配置其 BOOT 模式：

`Development boot`：B1 接 3V3

`Flash boot`：B0、B1 都接 GND

:::

4. 将对应接口的电源线接入 STM32N647 开发板底板的 USB Type-C 接口或 DC 接口，为其进行供电，并将 `K1` 自锁开关切换到开启状态。

## 实验现象

下载代码后，可以看到LED0和LED1交替亮。