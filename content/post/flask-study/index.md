---
title: flask
description: flask的学习日志
date: 2023-12-29
slug: study-flask
image: flask-horizontal.jpg

---


## Mac-配置python环境变量&安装pipenv

```shell
# 在终端输入，得到python3的路径，下称路径为a,b
which python3
which pip3
# 配置环境变量
vim ~/.bash_profile
# 加入参数
export PATH=$PATH:a
export PATH=$PATH:b
alias python="a"
alias pip="b"
# 应用配置
source ~/.bash_profile
pip install pipenv
```

## pipenv

```shell
# 切换到项目路径，创建虚拟环境，会自动根据项目文件中的Pipfile文件自动安装依赖包
pipenv install
	# 若想在项目目录创建虚拟环境文件夹，需配置环境变量 `PIPENV_VENV_IN_PROJECT=1`
# 切换到项目，启动环境
pipenv shell
# 查看环境依赖,等同于pip list
pipenv graph 
# 使用pipenv安装依赖时不需要启动环境
```

### 安装flask以及其依赖包

```python
pipenv install flask
"""
jinja2       模版渲染引擎
MarkupSafe   html字符转义工具
werkzeug     处理请求与响应
click        命令行工具
itsdangerous 提供各种加密签名功能
"""
```

######  实例

```python
from falks import Falks
app = Flask(__name__)
```

## 注册路由（route）

客户端和服务器上的flask程序的交互：

1. 输入URl访问
2. Flask接受请求并分析
3. 为URl找到对应的处理函数
4. 执行函数并生成响应，返回浏览器
5. 浏览器接受响应

💠 上述过程大部分由flask完成，只需为函数附加app.route()装饰器，并传入URL规则作为参数，该过程作为注册路由，路由负责管理URL和函数之间的映射，该函数称为视图函数

## flask装饰器

```python
@app.route()
	# 必须以“/”开始，此方式为硬编码
  # 一个函数可以有多个route装饰器,且可以使用变量，如<name>
  	# 当使用变量时，用户访问的URl中没有添加变量，如设置url变量“/name/<age>”，用户访问“/name”，就会报404错误。因此需要设置默认值，即
    	@app.route("/name", defaults={"age": "15"})
			@app.route("/name/<age>")
			def name(age):
    			return f"你好，{age}"
      # 也可以为
			@app.route("/name/<age>")
			def name(age=15):
    			return f"你好，{age}"
url_for
	# 软编码
```

## flask的环境变量和运行机制

💠 app.run()方法现在已不推荐使用，建议使用flask run

```shell
# flask run会自动在当前目录寻找app.py和wsgi.py模块或环境变量FLASK_APP对应的值，并从中寻找app或application的程序实例
	# 修改FLASK_APP的值
	export FLASK_APP = new_name # Linux/Mac
	set FLASK_APP=hello # Windows
	# 若安装了python-dotenv，还会自动成.flaskenv和.env文件中加载环境变量
		# 加载变量优先级：“手动设置的环境变量>.env中设置的环境变量>.flaskenv设置的环境变量”
		# .flaskenv存储与flask的变量，.env存储敏感信息，除非是私有项目，否则绝不能上传到github上（可在.gitignore文件中设置）
flask run --host=0.0.0.0 --port 8080 # host使服务对外可见，同一个局域网可访问，若更多人可以访问，可使用ngrok或localtunnel等内网穿透/端口转发工具，或者租用公网
	# 也可用FLASK_RUN_HOST和FLASK_RUN_PORT设置host和post

# 设置运行环境
	# 根据运行环境不同，flask的行为和设置是不同的，默认为production环境，可在.flaskenv文件中设置FLASK_ENV=development。此时所有支持开发的特性都会被开启
	
# Werkzeug提供的调试器非常强大，呈现详细的错误追踪信息，且点击右侧的命令行图标并输入PIN码后，可以运行python代码进行调试。当对代码进行修改后，重载器检测到文本变动后，会重新启动开发服务器。
	# 因为Werkzeug内置的stat重载器耗电严重且准确性一般，所以会安装watchdog
		# 因为watchdog只会在开发时使用，因此可以在安装时使用“--dev”将其声明为开发依赖
		
# flask的配置变量通过app.config属性进行设置，该属性实际上为一个字典
	# 添加配置变量类似在字典中添加键值对
		# 键必须全部为大写或下划线
```





