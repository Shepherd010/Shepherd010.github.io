---
title: 如何配置《动手学强化学习》的环境
date: '2025-03-13 10:56:29'
updated: '2025-03-14 13:59:08'
excerpt: >-
  本教程介绍了如何为《动手学强化学习》书籍配置Python环境，特别适用于需要使用`Pendulum-v0`或`CartPole-v0`环境的学习者。步骤包括：首先通过Conda创建一个新的Python
  3.8环境并激活它；随后安装`tqdm`、`matplotlib`和`torch`等必要库。在安装指定版本的`gym`（0.18.3）时，如果遇到setuptools版本过高导致的错误，需要将`setuptools`降级到66版本。之后，需要修改环境目录中的`requirement.py`文件，针对特定依赖关系进行调整。具体做法是，在指定行前加入相关代码，以解决opencv-python版本不兼容问题。完成以上步骤后，通过`pip
  list`命令可以确认环境成功配置。
tags:
  - 强化学习
categories:
  - 强化学习
permalink: >-
  /post/how-to-configure-the-environment-for-handon-reinforcement-learning-z292tq8.html
comments: true
toc: true
---





该教程要求使用gym\=\=0.18.3版本的gym库，本教程可以用于解决绝大多数需要使用`Pendulum-v0`​或者`CartPole-v0`​环境的学习者

#### 新建环境

```python
conda create --name myRL python=3.8
conda activate myRL
```

#### 安装必要的库

```
pip install tqdm, matplotlib, torch
```

#### 安装gym

 报错如下：

 ![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/118eede2816b60e7ecb7bbec02431b34-20250313105629-pd792c0.png)

 解决方法：

 setuptools的版本太高了，无法安装chatGPT，首先更新版本

```
pip install setuptools==66
```

 下一步，修改[配置文件](https://so.csdn.net/so/search?q=%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6&spm=1001.2101.3001.7020)

 找到你的环境所在目录，找到其中的`requirement.py`​文件

 ![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/aa8b31afc03a3fb6fa7071032dc0dfb6-20250313105629-08wljkk.png)

 ![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/8fad5cf08ba21e33c00a01b5bda7874f-20250313105629-hkth8e3.png)

 在原有的`parsed = _parse_requirement(requirement_string)`​上方，加入下面代码

```
if requirement_string.find('opencv-python>=3.')>=0:

            requirement_string += "0"    # opencv-python>=3.0
```

 ![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/a0733365ae8f1a0108135e8ea60a6e0e-20250313105629-a51zh4v.png)

 重新安装`pip install gym==0.18.3`​

 `pip list`​后可以发现配置成功

 ![在这里插入图片描述](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/18a39aaf6cf5485e9818d8e2b974e4e1-20250313105629-j9e3oep.png)
