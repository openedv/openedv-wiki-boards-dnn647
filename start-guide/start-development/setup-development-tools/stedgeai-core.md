---
title: 'STEdgeAI-Core'
sidebar_position: 4
---

# STEdgeAI-Core

在开发过程中，STEdgeAI-Core 用于评估、优化和编译边缘 AI 模型。

## 系统环境变量配置

在开发前，需要配置 STEdgeAI-Core 的可执行文件路径到系统的环境变量，以便在命令行中直接调用 STEdgeAI-Core。

STEdgeAI-Core 的可执行文件所在的路径为：`<STEdgeAI-Core 安装路径>/2.0/Utilities/windows`

可通过以下命令验证环境变量是否配置成功：

```shell
stedgeai --version
```

如果环境变量配置成功，则该命令会输出 STEdgeAI-Core 的版本信息，例如：

```shell
ST Edge AI Core v2.0.0-20049
   ISPU 1.1.0
   MLC 1.1.0
   StellarStudioAI 2.0.0
   STM32CubeAI 10.0.0
```