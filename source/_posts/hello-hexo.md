---
title: Hexo初体验
comments: true
keywords: 生命在于折腾，Life is a struggle!
description: 记录生活点滴，成长之路
date: 2017-01-05 17:03:44
tags:
    - Hexo
categories:
---

![hexo与github更配哦](/assets/blog/img/hexo.png)

# 说明

此文主要记录本人在Hexo体验中的关键操作，如：指令、注意的地方，并非完整文档。（完整文档将在文末提出）

# 环境要求

* Node.js

用以安装、编译Hexo项目，生产静态化站点

* Git

项目版本控制，以及Hexo项目、主题代码更新升级。 **安装 Git Bash Here 命令行工具**

* GitHub

注册帐号，代码托管平台，以及博客部署的 GitHub Pages 站点空间

# 常用指令

### 首次安装

* 安装Hexo

```
npm install hexo-cli -g
```

* 初始化Hexo项目

```
hexo init
```

* 安装项目依赖和插件

```
npm install
```

* 启动服务器本地预览（默认地址：``http://localhost:4000``）

```
hexo s
```

### 主题&文章

* 下载主题，复制到Hexo项目的 ``themes`` 文件夹

```
git clone https://github.com/wuchong/jacman.git themes/jacman
```
*下载完主题，如果要启用该主题，需要修改 项目 目录下的 ``_config.yml`` 文件中的 ``theme`` 属性值，对应上面 就是 ``jacman``*

* 更新主题

```
cd themes/jacman
git pull origin master
```

*1.先切换到要更新的主题下面 2.备份原来主题目录下的 ``_config.yml`` 3.pull最新版本主题*

* 写一篇文章

```
hexo new [layout] <title>
```

*[layout] 缺省时默认是post，如：`hexo new "My New Post"`*

### 部署

* 生成静态化

```
hexo g
```

*生成的文件，将全部在 根目录下的 `public` 文件夹*

* 启动服务器本地预览（默认地址：``http://localhost:4000``）

```
hexo s

hexo s -p 4001
```
*多个站点的时候，需要配置不同的服务器端口*

* 发布到Git空间

```
hexo d
```

*本地查看无误后，将生成的文件发布到Git等平台。**这个需要安装 `deploy` 插件，以及配置根目录下 `_config.yml` 文件***

### 推荐插件

* 项目静态页面部署到GitHub、GitCafe等

```
npm install hexo-deployer-git --save
```

* 生成RSS订阅

```
npm install hexo-generator-feed --save
```

*依然要配置 根目录下 `_config.yml` 的 `feed` 属性*


* 生成SEO用的站点地图


```
npm install hexo-generator-sitemap --save
```

*依然要配置 根目录下 `_config.yml` 的 `sitemap` 属性*


# 参考链接

[GitHub](https://www.github.com/)

[Hexo官方中文文档](https://hexo.io/zh-cn/docs/)

[民间教程](http://www.isetsuna.com/categories/Hexo/)

End.  二〇一七年一月五日