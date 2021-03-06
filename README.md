# Shadowsocks
在Ubuntu16.04上搭建Shadowsocks的笔记

### 准备工作
首先买一个VPS，安装Ubuntu16.04，为了操作方便，需要在VPS上安装 openssh-server
> apt-get install openssh-server

### 启动ssh服务
> /etc/init.d/ssh start

### 可能遇到的问题
+ ssh root@your-server-ip 时候报 : ECDSA host key for 172.106.32.109 has changed and you have requested strict checking.
Host key verification failed.
解决方式：删除 客户机~/.ssh/know_hosts 然后重新登录

+ ssh root@your-server-ip 时候报 : Permission Denied
解决方法：
> sudo vi /etc/ssh/sshd_config
> 找到：PermitRootLogin prohibit-password禁用
> 添加：PermitRootLogin yes

### 安装Shadowsocks
> apt-get install shadowsocks

### 配置
> 修改/etc/shadowsocks/config.json

### 配置多用户时候可能出错
> ERROR: password not specified

解决方法：
配置多多用户时候不要删除『password』

### 启动ssserver
> ssserver start
> 为了可以把启动命令放到/etc/rc.local 中
