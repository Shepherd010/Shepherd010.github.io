---
title: 思源笔记配合插件实现HEXO文章快速发布
date: '2025-03-13 14:26:42'
updated: '2025-03-13 16:06:35'
excerpt: >-
  本文介绍了如何使用思源笔记和相关插件实现HEXO文章的快速发布及具体配置。首先，解释了HEXO有两种发布方式：本地编译和Github
  Action远程编译，并推荐第二种方式以实现云端备份。然后详细阐述了HEXO在GitHub上正确运行所需的设置，以及借助思源笔记“发布工具”插件进行文章发布的步骤，包括插件安装、平台添加、插件鉴权等。此外，还介绍了如何配置思源AI，通过国内代理chatgpt或其他大模型接入实现更智能的发布方式。对于图片发布，由于图片默认本地存储带来显示问题，因此建议使用PicGo图床工具并配合插件进行配置，以保证网站上正常显示图片。最后推荐了一些HEXO主题选项以改善网站视觉体验。本教程结合各类工具和步骤，旨在提升HEXO文章的发布效率与质量。
permalink: >-
  /post/siyuan-notes-and-plugin-realize-the-rapid-release-of-hexo-articles-za8u7r.html
comments: true
toc: true
---





‍

## 一 、 前言

对于HEXO而言，有两种发布方式，一种是使用本地node.js生成网页文件后部署Github Pages仓库；另一种是直接上传md文档，通过调用Github Action实现远程自动编译后部署。

对于第二种方式而言，配合思源笔记和插件，可以实现文章的快速发布和可视化发布，同时可以保证文章的云端备份，不过Github Action的部署方式要比本地部署缓慢一些。

## 二、 HEXO的设置

1. 首先先要在本地确保 Hexo 是可以正确运行的，比如：

```bash
hexo clean
hexo deploy
```

至于如何设置和使用 Hexo，请参考 [https://hexo.io/](https://hexo.io/)

2. 部署在GitHub上

参考[https://hexo.io/zh-cn/docs/github-pages](https://hexo.io/zh-cn/docs/github-pages)，注意不要使用一键部署的版本，而是使用GitHub Actions版本

3. 推荐使用VS Code搭配Github插件进行开发，和远程仓库同步。写出一篇文档后进行分支的同步，看Action是否正常运行，Page是否成功部署：

![image](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/image-20250313150100-6sezru7.png "VS Code同步仓库")​

‍

![image](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/image-20250313150417-7cxmwme.png "Github Action正常运行")​

### 三、 思源笔记插件“发布工具”的设置

1. 安装“发布工具”

![image](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/image-20250313150625-0huzj7c.png "发布工具插件页")

2. 对其进行设置

![image](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/image-20250313150704-gz63icy.png)

按说明添加HEXO平台

![image](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/image-20250313150817-djbfodd.png)

3. 添加插件在Github平台的鉴权

![image](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/image-20250313150927-rledt69.png)

注意：有效期请设置永久有效，权限最低要给`workflow 更新 GitHub Actions 工作流程`​

4. 将对应的Token复制到插件中，检测配置是否成功
5. 进行常规发布，同时到仓库的Github Actions页面查看是否正常运行；个人网站是否正常显示

## 四、 思源AI的设置

1. api的购买，我使用的是国内代理的chatgpt，可以实现最低官方28折的价格，购买链接和使用说明如下：

    1. [https://api.chatanywhere.org/#/](https://api.chatanywhere.org/#/)
    2. [https://zwxvec6g91g.feishu.cn/docx/KS7AddreTouQg6xs44Oc0ZgHnOg](https://zwxvec6g91g.feishu.cn/docx/KS7AddreTouQg6xs44Oc0ZgHnOg)
    3. 注意：官方文档API接入点有误，应该是`https://api.chatanywhere.tech`​，必须加https
    4. 扩展：在使用说明文档中，包含AI的大量应用，推荐阅读和尝试

2. 也可以使用其他家的模型，例如qwen、deepseek等
3. 在思源设置中填写对应API、模型、接入点

![image](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/image-20250313152315-gx1b90n.png)

4. 不同家的大模型的接入，只是“API基础地址”、“模型”、“API Key”需要改变，不需要改变最上方的“API提供商”，详见：

[https://ld246.com/article/1727862165942](https://ld246.com/article/1727862165942)（注：链滴是思源自己构建的论坛平台，推荐注册）

5. 现在可以在“发布工具”的常规发布页，调用更复杂的发布方式了：

![image](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/image-20250313152705-11uryoo.png)

### 五、 图片的发表

1. 没有配置图床之前，发表的图片默认为本地链接，没有一同上传到服务器，会出现图片破损的情况，与此同时你的思源本地服务还开着，在本地电脑上会看到图片已经上传的假象，因为网站通过思源本地服务器读取到了图片，而在别的设备上会看到图片的破损：

    ![image](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/image-20250313153307-eml7sq9.png)

2. 下载PicGo图床工具，并进行配置，上一篇规划中有教程链接，故不在赘述，我使用的是阿里云OSS存储，配置如下，仅供参考：

    ![image](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/network-asset-20250313153523340-20250313155416-96w9zxm.png)​

3. 在思源插件中下载“PicGo图床”插件并配置

    ![image](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/network-asset-20250313153621752-20250313155416-36nahj8.png)
    ![image](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/network-asset-20250313153817121-20250313155416-2lje9nn.png)

    一定要选择app，不要选择内置服务，内置服务好像有问题。
4. 在“发布工具”插件的HEXO平台设置中，图床服务选择PicGo插件

    ![image](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/network-asset-20250313154006527-20250313155416-4i3icls.png)

5. 通过发布工具发表一篇带图片的文章，用另一个设备检测是否正常显示
6. 查看PicGo相册中是否正常显示

    ![image](https://pic-lxy.oss-cn-shenzhen.aliyuncs.com/img/network-asset-20250313154135079-20250313155416-egxgxf2.png)​
7. 注意：在文章发表的时候，必须保证PicGo应用在后台运行，因为PicGo插件是调用其接口实现的

## 六、 HEXO主题的配置

1. 主题推荐:[https://blog.lixiaomu.fun/posts/43857/](https://blog.lixiaomu.fun/posts/43857/)
2. 我使用的主题为Icarus，官方网站为

    [https://ppoffice.github.io/hexo-theme-icarus/uncategorized](https://ppoffice.github.io/hexo-theme-icarus/uncategorized)

若要使用NPM将Icarus安装为Node包，在你的Hexo站点根目录运行如下命令：

```shell
npm install -S hexo-theme-icarus hexo-renderer-inferno
```

---

接下来，在你的站点的`_config.yml`​文件中的开启Icarus：

```yaml
theme: icarus
```

‍
