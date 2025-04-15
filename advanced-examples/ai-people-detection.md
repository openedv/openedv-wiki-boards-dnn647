---
title: 'AI People Detection'
sidebar_position: 1
---

# AI People Detection

人体检测实验

## 前言

这是一个机器视觉的应用案例，实现了在 STM32N647 开发板上部署物体检测模型。

:::info[预训练模型说明]

预训练模型文件来自 [**STM32 Model Zoo**](https://github.com/STMicroelectronics/stm32ai-modelzoo/tree/v3.0.0/object_detection/tiny_yolo_v2/ST_pretrainedmodel_custom_dataset/st_person/tiny_yolo_v2_224)。

:::

本实验对应的工程文件夹为：`<STM32N647 开发板软件包路径>/Projects/99_Applications/991_AI_People_Detection`。

## 实验准备

1. 将工程文件夹下 `Binary` 目录下的 `network-data.hex`、`fsbl.hex` 和 `appli.hex` 依次烧录到 STM32N647 开发板上。

:::tip[烧录说明]

烧录顺序不影响烧录结果。

[**使用 `STM32CubeProgrammer` 烧录**](../start-guide/start-development/step-by-step.md#step-3-使用-stm32cubeprogrammer-烧录)。

:::

2. 将摄像头接入 STM32N647 开发板底板的 `J2` 接口。

:::info[摄像头适配说明]

本实验例程仅支持 `正点原子 MCIMX335 摄像头模块`。

:::

3. 将 LCD 通过 FPC 延长线接入 STM32N647 开发板核心板的 `RGBLCD` 接口。

:::info[LCD 适配说明]

本实验例程仅支持分辨率为 `800x480`，尺寸为 `4.3'` 或 `7'` 的 `正点原子 RGB 触摸屏模块`。

:::

4. 将 STM32N647 开发板的 BOOT 模式配置为 `Flash boot` 模式

:::tip[STM32N647 开发板 BOOT 模式配置说明]

通过 STM32N647 开发板 `P6` 的跳线帽配置其 BOOT 模式：

`Development boot`：B1 接 3V3

`Flash boot`：B0、B1 都接 GND

:::

5. 将对应接口的电源线接入 STM32N647 开发板底板的 USB Type-C 接口或 DC 接口，为其进行供电，并将 `K1` 自锁开关切换到开启状态。

## 实验现象

LCD 上实时显示摄像头采集的画面图像，并在检测到人体时在画面上绘制检测框。

## 附录

### 生成模型转换

工程文件夹下 `Model` 目录下提供了生成模型转换的 Shell 脚本 `generate-n6-model.sh`，直接运行该脚本即可生成模型转换后的文件，例如：

```shell
<工程文件夹>/
|-- Binary
|   `-- network_data.hex
|-- Model
    |-- network_ecblobs.h
    `-- network.c
```