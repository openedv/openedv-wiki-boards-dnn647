---
title: 'NetXDuo TCP Client'
sidebar_position: 61
---

# NetXDuo TCP Client

NetXDuo TCP 客户端实验

## 前言

这是一个网络通讯实验，实现了 STM32N647 开发板作为 TCP 客户端与 TCP 服务器上位机进行通讯。

本实验对应的工程文件夹为：`<STM32N647 开发板软件包路径>/Projects/61_NetXDuo_TCP_Client`。

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

:::tip[Appli 固件说明]

Appli 固件默认设置目标 TCP 主机的 IP 地址为 `192.168.2.11`，端口号为 `8080`，可自行修改 `<工程文件夹路径>/Appli/NetXDuo/App/app_netxduo.c` 文件中的 `TCP_SERVER_IP_ADDRESS` 和 `TCP_SERVER_PORT` 宏定义。

:::

3. 将 TCP 服务器物理机通过网线与 STM32N647 开发板底板的 `EARTHNET` 接口连接。

4. 使用 USB Type-C 数据线将串口调试助手的物理机与 STM32N647 开发板的 `USB UART` 接口连接。

5. 将 STM32N647 开发板的 BOOT 模式配置为 `Flash boot` 模式

:::tip[STM32N647 开发板 BOOT 模式配置说明]

通过 STM32N647 开发板 `P6` 的跳线帽配置其 BOOT 模式：

`Development boot`：B1 接 3V3

`Flash boot`：B0、B1 都接 GND

:::

6. 将对应接口的电源线接入 STM32N647 开发板底板的 USB Type-C 接口或 DC 接口，为其进行供电，并将 `K1` 自锁开关切换到开启状态。

## 实验现象

通过串口调试助手观察实验现象：

```shell
STM32
NetXDuo TCP Client
ATOM@ALIENTEK
TCP Server Configuration
TCP Server IP: 192.168.2.11
TCP Server Port: 8080
```

开发板成功获取到 IP 地址，并等待连接至 TCP 服务器：

```shell
The network cable is connected.
100Mbps full-duplex.
Looking for DHCP server...
IP Address: 192.168.1.189
Network Mask: 255.255.252.0
Connecting to TCP server...
```

成功连接 TCP 服务器：

```shell
Connected to TCP server. [192.168.2.11:8080]
```

接收到来自 TCP 服务器的数据：

```shell
[192.168.2.11:8080] -> '
From TCP server.
'
```

TCP 服务器发送的数据将被回显。