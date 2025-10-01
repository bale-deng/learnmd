# 使用Miniconda进行包管理
---

__* miniconda的用法与普通虚拟环境的区别__


```bash
#  下载miniconda安装包
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

#  安装miniconda(一路确认加enter加yes)
bash Miniconda3-latest-Linux-x86_64.sh

#  conda环境查看
conda env list

#  conda查看已经安装的包
conda list
```
__这个时候关闭当前终端开启多一个终端__
```bash
#  确认是否成功安装conda
conda --version

#  创建conda环境，可以在特定路径下创建
conda create --name condaEnv python=3.10

#  激活conda环境
conda activate condaEnv

#  在conda虚拟环境下安装需要的包
conda install numpy pandas matplotlib

#  关闭虚拟环境
conda deactivate condaEnv
```