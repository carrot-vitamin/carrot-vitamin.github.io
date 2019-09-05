---
title: eclipse使用技巧
date: 2017-09-15 19:43:04
tags:
- eclipse
- svn
- git
categories: 开发工具
---
#### eclipse在线安装svn插件：

- 菜单 —> Help —> Install New Software
- 进入安装窗体后，点击安装窗体的Add按钮，然后在弹出的窗体中输入插件安装地址：
> [subversion 1.6.x客户端](http://subclipse.tigris.org/update_1.6.x)
> [subversion 1.7.x客户端](http://subclipse.tigris.org/update_1.8.x)
> [subversion 1.8.x客户端](http://subclipse.tigris.org/update_1.10.x/)
> [目前最高版本的SVN插件(截止到2017年1月20日)](http://subclipse.tigris.org/update_1.12.x/)
- 在eclipse目录下修改eclipse.ini文件来指定eclipse启动JDK路径：
> -vm
> C:/Program Files/Java/jdk1.7/jdk1.7.0_51/bin/javaw.exe
> 添加至 -vmargs 参数上方

#### eclipse在线安装反编译插件：

- Help --> Eclipse Marketplace
- 搜索 "Decompiler"，安装即可
![Decompiler](https://images2018.cnblogs.com/blog/1160920/201806/1160920-20180625110400786-1103606120.png)


#### 开发工具问题：

- IDEA使用git做pull或push操作时，频繁弹出github登陆窗口，可在命令行或idea terminal（终端）输入命令：

> git config --global credential.helper store

之后的pull或push只需要再输入一次用户名密码就不用再反复输入了。

- 终端输入 命令：

> git config --global user.name "username"

可更改提交者的名称
