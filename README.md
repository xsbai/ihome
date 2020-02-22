# Flask-爱家租房网项目

传智播客Python教程所学习的项目,该项目按照爱家租房网开发的实际上线项目,实现所有基本功能,采用前后端分离的方式进行开发

### [项目详细介绍目录](https://github.com/yuanwenq/iHome-python/blob/master/SUMMARY.md)

### 技术栈
- [x] python
- [x] flask
- [x] mysql
- [x] redis
- [x] celery

### 目标功能
- [x] 功能模块
    - [x] 首页
    - [x] 注册
    - [x] 登录
    - [x] 短信验证
    - [x] 用户退出
    - [x] 个人中心
    - [x] 实名认证
    - [x] 房屋列表
    - [x] 房屋管理
    - [x] 房屋详情
    - [x] 城区信息
    - [x] 发布房源
    - [x] 订单
    - [x] 订单支付

### 项目部署流程：

1. 阅读项目目录。

2. 创建虚拟环境、安装项目依赖：

   pip install -r requirements.txt

3. 注册[容联云通讯](www.yuntongxun.com)，在utils文件夹下的sms.py文件里修改配置。

4. 注册[七牛云](www.qiniu.com) ，在utils文件夹下的image_storage.py文件里修改配置信息，在constants.py文件里修改七牛的空间外链域名。

5. 在mysql数据库中创建数据库名称，在config文件里 SQLALCHEMY_DATABASE_URI 修改数据库名称。

6. 创建表：

   python manage.py db init
   python manage.py db migrate
   python manage.py db upgrade

7. 把areas_facility.sql文件的insert语句插入数据库中。



### 项目目录文档说明：
```
|-- /ihome                                  # 项目主要文件
|   |-- __init__.py
|   |-- /api_1_0                            # 视图函数文件
|   |   |-- __init__.py                     
|   |   |-- demo.py
|   |   |-- houses.py                       # 房屋相关API
|   |   |-- keys                            # 支付宝秘钥存放文件夹
|   |   |-- orders.py                       # 订单相关API-保存订单-查询订单信息-接单-拒单-订单评论信息
|   |   |-- passport.py                     # 用户相关API-注册-登录-验证
|   |   |-- pay.py                          # 支付相关API-支付宝支付
|   |   |-- profile.py                      # 用户相关信息修改API-头像-名字-个人信息-实名认证
|   |   `-- verify_code.py                  # 验证相关API-图片验证-短信验证
|   |-- constants.py                        # 项目使用的常量
|   |-- /libs                               # 第三方文件存放文件夹-短信验证(容联云)
|   |   |-- __init__.py
|   |   `-- /yuntongxun
|   |       |-- CCPRestSDK.py               # 容联云PythonSDK
|   |       |-- __init__.py 
|   |       |-- sms.py                      # 容联云配置文件和封装的方法
|   |       `-- xmltojson.py
|   |-- models.py                           # ORM-模型类
|   |-- static                              # 静态文件存放目录
|   |-- /tasks                              # celery-分布式任务队列
|   |   |-- __init__.py
|   |   |-- config.py
|   |   |-- main.py
|   |   |-- /sms
|   |   |   |-- __init__.py
|   |   |   |-- tasks.py
|   |   `-- task_sms.py
|   |-- /utils                               # 工具类文件夹
|   |   |-- __init__.py
|   |   |-- /captcha                         # 图片验证相关代码
|   |   |   |-- __init__.py
|   |   |   |-- captcha.py
|   |   |   `-- /fonts
|   |   |       |-- Arial.ttf
|   |   |       |-- Georgia.ttf
|   |   |       `-- actionj.ttf
|   |   |-- commons.py                      # 公共类方法-定义正则转换器-定义的验证登录状态的装饰器
|   |   |-- image_storrage.py               # 七牛云图片上传相关代码
|   |   `-- response_code.py                # 项目定义返回的规范文件
|   |-- views.py                            
|   `-- web_html.py                         # html返回文件操作
|-- /logs                                   # 项目日志
|-- config.py                               # 项目配置文件
|-- manage.py                               # 项目启动文件
|-- requirement.txt                         # 项目依赖配置文件
`-- README.md                               # 项目启动文件
```