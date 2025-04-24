---
title: 'TPAD'
sidebar_position: 11
---

# TPAD

电容触摸按键实验

## 前言

上一章，我们介绍了STM32N647的输入捕获功能及其使用。这一章，我们将向大家介绍如何通过输入捕获功能，来做一个电容触摸按键。在本章中，我们将用 TIM2的通道4（ PF6）来做输入捕获，并实现一个简单的电容触摸按键，通过该按键控制 DS1 的亮灭。。

利用开发板板载的电容触摸按键(右下角白色LOGO，即TPAD)，通过TIM2_CH4（PF6）对电容触摸按键的检测，实现对DS1的控制, 下载本代码后，我们通过按压开发板右下角的TPAD按钮，就可以控制DS1的亮灭了。

本实验对应的工程文件夹为：`<STM32N647 开发板软件包路径>/Projects/11_TPAD`。

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

3. 用跳线帽短接 STM32N647 开发板 `P14` 接口的 `ADC` 和 `TPAD` 排针。

4. 将 STM32N647 开发板的 BOOT 模式配置为 `Flash boot` 模式

:::tip[STM32N647 开发板 BOOT 模式配置说明]

通过 STM32N647 开发板 `P6` 的跳线帽配置其 BOOT 模式：

`Development boot`：B1 接 3V3

`Flash boot`：B0、B1 都接 GND

:::

5. 将对应接口的电源线接入 STM32N647 开发板底板的 USB Type-C 接口或 DC 接口，为其进行供电，并将 `K1` 自锁开关切换到开启状态。

## 实验现象

下载代码后，可以看到 LED0 不停闪烁（每400ms 闪烁一次），用手指按下电容按键时，LED1 的状态发生改变（亮灭交替一次）。这里记得 TPAD 引脚和PF6都是连接到开发板上的排针上的，开始测试前需要连接好，否则测试就不准了，如果下载代码前没有连接好，请连接后复位重新测试即可。
