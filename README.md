# Paddle-raspberry-pi-64-bit
Raspberry Pi 4B Paddle installation wheels (64-bit).

English | [简体中文](./README_cn.md)

## Quick Start 

Requirements

Hardware and System: `Raspberry Pi 4B 64-bit (aarch64/armv8)`

Python version: `Python=3.9`

Download the `.whl` installer. [Paddle2.4-Raspberry-pi-64bit](https://github.com/1099255210/Paddle-raspberry-pi-64-bit/releases/download/2.4/paddlepaddle-0.0.0-cp39-cp39-linux_aarch64.whl)

```shell
pip install paddlepaddle-0.0.0-cp39-cp39-linux_aarch64.whl
```

After this, check if the installation is successful: 

```shell
python

>>> import paddle
>>> paddle.utils.run_check()
```

If you see `PaddlePaddle is installed successfully!`, then you are ready to go. 

## Detailed Information

This installer is compiled on the system below: 

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

Use this command to check your system:

```shell
uname -m && cat /etc/*release
```

Check your Python version: 

```shell
python -c "import sys; print(sys.version)"
```

This installer requires Python=3.9. 