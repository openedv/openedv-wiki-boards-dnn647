---
title: '独立看门狗实验'
sidebar_position: 6
---

# 独立看门狗实验

IWDG

## 前言

本章我们学习如何使用STM32N647的独立看门狗（以下简称IWDG）。STM32N647内部自带了两个看门狗：独立看门狗（IWDG）和窗口看门狗（WWDG）。这一章我们只介绍独立看门狗，窗口看门狗将在下一章介绍。在本章中，我们将通过按键KEY_UP来喂狗，然后通过LED0提示复位状态。

本实验在配置看门狗后，LED0将常亮，如果KEY_UP按键按下，就喂狗，只要KEY_UP不停的按，看门狗就一直不会产生复位，保持LED0的常亮，一旦超过看门狗定溢出时间（Tout）还没按，那么将会导致程序重启，这将导致LED0熄灭一次。

本实验对应的工程文件夹为：`<STM32N647 开发板软件包路径>/Projects/06_IWDG`。

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

下载代码后，可以看到LED0不停的闪烁，证明系统在不停的复位，否则LED0常亮。这时我们试试不停的按KEY_UP按键，可以看到LED0就常亮了，不会再闪烁。说明我们的实验是成功的。
