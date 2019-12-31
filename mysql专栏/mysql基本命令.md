# 一、常用命令
**登录**
```
mysql -h 'ip' -u 'user' -p
```
**退出**
```
exit 或者 quit  或者 \q 
```
**常用命令**  
显示所有数据库
```
show databases; 
```
使用数据库
```
use '数据库名称';
```
显示当前连接的数据库
```
select  database();
```
显示当前服务器版本
```
select version();
```
显示当前日期
```
select now();
```
显示当前用户名
```
select user();
```
显示所有表
```
show tables;
```

# 二、混合语句
算出这个列上有多少个不同的值
```
select count(distinct email) as L from SUser;
```
