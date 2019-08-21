#Flasgger

##安装

###安装python3
```
#更新环境
yum update
yum -y groupinstall "Development tools"
yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel
#下载python
wget https://www.python.org/ftp/python/3.6.2/Python-3.6.2.tar.xz

#安装python3
tar -xvJf  Python-3.6.2.tar.xz
cd Python-3.6.2
./configure --prefix=/usr/local/python3
make && make install

ln -s /usr/local/python3/bin/python3 /usr/bin/python3
ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
```

###安装flasgger
```
pip3 install -U setuptools
pip3 install flasgger

pip3 install flask-restful
```

##写测试代码

```
from flask import Flask, jsonify
from flasgger import Swagger
from flask_restful import Api, Resource

app = Flask(__name__)
#swagger = Swagger(app, template=template)
api = Api(app)
swagger = Swagger(app)

class Username(Resource):
    def get(self, username):
       """
       这是一个测试函数
       测试函数
       ---
       parameters:
         - in: path
           name: username
           type: string
           required: true
           description: "用户名称"
       responses:
         200:
           description: "返回用户的相关信息"
           schema:
             id: User
             properties:
               username:
                 type: string
                 description: "用户的名称"
                 default: Steven Wilson
       """
       return {'username': username}, 200


api.add_resource(Username, '/username/<username>')

app.run(debug=True, host='192.168.137.3')
```

##执行脚本
 python3 colors.py
