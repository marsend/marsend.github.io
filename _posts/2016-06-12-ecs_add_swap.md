---
layout: post
title:  "阿里云ecs centos 配置虚拟内存"
date:   2016-06-12 17:21:09 +0800
categories: server
tags: ["服务器"]
---
> 源于在ecs上跑node的react项目挂起时的解决方案

ecs上买了一个1g的云主机，在跑[react-starter-kit](https://github.com/kriasoft/react-starter-kit)项目，运行npm install时发现在解包过程中一直挂起...没有任何错误信息，后面发现是ecs的内存爆了- -！
<picture>
    <source srcset="/images/ecsaddswap1.webp" type="image/webp">
    <img src="/images/ecsaddswap1.png" alt="test">
</picture>
后面发现react npm install的所下载的依赖包快1g了...  
果断添加虚拟内存解决此问题
### 添加虚拟内存  
执行以下命令

    $ dd if=/dev/zero of=/var/swap bs=1024 count=65536
    $ mkswap /var/swap
    $ vi /etc/fstab

添加以下内容
<picture>
    <source srcset="{{site.IMG_PATH}}/ecsaddswap2.webp" type="image/webp">
    <img src="{{site.IMG_PATH}}/ecsaddswap2.png" alt="test">
</picture>
最后，检查下虚拟内存是否成功应用`$ free -m`
<picture>
    <source srcset="{{site.IMG_PATH}}/ecsaddswap3.webp" type="image/webp">
    <img src="{{site.IMG_PATH}}/ecsaddswap3.png" alt="test">
</picture>
此时，在react中npm install时就不会出现挂起的情况了，不过发现解压的过程没有纯粹使用内存时快，这也是意料中的事了...
