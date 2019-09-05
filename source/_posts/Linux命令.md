---
title: Linux命令
date: 2018-05-15 16:43:06
tags:
categories: linux
---

select 字段名 from 表名 group by 字段名（或是多个字段名，中间用逗号隔开） having count(*)>1；查询表中某一（某几个）字段内的重复数据

#### 常用linux命令：

`tailf 文件名` 追踪文件最新内容
`tail -f 文件名 | perl -pe 's/(要追踪的关键字)/\e[1;31m$1\e[0m/g'` 追踪的关键字出现会高亮显示
`scp root@172.16.01.02:/temp/paygate.war ./` 拷贝远程机文件至当前目录下
`ps -ef|grep tomcat` 查看tomcat进程
`kill -9 进程号` 杀掉tomcat进程
`tar -cvf filename.tar file` 将file文件压缩为filename.tar文件
`tar -xvf filename.tar` 解压filename.tar
`rm -fr filename` 删除文件
`cp /temp/paygate.war ./` 拷贝本地文件至当前目录下

#### 后台启动jar包命令：

> nohup java -jar XXX.jar >out.txt &

out.txt将command的输出重定向到out.txt文件，即输出内容不打印到屏幕上，而是输出到out.txt文件中。
关闭该进程：kill -9 进程号