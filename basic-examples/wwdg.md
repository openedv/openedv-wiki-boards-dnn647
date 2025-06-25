---
title: '窗口看门狗实验'
sidebar_position: 7
---

# 窗口看门狗实验

WWDG

## 前言

本章我们学习如何使用STM32N647的另外一个看门狗，窗口看门狗（以下简称WWDG）。我们将使用窗口看门狗的中断功能来喂狗。

本实验用LED1用来指示中断喂狗，每次中断喂狗翻转一次。

本实验对应的工程文件夹为：`<STM32N647 开发板软件包路径>/Projects/07_WWDG`。

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

下载代码后，可以看到LED1开始不停的闪烁。每秒钟闪烁3次左右，说明程序在中断不停的喂狗，和我们预期的一致。