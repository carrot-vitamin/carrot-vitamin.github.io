---
title: SQL命令
date: 2017-06-15 11:43:04
tags:
- oracle
- mysql
categories: 数据库
---

select 字段名 from 表名 group by 字段名（或是多个字段名，中间用逗号隔开） having count(*)>1；查询表中某一（某几个）字段内的重复数据

#### Oracle：
表名：person

列名：pid,name,interest,birth,sex

- N条数据，name字段like多个关键字查询：
查询名字中带“花”或“明”或“刚”的数据
select * from person where regexp_like(name, '花|明|刚');
- N条数据，按照interest分类，选出每组数据中birth最大的数据
select * from (select p.*,row_number() over (partition by interest order by birth desc) r from person p) where r=1;
- 将查询结果的枚举值转化为对应的文字描述
select pid,name,sex,decode(sex,'0','女','1','男','其他') as 性别,interest,birth from person;
注释：将查询的列sex里的值'0'转化为'女'，'1'转化为'男'显示到查询结果中。
