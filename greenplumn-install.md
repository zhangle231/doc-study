#gp��װ

##׼��

###�ر�SElinux
```
# sestatus
SELinuxstatus: disabled
```

###�رշ���ǽ

```
[zl@localhost greenplumn]$ systemctl status firewalld
�� firewalld.service - firewalld - dynamic firewall daemon
   Loaded: loaded (/usr/lib/systemd/system/firewalld.service; disabled; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:firewalld(1)

systemctl disable firewalld.service
systemctl stop firewalld.service
```

##����OS����

vim /etc/sysctl.conf ���ĵ��޸Ķ�Ӧ������

sysctl -p ʹ������Ч��sysctl -a �鿴��ǰ����


vim /etc/security/limits.conf ��Ӧ�޸�


ulimit -a �鿴��ǰֵ

##Creating User Account

groupadd gpadmin
useradd gpadmin -g gpadmin
passwd gpadmin

##Installing the RPM Distribution

rpm -qilp greenplum.rpm #�鿴��װ���е��ļ�

ln -s /data/greenplumn/data/ /usr/local/greenplum-db-5.20.1 #��������

rpm -Uvh greenplum.rpm #��װgp���

##Configuring Greenplum on all Hosts

source /usr/local/greenplum-db/greenplum_path.sh #���뻷������
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

##��������
[root@localhost ~]# pam_tally2 --user=gpadmin
Login           Failures Latest failure     From
gpadmin            12    08/15/19 16:45:36  10.5.0.31
[root@localhost ~]# pam_tally2 --user=gpadmin --reset
Login           Failures Latest failure     From
gpadmin            12    08/15/19 16:45:36  10.5.0.31

## ����MASTER_DATA_DIRECTORY
MASTER_DATA_DIRECTORY=/data/greenplumn/master/gpseg-1/

pg_hba.conf
gpstop -u


