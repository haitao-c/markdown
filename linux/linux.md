# Linux常用命令

## 系统相关
### 设置时间
```shell
1. 查看时间和日期
命令 ： "date"

2. yum install -y ntpdate
 ntpdate time.nist.gov同步网络时间

3. 将当前时间和日期写入BIOS，避免重启后失效
命令 ： "hwclock -w"
```

### 设置系统名
```shell
vi /etc/sysconfig/network
HOSTNAME=haitaoc-svr
:wq

sudo hostnamectl set-hostname haitaoc-svr

vi /etc/hosts
127.0.0.1    haitaoc-svr
```