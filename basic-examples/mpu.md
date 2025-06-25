---
title: '内存保护 (MPU) 实验'
sidebar_position: 13
---

# 内存保护 (MPU) 实验

MPU

## 前言

STM32的Cortex M4（STM32F3/F4系列）、Cortex M7（STM32F7/H7/H7RS系列）系列、Cortex M55（STM32N6）的产品，都带有内存保护单元（memory protection unit），简称：MPU。使用MPU可以设置不同存储区域的存储器访问特性（如只支持特权访问或全访问）和存储器属性（如可缓存、可共享），从而提高嵌入式系统的健壮性，使系统更加安全。接下来，我们将以STM32N647为例，给大家介绍内存保护单元（MPU）的使用。

本实验使用STM32N647自带的MPU功能，对一个特定的内存空间（地址：0x341FFC00）进行写访问保护。开机时，串口调试助手显示：MPU protected，表示默认是有写保护的。按下WK_UP，可以关闭内存保护，此时串口调试助手显示：MPU unprotected，按KEY0可以往数组里面写数据，按KEY1，可以读取数组里面的数据。如果不关闭内存写保护，直接按下KEY0写数据，会无法写入，导致程序出现异常。LED0用于提示程序正在运行，所有信息都是通过串口1输出，需要用串口调试助手查看。

本实验对应的工程文件夹为：`<STM32N647 开发板软件包路径>/Projects/13_MPU`。

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

3. 使用 USB Type-C 数据线将串口调试助手的物理机与 STM32N647 开发板的 `USB UART` 接口连接。

4. 将 STM32N647 开发板的 BOOT 模式配置为 `Flash boot` 模式

:::tip[STM32N647 开发板 BOOT 模式配置说明]

通过 STM32N647 开发板 `P6` 的跳线帽配置其 BOOT 模式：

`Development boot`：B1 接 3V3

`Flash boot`：B0、B1 都接 GND

:::

5. 将对应接口的电源线接入 STM32N647 开发板底板的 USB Type-C 接口或 DC 接口，为其进行供电，并将 `K1` 自锁开关切换到开启状态。

## 实验现象

下载代码后，LED0不停的闪烁，提示程序已经在运行了。串口助手首先提示MPU保护开启，我们按下WK_UP后，即可关闭内存保护，这时才可以正常往原内存保护区域写入数据，按下KEY0，可以写入数据，按下KEY1，可以读取数据，如图所示： 

![img](./img/11.png)

​	①上电默认开启内存保护，内存保护区域可设定读写权限

​	②按下WK_UP，可关闭内存保护。实验例程未关闭内存保护，无法通过按下KEY0写入数据

​	③按下KEY0，写入数据

​	④按下KEY1，读取数据