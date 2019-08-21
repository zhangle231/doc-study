#gp安装

##准备

###关闭SElinux
```
# sestatus
SELinuxstatus: disabled
```

###关闭防火墙

```
[zl@localhost greenplumn]$ systemctl status firewalld
● firewalld.service - firewalld - dynamic firewall daemon
   Loaded: loaded (/usr/lib/systemd/system/firewalld.service; disabled; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:firewalld(1)

systemctl disable firewalld.service
systemctl stop firewalld.service
```

##设置OS参数

vim /etc/sysctl.conf 按文档修改对应参数。

sysctl -p 使参数生效，sysctl -a 查看当前参数


vim /etc/security/limits.conf 对应修改


ulimit -a 查看当前值

##Creating User Account

groupadd gpadmin
useradd gpadmin -g gpadmin
passwd gpadmin

##Installing the RPM Distribution

rpm -qilp greenplum.rpm #查看安装包中的文件

ln -s /data/greenplumn/data/ /usr/local/greenplum-db-5.20.1 #创建链接

rpm -Uvh greenplum.rpm #安装gp软件

##Configuring Greenplum on all Hosts

source /usr/local/greenplum-db/greenplum_path.sh #引入环境变理
'''
vim hostfile_exkeys

mdw
mdw-1
mdw-2
sdw1
sdw1-1
sdw1-2
'''

vim /etc/hosts
10.x.x.xx   sdw

su - gpadmin
source /data/greenplumn/data/greenplum_path.sh

[gpadmin@localhost ~]$ cat hostfile_gpinitsystem
sdw

gpinitsystem -c gpconfigs/gpinitsystem_config -h gpconfigs/hostfile_gpinitsystem

##密码锁了
[root@localhost ~]# pam_tally2 --user=gpadmin
Login           Failures Latest failure     From
gpadmin            12    08/15/19 16:45:36  10.5.0.31
[root@localhost ~]# pam_tally2 --user=gpadmin --reset
Login           Failures Latest failure     From
gpadmin            12    08/15/19 16:45:36  10.5.0.31

## 配置MASTER_DATA_DIRECTORY
MASTER_DATA_DIRECTORY=/data/greenplumn/master/gpseg-1/

pg_hba.conf
gpstop -u


