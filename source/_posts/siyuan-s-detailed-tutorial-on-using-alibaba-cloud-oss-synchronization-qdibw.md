---
title: 思源使用阿里云 OSS 同步详细教程
date: '2024-07-10 13:30:10'
updated: '2025-03-11 23:23:08'
excerpt: 思源使用阿里云 OSS 同步详细教程
tags:
  - 服务器&NAS
permalink: >-
  /post/siyuan-s-detailed-tutorial-on-using-alibaba-cloud-oss-synchronization-qdibw.html
comments: true
toc: true
---





---

‍

## 1.创建存储桶

* 登录 [阿里云官网](https://ld246.com/forward?goto=https%3A%2F%2Faccount.aliyun.com%2Flogin%2Flogin.htm%3Foauth_callback%3Dhttps%3A%2F%2Foss.console.aliyun.com%2Findex)，可以用支付宝扫码登录
* 登录之后创建 Bucket

  ![image.png](http://127.0.0.1:1547/assets/image-oZ0CBrT-20240710133010-9fkk8xk.png)​
* 「Bucket 名称」任取 (取完之后**复制**下来，等下要用)，地域选择离你最近的那个，其他的设置保持默认。  
  （PS：如果想使用香港免费额度的话，就是下图的“地域”选取香港即可，其余的步骤都一样）  
  ​![image.png](http://127.0.0.1:1547/assets/image-UQrqmah-20240710133010-l7e4fma.png)​
* 创建完成后会跳转到如下界面，**复制**下「外网访问-Endpoint（地域节点）」  
  ​![image.png](http://127.0.0.1:1547/assets/image-zdKuxKj-20240710133010-wagdwpp.png)​

  ‍

## 2.创建子账户

* 这时候我们只有主账户，权限很高，风险也很大。同步不需要这么大的权限，所以接下来创建一个子账户接管部分权限。鼠标移动到右上角的头像位置，点击 「AccessKey 管理」  
  ​![image.png](http://127.0.0.1:1547/assets/image-PjGH7yf-20240710133010-ou6it4p.png)​
* 接下来会弹出一个安全提示的窗口，点击「开始使用子用户 AccessKey」

![image.png](http://127.0.0.1:1547/assets/image-u0zGWCs-20240710133010-eadmfbd.png)​

* 然后「创建用户」  
  ​![image.png](http://127.0.0.1:1547/assets/image-szohrIY-20240710133010-jpl64ft.png)​
* 「登录名称」和「显示名称」任取，但是注意：「​**Open API 调用访问**​」要勾选上  
  ​![image.png](http://127.0.0.1:1547/assets/image-0CnMgRd-20240710133010-oubgqhp.png)701 x 338
* 点击确定之后，会显示  AccessKey ID 和 AccessKey Secret 的信息，两个都**复制**一下

  * 注意：AccessKey Secret 信息​**只会显示这一次**​，请妥善保管
* 这里之前漏掉了一步，评论区有朋友提到了，感谢 Fix。
* 在创建完子账户之后，需要给子账户授予 OSS 权限
* 鼠标移动到右上角头像处，点击「访问控制」-「用户」-「添加权限」![image.png](http://127.0.0.1:1547/assets/image-Voizihy-20240710133010-yz607kf.png)
* 选中 AliyunOSSFullAccess，然后确定即可

  ![image.png](http://127.0.0.1:1547/assets/image-P4oZQOm-20240710133010-ilpwkze.png)

  ‍

## 3.给子账户添加 Bucket 权限

* 返回初始的 Bucket 界面，在「权限控制」-「Bucket 授权策略」中「新增授权」  
  ​![image.png](http://127.0.0.1:1547/assets/image-BxQGW9E-20240710133010-ygf6c0k.png)​

  ‍
* 在授权界面，「授权资源」-「整个 Bucket」；「授权用户」-「子账号」-选择刚刚创建的子账号；「授权操作」-「完全控制」  
  ​![image.png](http://127.0.0.1:1547/assets/image-QhLtzXZ-20240710133010-jzmmaeg.png)​

  ‍

## 4.开通套餐包

* 按步骤操作下来之后我们已经获得了相应的权限，同时复制了所需的所有信息，就是这四个：Bucket 名称、Endpoint（地域节点）、AccessKey ID 和 AccessKey Secret
* 通过[填写阿里云问卷](https://ld246.com/forward?goto=https%3A%2F%2Fwww.aliyun.com%2Factivity%2Fstorage%2Fossbag%3Fspm%3D5176.8465980.activity.1.77c21450ASmxuB) 购买特惠套餐包，1 元体验 3 个月

## 5.思源填入对应信息

* 打开思源，「设置」-「云端」，填入对应的信息即可

  * Endpoint 对应 Endpoint（地域节点）
  * Access Key 对应 AccessKey ID
  * Secret Key 对应 AccessKey Secret
  * Bucket 对应 Bucket 名称
  * Region 参考[这里](https://ld246.com/forward?goto=https%3A%2F%2Fhelp.aliyun.com%2Fzh%2Foss%2Fuser-guide%2Fregions-and-endpoints%3Fspm%3Da2c4g.11186623.0.0.20555b4enZQnaJ%23section-plb-2vy-5db)的 Region ID 进行填写
  * Timeout (s) 保持默认的 30
  * Addressing 保持默认的 Virtual-hosted-style 选项
  * TLS Verify 保持默认的 Verify
* 所有配置完成，开始同步之旅吧

  ‍

第三方同步价格：第三方同步选择 - S3 服务商对比推荐[^1]

[^1]: # 第三方同步选择 - S3 服务商对比推荐

    ## 1. 阿里云 OSS

    * 内地无免费额度，[按量计费模式](https://ld246.com/forward?goto=https%3A%2F%2Fwww.aliyun.com%2Fprice%2Fproduct%3Fspm%3Da2c4g.11186623.0.0.2644731215SOtN%23%2Foss%2Fdetail%2Fossbag)

      * 存储费用：0.12 元/GB/月
      * 流量费用：24:00-08:00 (闲时): 0.25 元/GB；08: 00-24:00(忙时): 0.50 元/GB
      * 请求费用：0.01 元/万次
      * Tips：阿里云香港地域每个月都有免费的 [5GB 存储空间](https://ld246.com/forward?goto=https%3A%2F%2Fhelp.aliyun.com%2Fdocument_detail%2F173534.html%3Fspm%3Da2c4g.11186623.0.0.6eb326e5G1MMbs%23%3A%7E%3Atext%3D%25E6%25A0%2587%25E5%2587%2586%25E5%25AD%2598%25E5%2582%25A8%25EF%25BC%2588%25E6%259C%25AC%25E5%259C%25B0%25E5%2586%2597%25E4%25BD%2599%25EF%25BC%2589%25E5%25AE%25B9%25E9%2587%258F%25E6%2594%25AF%25E6%258C%2581%25E4%25BD%25BF%25E7%2594%25A85%2520GB%2F%25E6%259C%2588%25E7%259A%2584%25E5%2585%258D%25E8%25B4%25B9%25E9%25A2%259D%25E5%25BA%25A6)和 [5GB 下载流量](https://ld246.com/forward?goto=https%3A%2F%2Fhelp.aliyun.com%2Fdocument_detail%2F173535.html%23%3A%7E%3Atext%3D%25E5%25A4%2596%25E7%25BD%2591%25E6%25B5%2581%25E5%2587%25BA%25E6%25B5%2581%25E9%2587%258F%25EF%25BC%2588NetworkOut%25EF%25BC%2589%25E6%2594%25AF%25E6%258C%2581%25E4%25BD%25BF%25E7%2594%25A85%2520GB%2F%25E6%259C%2588%25E7%259A%2584%25E5%2585%258D%25E8%25B4%25B9%25E9%25A2%259D%25E5%25BA%25A6)
    * [资源包定价](https://ld246.com/forward?goto=https%3A%2F%2Fcommon-buy.aliyun.com%2F%3Fspm%3Da2c4g.11186623.0.0.20da5a2dQapgxY%26commodityCode%3Dossbag%26request%3D%257B%2522region%2522%253A%2522china-common%2522%257D%23%2Fbuy)

      * 存储包： 最低一年 9 元 40GB；99 元 100GB
      * 流量包：最低一年 411 元，每月 100GB 下载流量
      * Tips：理论上可以实现 18 元/80GB/年的存储空间，仅从[阿里云官方文档条款](https://ld246.com/forward?goto=https%3A%2F%2Fhelp.aliyun.com%2Fdocument_detail%2F48272.html%23section-62f-d7o-56a)推测，暂无实测  
        方式为先购买一个 bucket 所在地域的指定地域专用资源包，然后再购买一个大陆通用资源包，两者可以叠加使用
      * 阿里云推出优惠存储包：[对象存储 OSS 预留空间](https://ld246.com/forward?goto=https%3A%2F%2Fcommon-buy.aliyun.com%2F%3Fspm%3D5176.8465980.rc-intro.dgo-buy-rc.62441450xDinwN%26commodityCode%3Doss_rc_dp_cn)，目前 **500G** 存储空间，1 年 118 元

    ## 2. 腾讯云 COS

    * 无免费额度，按量计费模式

      * [存储费用](https://ld246.com/forward?goto=https%3A%2F%2Fcloud.tencent.com%2Fdocument%2Fproduct%2F436%2F53482%23%3A%7E%3Atext%3D%25E9%2587%258F%25E8%25AE%25A1%25E8%25B4%25B9%25E3%2580%2582-%2C%25E5%25AD%2598%25E5%2582%25A8%25E5%25AE%25B9%25E9%2587%258F%25E5%25AE%259A%25E4%25BB%25B7%2C-%25E4%25BB%25A5%25E4%25B8%258B%25E8%25A1%25A8%25E6%25A0%25BC%25E4%25B8%25BA) ：各地域不一样，范围在 0.099-0.15 元/GB/月
      * [流量费用](https://ld246.com/forward?goto=https%3A%2F%2Fcloud.tencent.com%2Fdocument%2Fproduct%2F436%2F53863%23%3A%7E%3Atext%3D%25E5%258D%2597%25E4%25BA%25AC%25E3%2580%2581%25E4%25B8%258A%25E6%25B5%25B7%25E3%2580%2581%25E5%25B9%25BF%25E5%25B7%259E-%2C0.5%2C-0.15) ：全时段 0.50 元/GB
      * [请求费用](https://ld246.com/forward?goto=https%3A%2F%2Fcloud.tencent.com%2Fdocument%2Fproduct%2F436%2F53861%23%3A%7E%3Atext%3D%25E5%25AD%2598%25E5%2582%25A8%25E7%25B1%25BB%25E5%259E%258B-%2C%25E8%25AF%25B7%25E6%25B1%2582%25E8%25B4%25B9%25E7%2594%25A8%2C-%25EF%25BC%2588%25E5%2585%2583%2F%25E4%25B8%2587%25E6%25AC%25A1) ：0.01 元/万次
    * [资源包定价](https://ld246.com/forward?goto=https%3A%2F%2Fbuy.cloud.tencent.com%2Fcos) ：

      * 存储包：最低一年 9.77 元 10GB；93.46 元 100GB
      * 流量包：最低一年 41.4 元，每月 10GB 下载流量

    ## 3. 华为云 OBS

    * 无免费额度，[按量计费模式](https://ld246.com/forward?goto=https%3A%2F%2Fwww.huaweicloud.com%2Fpricing.html%3Ftab%3Ddetail%23%2Fobs)

      * 存储费用：0.099 元/GB/月
      * 流量费用：24:00-08: 00 (闲时): 0.25 元/GB；08: 00-24:00(忙时): 0.50 元/GB
      * 请求费用：0.01 元/万次
    * [资源包定价](https://ld246.com/forward?goto=https%3A%2F%2Fwww.huaweicloud.com%2Fpricing.html%23%2Fobs)

      * 存储包：最低一年 9 元 40GB；81 元 100GB
      * 流量包：最低一年 108 元，每月 50GB 下载流量

    ## 4. 七牛云 Kodo

    * 存储空间免费 10G，[按量计费模式](https://ld246.com/forward?goto=https%3A%2F%2Fwww.qiniu.com%2Fprices%2Fkodo%3Fref%3Ddeveloper.qiniu.com%26s_path%3D%252Fkodo%252F6379%252Fmetering-and-billing)

      * 存储费用：[10G 内免费](https://ld246.com/forward?goto=https%3A%2F%2Fwww.qiniu.com%2Fprices%2Fkodo%3Fref%3Ddeveloper.qiniu.com%26s_path%3D%252Fkodo%252F6379%252Fmetering-and-billing%23%3A%7E%3Atext%3D0%2520%252D%252010%2520GB-%2C%25E5%2585%258D%25E8%25B4%25B9%2C-0.06%2520%25E5%2585%2583%2FGB)，超出 10G 后 0.098 元/GB/月
      * 流量费用：各地域不一样，范围在 0.26-0.29 元/GB
      * 请求费用：10 万次内免费
    * [资源包定价](https://ld246.com/forward?goto=https%3A%2F%2Fqmall.qiniu.com%2Ftemplate%2FMTEy%3Fspec_combo%3DMzA0Mw%26kodoprice-txt%3D)：

      * 存储包：最低一年 13.2 元 50GB（新用户特惠），后续活动价格大概在 37 元/50GB/年左右
      * 流量包：最低一年 136.8 元，每月 50GB 下载流量
    * 2022 年 12 月 16 日更新：**没有域名**也可以使用七牛云的 S3 对象存储服务来同步思源笔记，只是不能外链下载

    ## 5. 金山云 KSS

    * 无免费额度，[按量计费模式](https://ld246.com/forward?goto=https%3A%2F%2Fsw.ksyun.com%2Fpro%2Fcalc%2F%23%2Fcom%2F37443%2Fdoc)

      * 存储费用：0.12 元/GB/月
      * 流量费用：全时段 0.40 元/GB
      * 请求费用：0.01 元/万次
    * 资源包定价

      * [存储包](https://ld246.com/forward?goto=https%3A%2F%2Fsw.ksyun.com%2Fpro%2Fcalc%2F%23%2Fcom%2F37443%2Fdoc%3A%7E%3Atext%3D55-%2C99%2C-500GB) ：最低一年 99 元 100GB
      * [流量包](https://ld246.com/forward?goto=https%3A%2F%2Fsw.ksyun.com%2Fpro%2Fcalc%2F%23%2Fcom%2F37443%2Fdoc%3A%7E%3Atext%3D2.2-%2C%25E4%25B8%258B%25E8%25A1%258C%25E6%25B5%2581%25E9%2587%258F%25E8%25B5%2584%25E6%25BA%2590%25E5%258C%2585%25E4%25BB%25B7%25E6%25A0%25BC%2C-%25EF%25BC%2588%25E5%258F%25AA%25E9%2580%2582%25E7%2594%25A8%25E4%25BA%258E)：最低一年 432 元，每月 100GB 下载流量

    ## 6. 百度云 BOS

    * 无免费额度，[按量计费模式](https://ld246.com/forward?goto=https%3A%2F%2Fcloud.baidu.com%2Fproduct-price%2Fbos.html)

      * 存储费用：0.119 元/GB/月
      * 流量费用：24:00-08: 00 (闲时): 0.25 元/GB；08: 00-24:00(忙时): 0.49 元/GB
      * 请求费用：0.01 元/万次
    * [资源包定价](https://ld246.com/forward?goto=https%3A%2F%2Fcloud.baidu.com%2Fproduct-price%2Fbos.html)

      * 存储包：最低一年 97.2 元 100GB
      * 流量包：最低一年 432 元，每月 100GB 下载流量

    ## 7. 京东云 OSS

    * 存储空间免费 10G，[按量计费模式](https://ld246.com/forward?goto=https%3A%2F%2Fdocs.jdcloud.com%2Fcn%2Fobject-storage-service%2Fprice-overview)

      * 存储费用：[10G 内免费](https://ld246.com/forward?goto=https%3A%2F%2Fdocs.jdcloud.com%2Fcn%2Fobject-storage-service%2Ffree-tier-for-oss)，超出 10G 后 0.128 元/GB/月
      * 流量费用：全时段 0.50 元/GB
      * 请求费用：50 万次内免费
    * [资源包定价](https://ld246.com/forward?goto=https%3A%2F%2Fdocs.jdcloud.com%2Fcn%2Fobject-storage-service%2Fresource-packages)：

      * 存储包：最低一年 50 元 50GB
      * 流量包：最低一年 24/46 元，每月 3.3/8.3GB 下载流量

    ## 8. 美团云 MSS

    * 无免费额度，[按量计费模式](https://ld246.com/forward?goto=https%3A%2F%2Fwww.mtyun.com%2Fdoc%2Fproducts%2Fstorage%2Fmss%2Fgou-mai-shuo-ming)

      * 存储费用：0.14 元/GB/月
      * 流量费用：全时段 0.29 元/GB
      * 请求费用：免费
    * 资源包定价：

      * 官方文档中没有资源包定价的信息

    ## 9. 滴滴云 OSS

    * 无免费额度，[按量计费模式](https://ld246.com/forward?goto=https%3A%2F%2Fhelp.didiyun.com%2Fstatic%2Fassets%2Fdocs%2FS3%25E4%25BA%25A7%25E5%2593%2581%25E6%2596%2587%25E6%25A1%25A3%2F02-%25E8%25B4%25AD%25E4%25B9%25B0%25E9%25A1%25BB%25E7%259F%25A5%2F%25E8%25AE%25A1%25E8%25B4%25B9%25E6%25A0%2587%25E5%2587%2586.html)

      * 存储费用：0.12 元/GB/月
      * 流量费用：全时段 0.50 元/GB
      * 请求费用：0.01 元/万次
    * 资源包定价：

      * 存储包：最低一年 96.48 元 100GB
      * 流量包：官方文档中没有流量包定价的信息

    ## 10. 青云 QingCloud

    * 有免费额度，[按量计费模式](https://ld246.com/forward?goto=https%3A%2F%2Fdocsv4.qingcloud.com%2Fuser_guide%2Fstorage%2Fobject_storage%2Fbilling%2Fprice%2F%23%3A%7E%3Atext%3D%25E4%25B8%258D%25E6%2594%25B6%25E5%258F%2596%25E8%25B4%25B9%25E7%2594%25A8%25E3%2580%2582-%2C%25E5%2585%258D%25E8%25B4%25B9%25E9%25A2%259D%25E5%25BA%25A6%2C-%25E6%25B3%25A8%25E5%2586%258C%25E6%2588%2590%25E5%258A%259F%25E5%25B9%25B6)

      * 存储费用：存储总量 10GB 内免费，超过后 0.147 元/GB/月
      * 流量费用：每月下载 1GB 内免费，超过后 0.45 元/GB/月
      * 请求费用：0.01 元/万次
    * 资源包定价

      * 官方文档未介绍

    ## 11. 群晖 C2 Object Storage

    这是看论坛帖子才发现的服务商，没错，就是那个 NAS 大厂群晖出品的 S3 对象存储服务

    每月免费 15G 存储空间和下载流量，超过 15G 之后没有按量付费，只能购买资源包，最低是 485 元/1TB/年，下载流量和存储空间相等

    选择台湾地区的话速度还行，直连速度介于国内服务商和 Cloudflare R2 之间

    具体同步教程参见：[思源笔记 S3 存储 synology - 链滴](https://ld246.com/article/1676827272258)；[思源笔记设置 Synology 免费 15G 对象存储 S3/C2 | D_SUPER BLOG](https://ld246.com/forward?goto=https%3A%2F%2Fwww.dsuper.xyz%2Farticle%2Fsiyuan_note_synology%3Futm_source%3Dld246.com)

    一些官方文档：[有关 C2 对象存储定价的常见问题](https://ld246.com/forward?goto=https%3A%2F%2Fkb.synology.com%2Fen-global%2FC2%2Ftutorial%2FC2_Object_Storage_pricing)；[定價 | C2 Object Storage (synology.com)](https://ld246.com/forward?goto=https%3A%2F%2Fc2.synology.com%2Fzh-tw%2Fpricing%2Fobject-storage%23c2-osp)

    ​**注意事项**​：群晖 C2 的占用空间会比其他 S3 厂商的占用空间更大，原因在于 [C2 对象存储上的最小数据单位为 128 KB。任何小于 128 KB 的对象仍按 128 KB 计算和计费](https://ld246.com/forward?goto=https%3A%2F%2Fkb.synology.com%2Fen-global%2FC2%2Ftutorial%2FC2_Object_Storage_pricing%23__next%3A%7E%3Atext%3DThe%2520minimum%2520unit%2520of%2520data%2520on%2520C2%2520Object%2520Storage%2520is%2520128%2520KB.%2520Any%2520object%2520smaller%2520than%2520128%2520KB%2520is%2520still%2520calculated%2520and%2520billed%2520as%2520128%2520KB)。而其他 S3 厂商是没有最小数据单位的。这也就是说一个 1kb 的空文档其他 S3 厂商就是算作 1kb，而群晖 C2 就会算成 128kb，直接翻了 128 倍，因此群晖的空间占用会大很多，具体大多少则取决于 repo 分块里面的零碎小块的多少

    ## 12. Cloudflare R2

    * [免费 10G 存储空间](https://ld246.com/forward?goto=https%3A%2F%2Fwww.cloudflare.com%2Fzh-cn%2Fproducts%2Fr2%2F%23%3A%7E%3Atext%3D%25E8%2581%2594%25E7%25B3%25BB%25E4%25B8%2593%25E5%25AE%25B6-%2CR2%2520%25E5%25AE%259A%25E4%25BB%25B7%2C-R2%2520%25E8%25AE%25A1%25E8%25B4%25B9)，超过 10G 之后是 0.015 美元/GB（约合 0.1 元人民币/GB），下载流量不管多少全免费
    * 直连速度比较玄学，时快时慢，时有时无。不过有梯子的话这是不错的选择

    ## 13. 网易云 NOS

    * **需要详细的**企业认证和企业对公账户信息，否则无法使用
    * [每月免费](https://ld246.com/forward?goto=https%3A%2F%2Fsf.163.com%2Fhelp%2Fdocuments%2F76809994847309824) 50G 存储空间；20G 下载流量；10 万次请求费用
