---
title: Java连接虚拟机Oracle数据库的问题
date: 2017-10-11 14:46:06
tags:
categories: linux
---
最近在电脑上装了虚拟机，为的是在虚拟机上安装Oracle数据库，Oracle实在太占内存，配置低的电脑装个Oracle几乎就瘫了，没办法，搞个虚拟机玩玩。我虚拟机用的是xp系统，顺便怀念下经典。装好Oracle之后，虚拟机使用pl/sql developer可以连接，但是物理机Java连接却始终报如下的一个错误：

    ### Error updating database. Cause: org.springframework.jdbc.CannotGetJdbcConnectionException: Could not get JDBC Connection; nested exception is org.apache.commons.dbcp.SQLNestedException: Cannot create PoolableConnectionFactory (Io 异常: The Network Adapter could not establish the connection)
    ### Cause: org.springframework.jdbc.CannotGetJdbcConnectionException: Could not get JDBC Connection; nested exception is org.apache.commons.dbcp.SQLNestedException: Cannot create PoolableConnectionFactory (Io 异常: The Network Adapter could not establish the connection), mergedContextConfiguration = [MergedContextConfiguration@578f7a8 testClass = UserTest, locations = '{classpath*:/META-INF/spring/spring-*.xml}', classes = '{}', contextInitializerClasses = '[]', activeProfiles = '{}', contextLoader = 'org.springframework.test.context.support.DelegatingSmartContextLoader', parent = [null]]], class dirties context [false], class mode [null], method dirties context [false].

网上搜罗各种解决办法，终于解决了。话不多说：
- cmd命令行输入hostname查看主机名并记录主机名，如UAFDHGJK；
- cmd命令行输入ipconfig查看IP地址，如192.168.0.123；
- 修改C:\WINDOWS\system32\drivers\etc目录下hosts文件，在hosts文件最后一行添加   192.168.0.123    UAFDHGJK
- 修改Oracle安装目录D:\oracle\softwarelocation\NETWORK\ADMIN下的监听文件listener.ora

		SID_LIST_LISTENER =
		(SID_LIST =
		(SID_DESC =
		  (SID_NAME = CLRExtProc)
		  (ORACLE_HOME = D:\oracle\softwarelocation)
		  (PROGRAM = extproc)
		  (ENVS = "EXTPROC_DLLS=ONLY:D:\oracle\softwarelocation\bin\oraclr11.dll")
		)
	  )
		LISTENER =
	  (DESCRIPTION_LIST =
		(DESCRIPTION =
		  (ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC1521))
		  (ADDRESS = (PROTOCOL = TCP)(HOST = 这里改为主机名)(PORT = 1521))
		)
	  )
		ADR_BASE_LISTENER = D:\oracle\basemenu

- 修改Oracle安装目录D:\oracle\softwarelocation\NETWORK\ADMIN下的监听文件tnsnames.ora

    	ORACLE =
    	(DESCRIPTION =
        (ADDRESS = (PROTOCOL = TCP)(HOST = 这里改为主机名)(PORT = 1521))
        (CONNECT_DATA =
        (SERVER = DEDICATED)
        (SERVICE_NAME = oracle)
        )
		)
		LISTENER_ORACLE = (ADDRESS = (PROTOCOL = TCP)(HOST = 这里改为主机名)(PORT = 1521))
		ORACLR_CONNECTION_DATA =
		(DESCRIPTION =
        (ADDRESS_LIST =
        (ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC1521))
        )
        (CONNECT_DATA =
        (SID = CLRExtProc)
        (PRESENTATION = RO)
        )
    	)

- 重启tnslsnr。打开cmd输入命令：
> lsnrctl stop  
> lsnrctl start
> lsnrctl stat
- cmd输入命令：
> lsnrctl stat

查看Oracle监听数据已经改为配置的IP地址啦！
此时就可以通过正常Java连接数据库的方式连接虚拟机Oracle数据库了。