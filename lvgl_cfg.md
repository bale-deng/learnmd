# 在ubuntu上跑lvgl
---
拉取lvgl仓库
```bash

#  安装SDL2并验证
sudo apt update
sudo apt install libsdl2-dev libsdl2-image-dev libsdl2-ttf-dev
pkg-config --modversion --cflags --libs sdl2

#  检查是否有git
git --version
#  若没有git，请执行以下指令
#  sudo apt install git

#  创立文件夹，激活虚拟环境
mkdir ./lvglapp
cd ./lvglapp
python3.10 -m venv lvglenv

#  拉仓库
git clone https://github.com/lvgl/lv_port_linux.git
cd lv_port_linux
git submodule update --init --recursive

#  下面更改一下lv_conf.h

```