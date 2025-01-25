---
title: 构建 PX4 软件
date: '2024-10-11 10:04:17'
updated: '2025-01-25 21:37:34'
excerpt: >-
  本文介绍了如何构建 PX4 软件，包括在控制台或集成开发环境中从源代码构建固件的步骤。用户首先需要下载 PX4
  源代码，确保开发工具链已安装。进行首次构建时，可以通过启动 Gazebo SITL 模拟无人机飞行，验证系统设置。在为 Pixhawk 硬件构建时，进入
  PX4-Autopilot 目录并执行相应的 make 命令。成功后，可将编译好的固件上传到硬件。此外，提供了 VSCode
  集成开发环境的使用指南，以及针对构建问题的故障排除建议，例如更新子模块和清理构建环境。最后，概述了调用 make 的完整语法及可用的构建目标。
tags:
  - UAV
  - PX4
permalink: /post/build-px4-software-1nryug.html
comments: true
toc: true
---



---

* 构建 PX4 软件 | PX4 指南（主） --- Building PX4 Software
* [https://docs.px4.io/main/en/dev_setup/building_px4.html](https://docs.px4.io/main/en/dev_setup/building_px4.html)
* PX4 User and Developer Guide
* 2024-10-11 10:04:17

---

## 构建 PX4 软件

PX4 固件可以在控制台或集成开发环境（IDE）中从源代码构建，适用于模拟和硬件目标。

您需要构建 PX4 以便使用模拟器，或者如果您想修改 PX4 并创建自定义构建。如果您只是想在真实硬件上尝试 PX4，则可以使用 QGroundControl 加载预构建的二进制文件（无需遵循这些说明）。

在遵循这些说明之前，您必须首先为您的主机操作系统和目标硬件安装开发工具链。如果在遵循这些步骤后遇到任何问题，请参阅下面的故障排除部分。

### 下载 PX4 源代码

PX4 源代码存储在 Github 的 PX4/PX4-Autopilot 仓库中。

要将最新的 ( `main`​ 分支) 版本安装到您的计算机上，请在终端中输入以下命令：

```sh
git clone https://github.com/PX4/PX4-Autopilot.git --recursive
```

请注意，您在安装开发工具链时可能已经完成了此操作

这就是您获取最新代码所需做的全部。如果需要，您还可以获取特定版本的源代码。GIT 示例提供了更多关于处理版本和为 PX4 贡献的信息。

### 首次构建（使用模拟器）

首先，我们将使用控制台环境构建一个模拟目标。这使我们能够在转向真实硬件和集成开发环境之前验证系统设置。

使用以下命令启动 Gazebo SITL：

```sh
make px4_sitl gz_x500
```

这将打开 PX4 控制台：

​![PX4 Console](assets/console_gazebo.1HYlL2vW-20241011100417-7hafouq.png)​

您可能需要在继续之前启动 QGroundControl，因为默认的 PX4 配置在起飞前需要与地面控制连接。

无人机可以通过输入以下命令来飞行（如上面的控制台所示）：

```sh
pxh> commander takeoff
```

该车辆将起飞，您将在模拟器用户界面中看到这一点：

​![Gazebo UI with vehicle taking off](assets/gazebo_takeoff.CxeFn6fJ-20241011100417-egxshgp.png)​

无人机可以通过输入 `commander land`​ 着陆，整个模拟可以通过按 CTRL+C（或输入 `shutdown`​ ）来停止。

在地面控制站进行飞行模拟更接近于实际操作该飞行器。在飞行（起飞飞行模式）时点击地图上的一个位置并启用滑块。这将重新定位飞行器。

​![QGroundControl GoTo](assets/qgc_goto.BTsEWZBV-20241011100417-im3mo74.jpg)​

## 为 Pixhawk 构建

要为基于 Pixhawk 或 NuttX 的板卡构建，请进入 PX4-Autopilot 目录，然后使用您的板卡的构建目标调用 `make`​ 。

例如，要为 Pixhawk 4 硬件构建，可以使用以下命令：

```sh
cd PX4-Autopilot
make px4_fmu-v5_default
```

成功的运行将以类似的输出结束：

```sh
-- Build files have been written to: /home/youruser/src/PX4-Autopilot/build/px4_fmu-v4_default
[954/954] Creating /home/youruser/src/PX4-Autopilot/build/px4_fmu-v4_default/px4_fmu-v4_default.px4
```

构建目标 `px4_fmu-v4`​ 的第一部分指示固件的目标飞行控制器硬件。后缀 `_default`​ 在这种情况下指示固件配置，例如支持或省略特定功能。

​`_default`​ 后缀是可选的。例如， `make px4_fmu-v5`​ 和 `px4_fmu-v5_default`​ 产生相同的固件。

为非 Pixhawk NuttX 飞行控制器（以及所有其他板）提供的构建命令在各个飞行控制器板的文档中。

### 上传固件（刷写板子）

将 `upload`​ 附加到 make 命令中，以通过 USB 将编译后的二进制文件上传到自动驾驶硬件。例如

```sh
make px4_fmu-v4_default upload
```

成功的运行将以以下输出结束：

```sh
Erase  : [====================] 100.0%
Program: [====================] 100.0%
Verify : [====================] 100.0%
Rebooting.

[100%] Built target upload
```

‍

在图形化集成开发环境中编译，VSCode 是 PX4 开发的官方支持（和推荐）集成开发环境（IDE）。它易于设置，可用于为模拟和硬件环境编译 PX4。

## 故障排除

许多构建问题是由于子模块不匹配或构建环境未完全清理造成的。更新子模块并进行 `distclean`​ 可以修复这些错误：

```sh
git submodule update --recursive
make distclean
```

## PX4 制作构建目标

前面的部分展示了如何调用 make 来构建多个不同的目标，启动模拟器，使用 IDE 等。本节将展示 make 选项是如何构建的，以及如何找到可用的选择。

调用带有特定配置和初始化文件的 make 的完整语法是：

```sh
make [VENDOR_][MODEL][_VARIANT] [VIEWER_MODEL_DEBUGGER_WORLD]
```

供应商模型变体：（也称为 `CONFIGURATION_TARGET`​ ）

* 供应商：电路板的制造商： `px4`​ ， `aerotenna`​ ， `airmind`​ ， `atlflight`​ ， `auav`​ ， `beaglebone`​ ， `intel`​ ， `nxp`​ 等。Pixhawk 系列电路板的供应商名称是 `px4`​ 。
* 模型：板模型“模型”： `sitl`​ ， `fmu-v2`​ ， `fmu-v3`​ ， `fmu-v4`​ ， `fmu-v5`​ ， `navio2`​ ，等等。
* 变体：指特定配置：例如 `bootloader`​ , `cyphal`​ ，其中包含在 `default`​ 配置中不存在的组件。最常见的是 `default`​ ，可以省略。

您可以使用以下命令获取所有可用的 `CONFIGURATION_TARGET`​ 选项列表：

```sh
make list_config_targets
```

查看器模型调试器世界：

* 查看器：这是启动和连接的模拟器（“查看器”）： `gz`​ ， `gazebo`​ ， `jmavsim`​ ， `none`​  
  提示

  ​`none`​ 可用于启动 PX4 并等待模拟器（jmavsim、Gazebo、Gazebo Classic 或其他模拟器）。例如， `make px4_sitl none_iris`​ 启动 PX4 而不使用模拟器（但使用 iris 机架）。
* 模型：要使用的车辆模型（例如 `iris`​ （默认）， `rover`​ ， `tailsitter`​ 等），将由模拟器加载。环境变量 `PX4_SIM_MODEL`​ 将被设置为所选模型，然后在启动脚本中使用该模型以选择适当的参数。
* 调试器：使用的调试器： `none`​ （默认）， `ide`​ ， `gdb`​ ， `lldb`​ ， `ddd`​ ， `valgrind`​ ， `callgrind`​ 。有关更多信息，请参见仿真调试。
* 世界：（仅限 Gazebo Classic）。设置加载的世界（PX4-Autopilot/Tools/simulation/gazebo-classic/sitl\_gazebo-classic/worlds）。默认是 empty.world。有关更多信息，请参见 Gazebo Classic \> 加载特定世界。

您可以使用以下命令获取所有可用的 `VIEWER_MODEL_DEBUGGER_WORLD`​ 选项列表：

```sh
make px4_sitl list_vmd_make_targets
```

* ​`CONFIGURATION_TARGET`​ 和 `VIEWER_MODEL_DEBUGGER`​ 中的大多数值都有默认值，因此是可选的。例如， `gazebo-classic`​ 等同于 `gazebo-classic_iris`​ 或 `gazebo-classic_iris_none`​ 。
* 您可以使用三个下划线，如果您想在两个其他设置之间指定一个默认值。例如， `gazebo-classic___gdb`​ 等同于 `gazebo-classic_iris_gdb`​ 。
* 您可以使用 `none`​ 值来启动 PX4 并等待模拟器。例如，使用 `make px4_sitl_default none`​ 启动 PX4，并使用 `./Tools/simulation/jmavsim/jmavsim_run.sh -l`​ 启动 jMAVSim。

​`VENDOR_MODEL_VARIANT`​ 选项映射到 PX4 源树中 /boards 目录下的特定 px4board 配置文件。具体来说， `VENDOR_MODEL_VARIANT`​ 映射到配置文件 boards/VENDOR/MODEL/VARIANT.px4board（例如， `px4_fmu-v5_default`​ 对应于 boards/px4/fmu-v5/default.px4board）。

## 固件版本与 Git 标签

PX4 固件版本和自定义固件版本通过 MAVLink AUTOPILOT\_VERSION 消息发布，并在 QGroundControl 设置 \> 概述机架面板中显示：

​![Firmware info](assets/qgc_setup_summary_airframe_firmware.CcZm2RSp-20241011100417-tuhoyq9.jpg)​

这些是在构建时从您仓库树的活动 git 标签中提取的。git 标签应格式化为 `<PX4-version>-<vendor-version>`​ （例如，上图中的标签设置为 `v1.8.1-2.22.1`​ ）。
