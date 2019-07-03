# Centos 7安装软件

## tmux
```shell
yum install -y tmux

# 使用
# 新建会话
tmux new -s "name"
# 重新回到会话
tmux attach
# 快捷键
Ctrl b+d # 脱离当前会话,暂时返回shell
```

## Redis
```shell
yum install epel-release # 下载epel库
yum install -y redis
# 启动redis
service redis start
# 停止redis
service redis stop
# 查看redis运行状态
service redis status
# 查看redis进程
ps -ef | grep redis


# 开启6379
firewall-cmd --zone=public --add-port=6379/tcp --permanent
# 开启6380
firewall-cmd --zone=public --add-port=6380/tcp --permanent
# 重新载入
firewall-cmd --reload
# 查看
firewall-cmd --zone= public --query-port=6379/tcp
# centos 7下执行
systemctl restart firewalld

# 开机自动启动
chkconfig redis on
# 配置文件位置：/etc/redis.conf
vi /etc/redis.conf
# 找到 bind 127.0.0.1 将其注释
# 找到 protected-mode yes 将其改为
protected-mode no
```
## Mariadb
```shell
yum -y install mariadb mariadb-server
rpm -qa | grep mariadb #查看安装的mariadb数据库软件包
systemctl start mariadb
mysql_secure_installation # 设置密码等
cd /etc/my.cnf.d
vi server.cnf
# 在[mysqld]下添加:
init_connect='SET collation_connection = utf8_unicode_ci' 
init_connect='SET NAMES utf8' 
character-set-server=utf8 
collation-server=utf8_unicode_ci 
skip-character-set-client-handshake
#####################
vi client.cnf
# 在[client]中添加
default-character-set=utf8
# 在文件/etc/my.cnf.d/mysql-clients.cnf
default-character-set=utf8

systemctl restart mariadb

# 创建用户命令
create user username@localhost identified by 'password';

# 授予外网登陆权限 
grant all privileges on *.* to username@'%' identified by 'password';

# 授予权限并且可以授权
grant all privileges on *.* to username@'hostname' identified by 'password' with grant option;

# 查询各Schema和Table占用的空间:
use information_schema;
select table_schema,round(sum(DATA_LENGTH/1024/1024),2) as datasize  from tables group by table_schema;
```


