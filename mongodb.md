# mongodb 安装使用

## 安装

```
#创建yum源

vim /etc/yum.repos.d/mongodb-org-4.2.repo

[mongodb-org-4.2]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/4.2/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-4.2.asc

#安装4个组件
sudo yum install -y mongodb-org
```

## 启动服务

```
#修改ulimit，以下是建议的值
limit fsize unlimited unlimited    # (file size)
limit cpu unlimited unlimited      # (cpu time)
limit as unlimited unlimited       # (virtual memory size)
limit memlock unlimited unlimited  # (locked-in-memory size)
limit nofile 64000 64000           # (open files)
limit nproc 64000 64000            # (processes/threads)

#修改配置文件，外网访问
vim /etc/mongod.conf
bindIp: 0.0.0.0 #这行修改为0.0.0.0

#启动服务
sudo service mongod start

#注册为服务
sudo chkconfig mongod on

#停止\重启
sudo service mongod stop
sudo service mongod restart

#卸载
sudo yum erase $(rpm -qa | grep mongodb-org)
sudo rm -r /var/log/mongodb
sudo rm -r /var/lib/mongo
```

## 使用

```
#进入shell
mongo

mongo --port 27017 #默认端口

db #显示db

use test #使用db

#创建一条数据
db.coll1.insertOne({x:1});

#查寻数据
db.coll1.find()

```

## 使用python操作mongodb

```
#安装包
pip install pymongo

#测试方法

#!/usr/bin/env python
# -*- coding:utf-8 -*-

from pymongo import MongoClient

conn = MongoClient('127.0.0.1', 27017)
db = conn.test #连接mydb数据库，没有则自动创建
my_set = db.coll1 #使用test_set集合，没有则自动创建

for i in my_set.find():
    print(i)

```
