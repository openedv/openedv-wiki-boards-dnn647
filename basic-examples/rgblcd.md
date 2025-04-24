---
title: 'RGBLCD'
sidebar_position: 15
---

# RGBLCD

LTDC LCD(RGB屏)实验

## 前言

在前面，我们介绍了TFTLCD模块（MCU屏）的使用，但是高分辨率的屏幕（超过800*480），一般都没有MCU屏接口，而是使用RGB接口的，这种接口的屏幕，就需要用到STM32N647的LTDC来驱动了。在本章中，我们将使用STM32N647开发板核心板上的LCD接口（仅支持RGB屏，本章介绍RGB屏的使用），来点亮LCD，并实现ASCII字符和彩色的显示等功能，并在串口打印LCD ID，同时在LCD上面显示。

本实验利用STM32N647的LTDC接口来驱动RGB屏，RGBLCD模块的接口在核心板上，通过40P的FPC排线连接RGBLCD模块，实现RGBLCD模块的驱动和显示，下载成功后，按下复位之后，就可以看到RGBLCD模块不停的显示一些信息并不断切换底色。同时，屏幕上会显示LCD的ID。

本实验对应的工程文件夹为：`<STM32N647 开发板软件包路径>/Projects/15_RGBLCD`。

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

下载代码后，LED0不停的闪烁，提示程序已经在运行了。我们可以看到屏幕的背景是不停切换的，如图所示： 

![img](./img/13.png)