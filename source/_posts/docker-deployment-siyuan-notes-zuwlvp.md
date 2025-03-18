---
title: Docker部署思源笔记
date: '2024-08-09 11:04:30'
updated: '2025-03-14 13:44:11'
excerpt: >-
  本文介绍了如何使用 Docker 部署思源笔记的步骤。首先，需要在服务器上安装 Docker，并创建数据目录设置权限。接着，通过 Docker
  命令运行思源笔记的容器，其中重要项为 `--accessAuthCode`，用于设置授权码，这个授权码类似于密码。部署后，通过访问服务器的 IP
  加端口（6806）即可访问思源笔记的 Web 界面。不过，这种部署方式有几个限制：不支持桌面端和移动端应用连接、不能导出特定格式文件以及无法导入
  Markdown 文件。文中还建议通过域名来访问部署的服务，可以参考另外两篇文章进行 Nginx Proxy Manager 的反向代理配置，并确保开启
  WebSocket 的反代 `/ws`。最后，在进入 Web 界面时需输入之前设置的授权码以获得权限。
tags:
  - 服务器&NAS
permalink: /post/docker-deployment-siyuan-notes-zuwlvp.html
comments: true
toc: true
---





在开始部署之前，你需要安装 docker。具体安装见：[【docker】在服务器上安装 docker/docker-compose](https://tech.yemengstar.com/?p=536)

使用 docker 部署的思源笔记有以下限制：

* ** **不支持桌面端和移动端应用连接，仅支持在浏览器上使用** **。也就是**不能**当作同步服务器同步本地文件，但是可以多人协同协作。
* 不支持导出 PDF、HTML 和 Word 格式
* 不支持导入 Markdown 文件

```powershell
mkdir -p /root/data/docker_data/SiYuan && chown -R 1000:1000 /root/data/docker_data/SiYuan
```

你需要修改的是

* ​`--accessAuthCode`​\= 授权码（修改为你自己的授权码，类似密码）

```powershell
docker run -d -v /root/data/docker_data/SiYuan:/siyuan/workspace -p 6806:6806 -u 1000:1000 b3log/siyuan --workspace=/siyuan/workspace/ --accessAuthCode=授权码
```

![](https://raw.githubusercontent.com/Shepherd010/Shepherd010.github.io/master/source/images/siyuannote-bp04-20240809110513-gz1ehru.png)

然后你就可以访问 `ip:6806`​ 进入 WEB 界面了。

夜梦建议你使用域名，如果你已经完成解析，那么你可以看夜梦的这两篇文章进行反向代理：

[【docker】反向代理神器 ——Nginx Proxy Manager 的安装](https://tech.yemengstar.com/?p=443)

[【docker】Nginx Proxy Manager 的使用](https://tech.yemengstar.com/?p=677)

确保开启 WebSocket 反代 `/ws`​

访问 `ip:6806`​（或者你的域名）进入 WEB 界面后，输入授权码：
