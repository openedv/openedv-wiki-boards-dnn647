---
title: 'Basic Timer'
sidebar_position: 8
---

# Basic Timer

基本定时器实验

## 前言

STM32N647有众多的定时器，其中包括3个基本定时器（TIM6、TIM7、TIM18）、13个通用定时器（TIM2-TIM5，TIM9-TIM17）、2个高级控制定时器（TIM1、TIM8）和5个低功耗定时器（LPTIM1-LPTIM5）。这些定时器彼此完全独立，不共享任何资源。本章我们学习如何使用STM32N647的基本定时器中断。我们将使用TIM6的定时器中断来控制LED0的翻转，在主函数用LED1的翻转来提示程序正在运行。

本实验，LED1用来指示程序运行，每200ms翻转一次。我们在更新中断中，将LED0的状态取反。LED0用于指示定时器发生更新事件的频率，500ms取反一次。

本实验对应的工程文件夹为：`<STM32N647 开发板软件包路径>/Projects/08_Basic_Timer`。

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

下载代码后，可以看到LED1不停闪烁（每400ms一个周期），而LED0也是不停的闪烁，但是闪烁时间较LED1慢（每1s一个周期）。