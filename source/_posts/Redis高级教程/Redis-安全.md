---
title: Redis 安全
date: 2025-03-21 11:44:17
tags:
---
我们可以通过 redis 的配置文件设置密码参数，这样客户端连接到 redis 服务就需要密码验证，这样可以让你的 redis 服务更安全。

### 实例
我们可以通过以下命令查看是否设置了密码验证：  
```text
127.0.0.1:6379> CONFIG get requirepass
1) "requirepass"
2) ""
```
默认情况下 requirepass 参数是空的，这就意味着你无需通过密码验证就可以连接到 redis 服务。

你可以通过以下命令来修改该参数：   
```text
127.0.0.1:6379> CONFIG set requirepass "w3cschool.cc"
OK
127.0.0.1:6379> CONFIG get requirepass
1) "requirepass"
2) "w3cschool.cc"
```
设置密码后，客户端连接 redis 服务就需要密码验证，否则无法执行命令。  

### 语法
AUTH 命令基本语法格式如下：  
实例
```text
127.0.0.1:6379> set 1 zang 
(error) NOAUTH Authentication required.  //拒绝被访问，因为没有授权

127.0.0.1:6379> AUTH "w3cschool.cc"
OK
127.0.0.1:6379> SET mykey "Test value"
OK
127.0.0.1:6379> GET mykey
"Test value"
```

