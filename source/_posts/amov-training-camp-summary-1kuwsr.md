---
title: 阿木训练营总结
date: '2025-02-28 16:54:01'
updated: '2025-02-28 17:56:31'
excerpt: 本文总结了阿木实验室的训练营经验，重点介绍了数据传输逻辑、地面站功能、仿真模拟的重要性、机架样式优化、试飞场地的优势和知识串联。
tags:
  - UAV
permalink: /post/amu-training-camp-summary-1kuwsr.html
comments: true
toc: true
---





## 数据传输逻辑

1. 阿木实验室的数传通过构建局域网，以UDP数据包的方式传输，并且可以同时连接飞控和上位机；而我们的数传只能以串口通信的方式连接飞控。
2. 阿木实验室的数据传输逻辑是

    1. 飞机上电，上位机和飞控启动，局域网构建成功，可以通过NoMachine或SSH，从地面站访问上位机
    2. 通过上位机内部写好的Shell脚本配合launch文件，启动ROS节点，并与飞控通讯
    3. 地面站与飞机连接，实际上是与上位机连接，通过mavros来显示飞机的各项参数
    4. 在地面站启动相机/雷达/各种设备，实际上是给上位机发送指令，运行上位机中写好的shell脚本，启动对应节点
    5. 地面站通过调用API来显示摄像头/RVIZ图像，并传回点击、拖动等操作
3. 后续工作

    1. 保持以串口的方式连接飞控
    2. 通过地面站连接上位机热点的方式构建局域网，对于传输距离不够的情况可以：

        1. 加装增益天线
        2. 配置5G传输模块
    3. 研究属于自己的Shell脚本，实现数据流通的自动化，并且可以通过地面站一体控制

## 地面站

1. QGC做室外飞行无可替代，包含专业的GPS模块和打点导航；而对于室外飞行，阿木实验室的[普罗米修斯](https://gitee.com/amovlab/Prometheus)地面站则更为专业和完善，其功能包括自定义启动ROS结点、API推流传输图像/RVIZ等
2. QGC功能繁杂，代码繁杂，对于编译环境要求高，并且对ROS无支持，更复杂的功能较为少用；而普罗米修斯代码模块清晰，代码量少，并且可以实现ROS指令的自定义开发
3. 后续应学习普罗米修斯的开发逻辑，可以基于其开源版本二次开所需功能，更进一步地，可以完全自主地开发地面站，只保留我们所需的功能

​![普罗米修斯自定义DEMO](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250228175658113.png)​

## 仿真模拟

1. 无人机进度慢的原因是因为没有使用仿真系统进行测试，每次验证新想法需要烧录实机、协调飞手、现场改正错误，非常的消耗时间
2. 在本次训练营中，我和杨骏师兄在仿真平台中测试了很久，才终于调试好算法，而上传到实机一遍通过
3. 基于普罗米修斯地面站，阿木实验室开发了普罗米修斯仿真系统，其可以通过自定义DEMO（脚本），一键启动所需要的Gazebo环境、PX4、ROS及所需的ROS节点，非常方便调试

    ​![普罗米修斯连接仿真环境](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250228175626919.png)​

4. 后续工作

    1. 基于普罗米修斯仿真环境、Gazebo社区，打造符合需求的Gazebo世界
    2. 编写自定义Shell，快速启动所需仿真的内容
    3. 在实机飞行前，在仿真平台模拟实现效果

## 机架样式

1. 阿木实验室飞机的雷达，使用3d打印的倾斜架子架于飞机之上，可以很好地扫描整个环境；而我们实验室的飞机，雷达被架得太高，扫描效果会减弱。

    ​![阿木实验室飞机的雷达](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250228175658593.jpg)​

2. 对于各模块，阿木实验室均设计了外壳进行保护
3. 对于上位机、雷达、摄像头等，现有的机架样式已经不能满足我们的需求，需要依赖3D打印模型社区，选择合适我们的机架，并通过线上打印，多打几副以便备用。

## 试飞场地

1. 阿木实验室和上次的职业技术学院一样，拥有专业的飞行笼，里面设计了障碍区域、目标检测区域等

    ​![阿木实验室的飞行笼](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/20250228175621001.jpg)​

2. 我们学校可否申请该类场地，需求空间不大，且部署成本低，后续能大大方便调试飞机
3. 缺点是飞行噪音大，需要一个不需要保持安静的区域

## 知识串联

1. 对于OFFBOARD模式来说，搭载PX4的飞控只是一个三维位置接收器和运动规划器，其本身并不重要
2. PX4中很多的算法是飞行控制类的，但是这并不是我们的研究方向，故对于我们透明
3. 而视觉/雷达算法通过ROS平台实现，更需要深入学习
4. 在没有飞行场地的情况下，ROS平台的算法验证效果差、代价大，可以通过无人车来替代
