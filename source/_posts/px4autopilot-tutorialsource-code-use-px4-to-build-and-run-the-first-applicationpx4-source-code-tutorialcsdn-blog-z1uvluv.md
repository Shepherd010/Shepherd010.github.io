---
title: 使用PX4搭建并运行第一个应用程序
date: '2024-10-25 17:03:52'
updated: '2025-02-24 21:16:11'
excerpt: |-
  本文介绍了如何在PX4飞控上搭建并运行一个简单的板载应用程序。主要内容包括：

  1. **编写px4_simple_app应用程序文件**：
      - 创建C文件和CMake定义文件。
      - 在`px4_simple_app.c`文件中，编写一个最小应用程序示例，仅打印 `"Hello Sky!"` 。主函数必须命名为“应用程序名称_main”的形式，并从模块中导出 `__EXPORT` 。
      - 使用宏 `PX4_INFO` 将输出信息显示到PX4壳。

  2. **创建CMakeLists.txt文件**：
      - 使用 `px4_add_module()` 方法生成静态库，指定模块的主入口点及其相关源文件。

  3. **定义Kconfig文件**：
      - 定义该应用程序的名称，使其能够被内核配置器识别和启用。

  4. **编译并烧录应用程序到飞控固件中**：
      - 修改目标板级 CMake 文件（例如 `default.px4board`），添加对新应用程序的支持。
      - 在终端中使用 `make px4_fmu-v2_default` 命令编译固件。

  通过上述步骤，可以成功在PX4飞控中添加并运行一个自定义的简单应用程序。
tags:
  - UAV
  - PX4
permalink: >-
  /post/px4autopilot-tutorialsource-code-use-px4-to-build-and-run-the-first-applicationpx4-source-code-tutorialcsdn-blog-z1uvluv.html
comments: true
toc: true
---



本文主要说明如何搭建并运行你的第一个板载应用程序。

**Firmware/src/examples/px4_simple_app**文件夹下默认已经有一个完整的例程，如果遇到了问题可以作为参考。如果需要自己重新编写的话请重命名px4\_simple\_app文件夹或删除px4\_simple\_app文件夹。

### 1.编写px4\_simple\_app应用程序文件

我们创建一个很小的应用程序，只是打印出来`Hello Sky!`​。

​![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224205237274.png)​

这包括一个**C 文件**和一个**cmake 定义文件**（它告诉工具链如何构建应用程序）。

1. 新建如下文件夹： **Firmware/src/examples/px4_simple_app**。
2. 在该目录中新建一个名为 **px4_simple_app.c** 的 C 文件：

```c++
/**
 * @file px4_simple_app.c
 * Minimal application example for PX4 autopilot.
 */

#include <px4_platform_common/log.h>

__EXPORT int px4_simple_app_main(int argc, char *argv[]);

int px4_simple_app_main(int argc, char *argv[])
{
    PX4_INFO("Hello Sky!\n");
    return OK;
}
```

**main函数必须命名为 “应用程序名称” + “_” + “main” 的形式并从模块中导出**​ **​`__EXPORT。`​** ​

> 这里`__EXPORT`​是一个宏定义，其定义在Firmware/src/modules/systemlib/visibility.h中
>
> ```c++
> #ifdef __EXPORT
> #  undef __EXPORT//这里#后面的空格语法上是正确的，但不推荐这样写
> #endif
> #define __EXPORT __attribute__((visibility("default")))
>
> #ifdef __PRIVATE
> #  undef __PRIVATE//这里#后面的空格语法上是正确的，但不推荐这样写
> #endif
> #define __PRIVATE __attribute__((visibility("hidden")))
> ```
>
> ​`__attribute__()`​函数用于设置动态链接库中函数的可见性，将变量或函数设置为default，则该符号可在其他动态链接库中可见；将变量或函数设置为hidden，则该符号仅在本动态链接库中可见，在其他库中不可见。
>
> 编写大型程序时默认隐藏，针对特定变量和函数，在代码中使用`__attribute__((visibility("default")))`​令该符号外部可见，这种方法可有效避免动态链接库之间的符号冲突。
>
> （近似于类中的访问权限:public, private, protected）

​`PX4_INFO`​相当于输出到PX4 shell的`printf`​（包含在Firmware/src/platforms/px4\_log.h中）。 这里有不同的日志级别：`PX4_INFO`​、`PX4_WARN`​、`PX4_ERR`​、`PX4_DEBUG`​。 警告和错误会额外添加到 ULog 并显示在 Flight Review 中。

3. 创建并打开一个名为**CMakeLists.txt**的**cmake定义文件**：

```cmake
px4_add_module(
 MODULE examples__px4_simple_app
 MAIN px4_simple_app
 STACK_MAIN 2000
 SRCS
     px4_simple_app.c
 DEPENDS
 )
```

​`px4_add_module()`​ 方法根据模块描述生成静态库。

* ​`MODULE`​块是模块的唯一固件名称（按照惯例，模块名称的前缀是`src`​之后的父路径）
* ​`MAIN`​块列出了模块的入口点，它将命令注册到 NuttX，以便可以从 PX4 shell 或 SITL 控制台调用它。

4. 创建Kconfig文件，定义该应用程序的名称：

```Kconfig
menuconfig EXAMPLES_PX4_SIMPLE_APP
	bool "PX4 Simple app"
	default n
	---help---
		Enable PX4 simple app
```

> **PX4 Kconfig符号命名约定**：
>
> 按照惯例，模块/驱动程序的符号是根据模块文件夹路径命名的。
>
> 例如，Firmware/src/drivers/ADC/board\_ADC处ADC驱动程序的符号必须命名为drivers\_ADC\_board\_ADC。

应用程序的编写至此完成。

### 2.编译并烧录px4\_simple\_app应用程序到飞控固件中

为了运行它，首先需要确保它是作为PX4的一部分构建的。 应用程序被将依据目标的适当板级**cmake**文件添加到编译/固件中。

​![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224205522152.png)​

首先需要在px4board文件中添加px4\_simple\_app，位置在Firmware/boards/px4/fmu-v2/default.px4board，在空白行添加以下语句。

```
CONFIG_EXAMPLES_PX4_SIMPLE_APP=y
```

​![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224205522675.png)​

保存之后退出。

打开命令行终端Terminal，使用`ls`​、`cd`​命令进入Firmware文件夹中。

​![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224205523246.png)​

在Firmware文件夹中输入命令即可对固件进行编译。

```
make px4_fmu-v2_default
```

​![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224205523844.png)​

等待进度到100%即可完成固件编译。

​![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224205524399.png)​

将编译好的固件下载到无人机，需要输入命令。

```
make px4_fmu-v2_default upload
```

​![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224205525017.png)​

这里提示需要连接无人机的数据线，等待进度条读完即可完成烧录固件。

​![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224205525631.png)​

### 3.在QGC地面站MavlinkConsole终端运行px4\_simple\_app应用程序

打开QGC地面站，进入MavlinkConsole终端。

​![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224205526249.png)​

在终端中输入`help`​命令调出所有进程，这时会发现px4\_simple\_app已经在列表中。

​![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224205526751.png)​

在终端中输入`px4_simple_app start`​命令调用该进程。

​![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250224205527271.png)​

运行后会输出语句`INFO [px4_simple_app] Hello Sky!`​，说明程序运行成功。

---
