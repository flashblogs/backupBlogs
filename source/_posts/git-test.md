---
title: Git的一些练习总结
comments: true
keywords: "生命在于折腾，Life is a struggle!"
description: 记录生活点滴，成长之路
reward: false
date: 2017-01-17 11:44:25
tags:
    - Git
categories: 编程
---

![git版本控制](http://img.mukewang.com/55fb826f00017e2d06030263.jpg)

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=5119519&auto=0&height=66"></iframe>

## 容易混淆的提示(windows下面)

> 1. Clone、Pull一个远程Git库，不需要密码
> 2. Push是需要密码的
> 3. 可以通过配置，Push 到多个远程Git代码托管平台
> 4. 同一台电脑，只能保留一个Git平台的帐号密码 ( *也就是说你可以同时push到 `github` 、 `oschina` 、`coding` ,但是，你不能同时push到两个 `github`的库...* )
> 5. 当你push的时候，如果当前设备没有保存你push的托管平台帐号密码，会提示你输入正确的 `登录名` 和 `密码`
> 6. 如果刚push了代码到 `url:github1`,切换到另外一个项目，想push代码到 `url:github2`,这个时候，
你得通过 **控制面板 -> 用户 -> 凭据管理器 -> 普通凭据** 找到已经保存的 `url:github1` 凭据并删除，再次push `url:github2` 将会提示你重新输入 帐号密码
(*如果不切换账户密码，`push`会失败，提示403，库不存在、没授权 等信息*)

## Git同时提交多个远程代码托管平台

* push 一个远程库

```
git remote add origin <url>
```

* push 多个远程库

1. 增加第一个地址

```
git remote add origin <url1>
```

2. 增加第二个……第N个地址

```
git remote set-url --add origin <url2>
……
git remote set-url --add origin <urlN>
```

*重复向同一个远程仓库名字添加需要 `set-url --origin` 参数。 `origin` 远程库*

3. 一次push到多个库

```
git push origin master
```

### git push 到多个远程库分析

* 分析配置文件

你每执行一次git remote set-url --add origin 就会增加一行，

在操作完上面的添加命令后，如果我们打开.git/config文件,我们可以看到这样的配置:

```
[remote "origin"]
	url = <url1>
	fetch = +refs/heads/*:refs/remotes/origin/*
	url =<url2>
[branch "master"]
	remote = origin
	merge = refs/heads/master
```

使用git push origin master时，你可以push到origin的多个url地址，
但是使用 git pull时，只能拉取origin里的一个url地址(即fetch-url)，这个fetch-url默认为 你添加的到origin的第一个地址 `<url1>`，
如果你想更改，只需要更改config文件里，那几个url的顺序即可，fetch-url会直接对应排行第一的那个url连接。

* 手动修改 `.git config` 文件

如上，我们不一定非要用 `git 命令` 去执行添加多个url，也可以直接打开config，手动修改、添加 url 来操作：

```
[remote "origin"]
	url = <url1>
	fetch = +refs/heads/*:refs/remotes/origin/*
	url =<url2>
    	url =<url……N>
[branch "master"]
	remote = origin
	merge = refs/heads/master
```

# 附

![Git常用命令速查](http://static.oschina.net/uploads/img/201412/07180843_cbKA.jpg)



{% blockquote 段水流, 大师兄 %}
先大概写这么些吧，以后慢慢再补充
{% endblockquote %}

THE END.










