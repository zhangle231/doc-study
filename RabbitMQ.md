# RabbitMQ安装与使用

## 安装

```
#安装erlang
#添加yum源
wget http://mirrors.sohu.com/fedora-epel/epel-release-latest-7.noarch.rpm
rpm -ivh epel-release-latest-7.noarch.rpm

wget https://packages.erlang-solutions.com/erlang-solutions-1.0-1.noarch.rpm
rpm -Uvh erlang-solutions-1.0-1.noarch.rpm

#安装
yum install erlang

以上方法不可用，版本太老了

#安装RabbitMQ
curl -s https://packagecloud.io/install/repositories/rabbitmq/erlang/script.rpm.sh | sudo bash

curl -s https://packagecloud.io/install/repositories/rabbitmq/rabbitmq-server/script.rpm.sh | sudo bash

yum install rabbitmq-server

#配置RabbitMQ

#开机自动启动
chkconfig rabbitmq-server on
#启协
/sbin/service rabbitmq-server start
/sbin/service rabbitmq-server stop
#启动ui
rabbitmq-plugins enable rabbitmq_management
#url
http://localhost:15672

#修改配置文件，允许远程访问
vim /etc/rabbitmq/rabbitmq.conf
listeners.tcp.default = 5673
loopback_users = none

#默认用户密码
guest/guest
```

# 安装celery
```
pip install celery


#启动任务和定时
celery -A proj worker -B

#定时任务样例
from celery import Celery
from celery.schedules import crontab

app = Celery()

@app.on_after_configure.connect
def setup_periodic_tasks(sender, **kwargs):
    # Calls test('hello') every 10 seconds.
    sender.add_periodic_task(10.0, test.s('hello'), name='add every 10')

    # Calls test('world') every 30 seconds
    sender.add_periodic_task(30.0, test.s('world'), expires=10)

    # Executes every Monday morning at 7:30 a.m.
    sender.add_periodic_task(
        crontab(hour=7, minute=30, day_of_week=1),
        test.s('Happy Mondays!'),
    )

@app.task
def test(arg):
    print(arg)


