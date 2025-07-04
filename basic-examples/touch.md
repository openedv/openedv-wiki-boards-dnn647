---
title: '触摸屏实验'
sidebar_position: 27
---

# 触摸屏实验

Touch

## 前言

本章，我们将介绍如何使用STM32N647来驱动触摸屏，STM32N647本身并没有触摸屏控制器，但是它支持触摸屏，可以通过外接带触摸屏的LCD模块（比如正点原子RGBLCD模块），来实现触摸屏控制。在本章中，我们将向大家介绍STM32控制正点原子RGBLCD模块，实现触摸屏驱动，最终实现一个手写板的功能。

正点原子N647的实验例程，默认支持RGBLCD显示器（包括4.3寸、7寸和10.1寸共计5款），这五款RGBLCD显示器均采用电容触摸的方式，在初始化电容触摸屏完成后，进入电容触摸屏测试程序（电容触摸屏无需校准！！），测试界面的右上角会有一个清空的操作区域（RST），点击这个地方就会将输入全部清除，恢复白板状态。

本实验对应的工程文件夹为：`<STM32N647 开发板软件包路径>/Projects/27_Touch`。

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

在代码编译成功之后，我们通过下载代码到开发板上，电容触摸屏测试如下图所示：

![img](./img/29.png)

电容屏支持多点触摸，每个点的颜色都不一样，图中的波浪线就是三点触摸画出来的，最多可以5点触摸。按右上角的RST标志，可以清屏。