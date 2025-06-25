---
title: 'JPEG 硬件解码实验'
sidebar_position: 42
---

# JPEG 硬件解码实验

JPEG

## 前言

这是一个 JPEG 硬件解码的实验，在 STM32N647 开发板上实现了显示 JPEG 图片的功能。

本实验对应的工程文件夹为：`<STM32N647 开发板软件包路径>/Projects/42_JPEG`。

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

4. 将 TF 卡接入 STM32N647 开发板的 `TF CARD` 接口。

:::info[JPEG 文件说明]

用于显示的 JPEG 文件需提前放在 TF 卡的根目录的 `PICTURE` 文件夹下。

:::

5. 将 STM32N647 开发板的 BOOT 模式配置为 `Flash boot` 模式

:::tip[STM32N647 开发板 BOOT 模式配置说明]

通过 STM32N647 开发板 `P6` 的跳线帽配置其 BOOT 模式：

`Development boot`：B1 接 3V3

`Flash boot`：B0、B1 都接 GND

:::

6. 将对应接口的电源线接入 STM32N647 开发板底板的 USB Type-C 接口或 DC 接口，为其进行供电，并将 `K1` 自锁开关切换到开启状态。

## 实验现象

`DS0` 灯以一定的频率闪烁。

LCD 上显示硬件解码后的 JPEG 图像。

每按下 `KEY0` 按键，LCD 上显示的 JPEG 图像会切换到上一张。

每按下 `KEY1` 按键，LCD 上显示的 JPEG 图像会切换到下一张。