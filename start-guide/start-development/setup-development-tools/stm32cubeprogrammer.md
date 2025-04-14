---
title: 'STM32CubeProgrammer'
sidebar_position: 3
---

# STM32CubeProgrammer

在开发过程中，STM32CubeProgrammer 提供了烧录、调试和更新 ST-Link 固件等功能。

## 添加 External loader 文件

STM32CubeProgrammer 可以将固件或 AI 模型的参数文件烧录到 STM32N6 外部的 Flash中，不过需要借助 External loader 文件来实现。

:::tip[STM32N647 开发板的 External loader 文件]

STM32N647 开发板的软件包中提供了适用于 STM32N647 开发板的 External loader 文件。

:::

External loader 文件需拷贝到特定的路径下，才能被 STM32CubeProgrammer 正确调用，具体路径为 `<STM32CubeProgrammer 安装路径>/bin/ExternalLoader`。

将 External loader 文件拷贝到上述路径以后，STM32CubeProgrammer 就可以正常调用 External loader 文件了。