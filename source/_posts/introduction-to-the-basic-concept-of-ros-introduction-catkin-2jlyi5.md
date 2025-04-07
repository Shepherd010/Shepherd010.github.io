---
title: ROS入门之基本概念+catkin简介
date: '2025-04-07 10:39:04'
updated: '2025-04-07 11:03:47'
excerpt: >-
  本文介绍了ROS的基本概念和catkin构建系统。首先，解释了编译和构建的定义，编译是将源代码转换为可执行文件，而构建则是安排编译过程。Makefile定义了编译规则，而Make命令依赖于此进行构建。CMake是一种跨平台安装工具，能够输出各种构建文件。


  随后，文章介绍了catkin，它是ROS定制的构建系统，基于cmake扩展，用于支持大型项目。为了创建一个catkin工作空间，需要使用命令`catkin_make`进行初始化，并将所有ROS代码置于`src`目录下。此过程中，会生成两个文件夹，其中`src`用于放置功能包(package)，**package**是catkin的基本构建单元，编译时，catkin会递归查找package。


  最后强调，完成编译后需运行`source ~/ros_test/devel/setup.bash`，将生成的可执行文件加入到系统环境中，以确保程序正常运行。
tags:
  - ROS
categories:
  - ' 工具简介'
permalink: /post/introduction-to-the-basic-concept-of-ros-introduction-catkin-2jlyi5.html
comments: true
toc: true
---





## 编译（make）和构建（build）

编译(compilation , compile)：编译就是把高级语言变成计算机可以识别的2进制语言，计算机只认识1和0，编译程序把人们熟悉的语言换成2进制的。

代码变成可执行文件，叫做**编译（compile**）；先编译这个，还是先编译那个（即编译的安排），叫做**构建（build**）。**Make**是最常用的**构建工具**，诞生于1977年，主要用于C语言的项目。但是实际上 ，任何只要某个文件有变化，就要重新构建的项目，都可以用Make构建。

1. 利用编译程序从源语言编写的源程序产生目标程序的过程。
2. 用编译程序产生目标程序的动作。

### makefile

 **makefile**定义了一系列的规则来指定哪些文件需要先编译，哪些文件需要后编译，哪些文件需要重新编译，甚至于进行更复杂的功能操作

 Make命令**依赖makefile**进行构建，make解释makefile中的命令

### 可执行文件

win下的可执行文件有比如exe等，linux是不依靠扩展名区分是否是可执行文件，而是文件的读写权限。当然，linux下的可执行文件一般的扩展名为ELF文件或者out文件。

### CMake（跨平台的安装（编译）工具）

CMake是一个跨平台的安装（编译）工具，可以用简单的语句来描述所有平台的安装(编译过程)。他能够**输出各种各样的makefile或者project文件**。

## catkin

### 1、概念

 ros定制的编译构建系统，对cmake的扩展。支持大体量工作。工作空间是一个文件夹，以catkin工具进行编译构建。

 ros代码都放在catkin worksoace中，这个工作空间需要通过指令**catkin_make**创建。

### 2、运行

```powershell
makdir -p ~/xxx/src#xxx可以随便取名;但必须有src;-p是递归创建目录 
cd ~/xxx/
catkin_make
```

 catkin\_make一可以创建工作空间，第二是编译产生目标文件

>  ***注意！！！***   
>  使用catkin\_make必须回到工作空间才能运行  
>  编译完成后，需要运行

```powershell
source ~/ros_test/devel/setup.bash
```

 作用是将编译生成的可执行文件的位置放在系统环境中。

 此时会多出两个文件夹

 ![在这里插入图片描述](http://127.0.0.1:1990/assets/a6e1dbc85dc6a6b5df691aecaf44a13d-20250407103904-0hrqi1f.png)​

代码放在src中，其他俩个了解就可以。

另一个编译系统rosbuild，是catkin的以前版本。

src放的是各种功能包，package，是catkin编译的基本单元。编译时，递归的查找package。  
 ![在这里插入图片描述](http://127.0.0.1:1990/assets/3d3967ffd90f8bd9e745f360b82e926d-20250407103904-rnofyi4.png)
