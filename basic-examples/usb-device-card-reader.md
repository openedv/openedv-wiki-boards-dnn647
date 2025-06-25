---
title: 'USB 读卡器（Device）实验'
sidebar_position: 52
---

# USB 读卡器（Device）实验

USB Device Card Reader

## 前言

这是一个 USB 从机的实验，在 STM32N647 开发板上实现了 USB 读卡器的功能。

本实验对应的工程文件夹为：`<STM32N647 开发板软件包路径>/Projects/52_USB_Device_Card_Reader`。

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

4. 使用 USB Type-C 数据线将具有 USB Host MSC 功能的物理机与 STM32N647 开发板的 `USB SLAVE` 接口连接。

5. 将 TF 卡接入 STM32N647 开发板的 `TF CARD` 接口。

6. 将 STM32N647 开发板的 BOOT 模式配置为 `Flash boot` 模式

:::tip[STM32N647 开发板 BOOT 模式配置说明]

通过 STM32N647 开发板 `P6` 的跳线帽配置其 BOOT 模式：

`Development boot`：B1 接 3V3

`Flash boot`：B0、B1 都接 GND

:::

7. 将对应接口的电源线接入 STM32N647 开发板底板的 USB Type-C 接口或 DC 接口，为其进行供电，并将 `K1` 自锁开关切换到开启状态。

## 实验现象

`DS0` 灯以一定的频率闪烁。

LCD 上显示外接 TF 卡的容量信息、板载 SD NAND 的容量信息和 USB 的连接状态。

USB Host 端，可通过 USB Host MSC 功能访问 TF 卡和 SD NAND。