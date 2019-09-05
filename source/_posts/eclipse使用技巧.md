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

添加至 -vmargs 参数上方

#### eclipse在线安装反编译插件：

- Help --> Eclipse Marketplace
- 搜索 "Decompiler"，安装即可
![Decompiler](img/decoder.png)

#### eclipse集成dorado5插件：

dorado5最好使用jdk1.6 32位，与eclipse j2ee indigo版本兼容最好。其他eclipse版本貌似view编辑时按钮点击事件不生效。。。
现附上安装包链接（均为官方版本）：
- [jdk1.6 (包含64位和32位) 密码：xneq](https://pan.baidu.com/s/1nwLjSHN)
- [eclipse j2ee indigo 32位 密码：q4wx](https://pan.baidu.com/s/1smCUmYD)
- [eclipse j2ee indigo 64位 密码：p97a](https://pan.baidu.com/s/1bqIM0MV)
- [eclipse dorado5ide插件 密码：umpq](https://pan.baidu.com/s/1jJ0rqey)

#### 集成步骤（默认jdk环境和eclipse已正常安装）：
- 在eclipse安装目录下新建links目录，并在此目录下创建 com.bstek.dorado.link文件。
- 将eclipse dorado5ide插件下载后解压，并重组合并：
##### 解压后目录结构为：
![dorado5](img/dorado5_1.png)
##### 整合后目录结构为：
![dorado5](img/dorado5_2.png)
>整合是指：将aptana和dorado5文件夹下的features和plugins文件夹分别合并后保存在eclipse文件夹下
- 编辑eclipse目录下links文件夹内的com.bstek.dorado.link文件，文件内容为：
    path=E:\\plugins\\dorado5ide
- 至此，eclipse集成dorado5插件完成。启动eclipse
![dorado5](img/dorado5_3.png)
![dorado5](img/dorado5_4.png)
![dorado5](img/dorado5_5.png)
此时eclipse已可开发dorado5项目。
> 附dorado5 studio客户端：链接：https://pan.baidu.com/s/1c2Wbu72 密码：s31z





#### 开发工具问题：

- IDEA使用git做pull或push操作时，频繁弹出github登陆窗口，可在命令行或idea terminal（终端）输入命令：
> git config --global credential.helper store

之后的pull或push只需要再输入一次用户名密码就不用再反复输入了。
- 终端输入 命令：
> git config --global user.name "username"

可更改提交者的名称
