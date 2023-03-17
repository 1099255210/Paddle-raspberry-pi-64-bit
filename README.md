# Paddle-raspberry-pi-64-bit
Raspberry Pi 4B Paddle installation wheels (64-bit).

树莓派 4B (64位) 上的 PaddlePaddle `.whl` 安装包

## Quick Start 快速上手

Requirements 安装要求

Raspberry Pi 4B (aarch64)

Python=3.9

Download the `.whl` installer. 下载 `.whl` 安装包。

[Paddle2.4-Raspberry-pi-64bit](https://github.com/1099255210/Paddle-raspberry-pi-64-bit/releases/download/2.4/paddlepaddle-0.0.0-cp39-cp39-linux_aarch64.whl)

```shell
pip install paddlepaddle-0.0.0-cp39-cp39-linux_aarch64.whl
```

After this, check if the installation is successful: 安装完成后检查是否安装成功：

```shell
python

>>> import paddle
>>> paddle.utils.run_check()
```

If you see `PaddlePaddle is installed successfully!`, then you are ready to go. 

如果看到 `PaddlePaddle is installed successfully!`， 说明安装成功。

## Detailed Information 详细信息

This installer is compiled on the system below: 编译这个安装包的系统如下：

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

Use this command to check your system: 用下面这行命令查看你的操作系统：

```shell
uname -m && cat /etc/*release
```

Check your Python version: 查看你的 Python 版本：

```shell
python -c "import sys; print(sys.version)"
```

This installer requires Python=3.9. 本安装包需要 Python=3.9