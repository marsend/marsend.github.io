---
layout: post
title:  "Mac安装php配置phpstorm"
date:   2017-01-05 17:21:09 +0800
categories: php
tags: "php"
---
> 在OSX 10.11版本中，系统内置了php5.5,此版本不是配置齐全的版本。如在phpstorm中其php-cgi，所以就干脆重装一遍php。

## php安装方式  

[php.net](http://php.net/manual/zh/install.macosx.packages.php)提供如下的几种软件包安装方式  
1. [MacPorts](http://www.macports.org/)
2. [Liip](http://php-osx.liip.ch/)
3. [Fink](http://www.finkproject.org/)
4. [Homebrew](https://github.com/Homebrew/homebrew-php)  

### 下面我们用homebrew来示例安装php  
1. 安装[homebrew](http://brew.sh/index_zh-cn.html)    

    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

2. 安装php
首先得先设置下相关的homebrew php依赖

    $ brew tap homebrew/dupes

    $ brew tap homebrew/versions

    $ brew tap homebrew/homebrew-php
设置好依赖后，开始安装php  
    $ brew install php56  
其中版本根据自己需要指定...  
3. 配置phpsotrm  
![配置phpstorm](/images/configphpsotrm.gif)

成功跑出`Hello World`后，phpstorm的配置就完成，后面需要在添加php的扩展，只需再经过homebrew去安装就行了。
