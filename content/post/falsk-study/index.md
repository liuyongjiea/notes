---
title: flask
description: flask的学习日志
date: 2023-12-29
slug: test-chinese
image: helena-hertz-wWZzXlDpMog-unsplash.jpg
draft: false
categories:

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




