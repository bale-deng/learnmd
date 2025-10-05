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

```C
lv_conf.h
/* 启用 SDL 驱动 */
#define LV_USE_SDL              1

/* 禁用其他不相关的硬件驱动 */
#define LV_USE_LINUX_FBDEV      0
#define LV_USE_EVDEV            0
#define LV_USE_X11              0
/* ... 其他驱动也都应为 0 ... */

/* 设置推荐的色深 */
#define LV_COLOR_DEPTH          32

/* 操作系统接口（SDL 移植版通常不需要） */
#define LV_USE_OS               LV_OS_NONE

/* 在 PC 环境下，使用标准 C 库进行内存管理和文件操作 */
#define LV_USE_STDLIB_MALLOC    LV_STDLIB_CLIB
#define LV_USE_FS_STDIO         1
#if LV_USE_FS_STDIO
    #define LV_FS_STDIO_LETTER 'A'
#endif
```
*之后在终端当中输入以下指令：*
```bash

#  当前路径是在lv_port_linux下
mkdir ./build
cd ./build
cmake ..
make -j${nproc}

#  等待编译完沉，进行下面步骤
ls -l
#  看看是否有bin这个文件夹
cd ./bin
./lvglsim
```

这下就完成了基本的配置
