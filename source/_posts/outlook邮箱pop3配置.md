---
title: outlook建立邮箱
date: 2017-07-23 19:38:06
tags:
- outlook
categories: windows
---
使用windows自带的outlook建立邮箱需要配置POP3，配置方法如下：

- 在outlook邮箱设置里启用POP3；
- 接收邮件服务器配置：pop3-mail.outlook.com
- 发送邮件服务器配置：smtp-mail.outlook.com
- 其他设置 -->发送服务器 -->我的发送要求验证
- 其他设置 -->高级 -->接收服务器 995，勾选 此服务要求加密连接
- 发送服务器 --> 587 使用tls加密类型