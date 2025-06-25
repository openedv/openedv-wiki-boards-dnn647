---
title: '外部中断实验'
sidebar_position: 4
---

# 外部中断实验

Button EXTI

## 前言

在前面几章的学习中，我们掌握了STM32N647的IO口最基本的操作。本章我们将介绍如何把STM32N647的IO口作为外部中断输入来使用，在本章中，我们将以中断的方式，实现我们在本章所实现的功能。

本实验，通过外部中断的方式让开发板上的四个独立按键控制LED灯：KEY0控制LED0翻转，KEY1控制LED1翻转，KEY2控制LED0/LED1同时翻转，KEY_UP控制LED0/LED1点亮。

本实验对应的工程文件夹为：`<STM32N647 开发板软件包路径>/Projects/04_Button_EXTI`。

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

下载完成之后，我们可以按KEY0、KEY1、KEY2和KEY_UP来看看LED灯的变化是否和我们预期的结果一致？