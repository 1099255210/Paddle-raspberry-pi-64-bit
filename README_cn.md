# Paddle-raspberry-pi-64-bit

树莓派 4B (64位) 上的 PaddlePaddle `.whl` 安装包

[English](./README.md) | 简体中文 

## 快速上手

安装要求：

硬件与系统： `Raspberry Pi 4B 64-bit(aarch64/armv8)`

Python版本： `Python=3.9`

下载 `.whl` 安装包 [Paddle2.4-Raspberry-pi-64bit](https://github.com/1099255210/Paddle-raspberry-pi-64-bit/releases/download/2.4/paddlepaddle-0.0.0-cp39-cp39-linux_aarch64.whl)

```shell
pip install paddlepaddle-0.0.0-cp39-cp39-linux_aarch64.whl
```

安装完成后检查是否安装成功：

```shell
python

>>> import paddle
>>> paddle.utils.run_check()
```

如果看到 `PaddlePaddle is installed successfully!`， 说明安装成功。

## 详细信息

编译这个安装包的系统如下：

```shell
aarch64
PRETTY_NAME="Debian GNU/Linux 11 (bullseye)"
NAME="Debian GNU/Linux"
VERSION_ID="11"
VERSION="11 (bullseye)"
VERSION_CODENAME=bullseye
ID=debian
HOME_URL="https://www.debian.org/"
SUPPORT_URL="https://www.debian.org/support"
BUG_REPORT_URL="https://bugs.debian.org/"
```

用下面这行命令查看你的操作系统：

```shell
uname -m && cat /etc/*release
```

查看你的 Python 版本：

```shell
python -c "import sys; print(sys.version)"
```

本安装包需要 Python=3.9

## 编译指南

树莓派 4B 64位 系统镜像：[下载链接](https://downloads.raspberrypi.org/raspios_arm64/images/raspios_arm64-2023-02-22/2023-02-21-raspios-bullseye-arm64.img.xz)

PaddlePaddle 编译流程基本参考 [飞桨官方源码编译指南](https://www.paddlepaddle.org.cn/install/quick?docurl=/documentation/docs/zh/install/compile/linux-compile.html)

对于 树莓派4B 64bit 而言，下面是可以参考的指南：

安装 CMAKE, protobuf, patchelf:

```shell
sudo apt install cmake patchelf
pip install protobuf
```

克隆 `PaddlePaddle` 仓库：

```shell
git clone https://github.com/PaddlePaddle/Paddle.git && cd Paddle 
```

切换到 `develop` 分支, 新建 `build` 目录：

```shell
git checkout develop && mkdir build && cd build
```

开始编译：

```shell
cmake .. -DPY_VERSION=3 -DPYTHON_EXECUTABLE=`which python3` -DWITH_ARM=ON -DWITH_GPU=OFF
ulimit -n 8192
make TARGET=ARMV8 -j$(nproc)
```

这里有一些需要注意的点：

- make 过程中可能会需要克隆一些仓库，如果速度特别慢可以考虑更换 git 代理。
- 多线程编译会导致一些问题，中途会报错，此时请切换到单线程（`make TARGET=ARMV8`）继续。
- 单线程编译到约 90% 以上时会报错，此时再切换到多线程编译，直到出错后再切换回单线程，可以进行至编译成功。
- 整个编译过程可能长达一整天，请留足时间。

如果在编译中遇到了其它问题，请参考以下流程：

1. 在 google 必应等平台搜索（适用于普遍问题）
2. 在 paddlepaddle 的[官方仓库的issues](https://github.com/PaddlePaddle/Paddle/issues)中寻找关键字。(可参考的关键词：`aarch64/armv8`)
3. 以上都无法寻找到答案，请在本仓库提出 `issue`，如果有我们碰到的问题可以帮助解答。