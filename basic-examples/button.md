---
title: '按键输入实验'
sidebar_position: 3
---

# 按键输入实验

Button

## 前言

上一章，我们介绍了STM32N647的IO口作为输出的使用。本章，我们将向大家介绍如何使用STM32N647的IO口作为输入。我们将利用板载的4个按键，来控制板载的两个LED灯亮灭。通过本章的学习，我们将了解到STM32N647的IO口作为输入的使用方法。

本实验将通过开发板上的四个独立按键控制LED灯：KEY0控制LED0翻转，KEY1控制LED1翻转，KEY2控制LED0、LED1状态翻转，KEY_UP控制LED0/LED1点亮。

本实验对应的工程文件夹为：`<STM32N647 开发板软件包路径>/Projects/03_Button`。

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

下载完之后，我们可以按KEY0、KEY1、KEY2和KEY_UP来看看LED灯的变化是否和我们预期的结果一致？