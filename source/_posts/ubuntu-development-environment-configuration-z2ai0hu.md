---
title: PX4的Ubuntu开发环境配置
date: '2024-10-11 09:47:14'
updated: '2025-01-25 21:13:11'
excerpt: >-
  本文介绍了如何在支持的 Ubuntu Linux LTS 版本上设置 PX4 开发环境，涵盖了 Ubuntu 22.04、20.04 和
  18.04。环境包括 Gazebo 模拟器和为 Pixhawk/NuttX 硬件构建的工具链。用户可以通过运行 `ubuntu.sh`
  脚本来进行安装，此脚本适用于干净的 Ubuntu 安装。在安装流程中，用户应根据提示进行确认，若需省略 NuttX
  或仿真工具可使用特定选项。完成之后，建议重新启动计算机。如果只想设置开发环境而不下载完整源代码，可以直接下载 `ubuntu.sh` 和
  `requirements.txt` 并执行。安装完命令行工具链后，用户可选择安装 VSCode 和 QGroundControl 的每日构建版，并开始构建
  PX4 软件。
tags:
  - UAV
  - PX4
permalink: /post/ubuntu-development-environment-configuration-z2ai0hu.html
comments: true
toc: true
---

# PX4的Ubuntu开发环境配置

---

* Ubuntu 开发环境 | PX4 指南（主） --- Ubuntu Development Environment
* [https://docs.px4.io/main/en/dev_setup/dev_env_linux_ubuntu.html](https://docs.px4.io/main/en/dev_setup/dev_env_linux_ubuntu.html)
* PX4 User and Developer Guide
* 2024-10-11 09:47:14

---

## Ubuntu 开发环境

以下说明使用 bash 脚本在 PX4 支持的 Ubuntu Linux LTS 版本上设置 PX4 开发环境：

Ubuntu 22.04（Jammy Jellyfish）、20.04（Focal Fossa）和 18.04（Bionic Beaver）

环境包括：

* Gazebo 模拟器（“Harmonic”）在 Ubuntu 22.04 上
* 在 Ubuntu 20.04 和 Ubuntu 18.04 上的 Gazebo Classic 模拟器
* 为 Pixhawk（及其他基于 NuttX 的硬件）构建工具链。

如果您需要在 Ubuntu 20.04 上使用 Gazebo，您可以手动安装 Gazebo "Garden"，但请注意，这将在 2024 年 11 月结束支持。如果您想在 Ubuntu 22.04 上使用 Gazebo Classic（例如），您可以按照 Gazebo Classic \> 安装中的说明手动安装它。

‍

## 仿真与 NuttX（Pixhawk）目标

使用 ubuntu.sh 脚本设置开发环境，以便您可以为模拟器和/或 NuttX/Pixhawk 工具链进行构建。

该脚本旨在干净的 Ubuntu LTS 安装上运行，如果在现有系统上“叠加”运行或在不同的 Ubuntu 版本上运行，可能无法正常工作。

### 安装工具链：

下载 PX4 源代码：  

```sh
   git clone https://github.com/PX4/PX4-Autopilot.git --recursive
```

源代码中的环境设置脚本通常适用于最近的 PX4 版本。如果使用较旧版本的 PX4，您可能需要获取特定于您版本的源代码。

1. 在 bash shell 中运行 ubuntu.sh 而不带任何参数以安装所有内容：  

    ```sh
    bash ./PX4-Autopilot/Tools/setup/ubuntu.sh
    ```

    * 在剧本进展中承认任何提示。
    * 您可以使用 `--no-nuttx`​ 和 `--no-sim-tools`​ 选项来省略 NuttX 和/或仿真工具。
2. 完成后重新启动计算机。

* 附加说明
* 您无论如何都需要 PX4 源代码。但是，如果您只是想设置开发环境而不获取所有源代码，您可以只下载 ubuntu.sh 和 requirements.txt，然后运行 ubuntu.sh：  

  ```sh
  wget https://raw.githubusercontent.com/PX4/PX4-Autopilot/main/Tools/setup/ubuntu.sh
  wget https://raw.githubusercontent.com/PX4/PX4-Autopilot/main/Tools/setup/requirements.txt
  bash ubuntu.sh
  ```

## 下一步

一旦您完成了命令行工具链的设置：

* 安装 VSCode（如果您更喜欢使用 IDE 而不是命令行）。
* 安装 QGroundControl 每日构建版
* 构建 PX4 软件
