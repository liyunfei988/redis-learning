---
title: Redis 命令
date: 2025-03-21 11:53:01
tags:
---
Redis 命令用于在 redis 服务上执行操作。

要在 redis 服务上执行命令需要一个 redis 客户端。Redis 客户端在我们之前下载的的 redis 的安装包中。

### 语法
Redis 客户端的基本语法为：  
```text
$ redis-cli
```

### 实例
以下实例讲解了如何启动 redis 客户端：

启动 redis 客户端，打开终端并输入命令 redis-cli。该命令会连接本地的 redis 服务。

```text
$redis-cli
redis 127.0.0.1:6379>
redis 127.0.0.1:6379> PING
 
PONG
```

以上实例中我们连接到本地的 redis 服务并执行 PING 命令，该命令用于检测 redis 服务是否启动。


### 在远程服务上执行命令
如果需要在远程 redis 服务上执行命令，同样我们使用的也是 redis-cli 命令。

语法
```text
$ redis-cli -h host -p port -a password
```

### 实例
以下实例演示了如何连接到主机为 127.0.0.1，端口为 6379 ，密码为 mypass 的 redis 服务上。
```text
$redis-cli -h 127.0.0.1 -p 6379 -a "mypass"
redis 127.0.0.1:6379>
redis 127.0.0.1:6379> PING
 
PONG
```


### 检查redis-server是否启动
```text
$ ps -ef | grep redis
     2568147 2561694  0 11:46 pts/1    00:00:00 redis-cli
     2568577       1  0 11:51 ?        00:00:00 redis-server *:6379
     2568645 2566357  0 11:55 pts/0    00:00:00 grep redis
```
6379为redis-server运行的端口号


查看6379端口号的运行状态：LISTEN
```text
$ netstat -tuln | grep 6379
tcp        0      0 0.0.0.0:6379            0.0.0.0:*               LISTEN     
tcp6       0      0 :::6379                 :::*                    LISTEN   
```

### 关闭redis-server服务
关闭redis-server服务   
```text
sudo systemctl stop redis
```
关闭redis-server开机自启动   
```text
sudo systemctl disable redis
```