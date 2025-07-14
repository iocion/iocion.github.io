!!! info "py使用小技巧"

​	使用手册

#### 1.python虚拟环境

虚拟环境包括conda , venv 

包管理器 pip , uv  

```bash
传统流程
1.创建venv虚拟环境文件夹
python -m venv venv
2.激活虚拟环境
source .venv/bin/activate #linux or unix 
.venv/Scripts/activate # windows
requirements.txt # 会导致直接依赖和简介依赖混乱
3.添加依赖 # python官方提供了pyproject.toml文件
edit pyproject.toml
```

下面是一个pyproject.toml文件示例，使用传统流程需要手动创建

```toml
[project]
name = "project name"
version = "0.0.1"
[dependencies] = [
	"flask >= 3.1.1"
]
```

```bash
4.下载相关依赖
pip install -e .
```

##### 1.1使用uv包管理工具

```bash
pip install uv

# 添加相关依赖
uv add [dependencies]

# 拿到一个有相关pyproject.toml文件的项目时
uv sync 
# 自动读取文件并安装好对应的文件
```

```bash
1.传统情况下使用uv管理工具
# source .venv/bin/activate 
# python main.py
2.使用uv后
uv run main.py
```

#### 2.使用uv创建项目

```bash
uv python list # 查看可以使用的python版本

uv init -p 3.11 # 可以选择init的python版本

# 使用vscode选择创建的虚拟环境名称
[project]
name = "(test)" # 通常就是创建的项目名称
```

