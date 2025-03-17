# MIAA-Z1 仓库

本仓库和宇树提供的仓库基本一致，我们删去了C++实例，并把官方文档中的教程在这体现一二。如果本文档令您感到困惑或者不清晰，还清前往[官方文档](https://dev-z1.cn.unitree.com/)查看，或者查看B站上的[官方视频教程](https://www.bilibili.com/video/BV1jT411B7Cz?vd_source=11e4ce612726bc848135c5c6c83ddfa9&spm_id_from=333.788.videopod.sections)

#  实机运行

这部分的主要目的是帮助您安装并运行Z1-sdk，接下来步骤：
## 克隆仓库

克隆仓库可以在终端使用如下指令
```BASH
# 设置路径
mkdir -p ~/your/path
cd ~/your/path

# 克隆仓库
git clone https://github.com/unitreerobotics/z1_controller.git 
git clone https://github.com/unitreerobotics/z1_sdk.git
```

## 编译仓库

```BASH
# 编译z1-controller
cd z1_controller 
mkdir build && cd build cmake .. 
make -j$(nproc)
cd ../..
```
这会在`z1-controller/build`下生成一个名为`z1_ctrl`可执行文件，这是用于设备通讯和机械臂控制的程序，使用`UTP`协议。
```BASH
# 编译sdk的python接口
cd z1_sdk 
mkdir build && cd build 
cmake -DBUILD_PYTHON_INTERFACE=ON .. 
make -j$(nproc) 
cd ../..
```
编译后会产生可执行的示例文件。

## 使用SDK
在连接设备和机械臂后，先调整你的网络设置为如下：

| 域名              | 子网掩码          | 网关            |
| --------------- | ------------- | ------------- |
| 192.168.123.XXX | 255.255.255.0 | 192.168.123.1 |
XXX可以换为除110和111外的所有数，当然，如果你要操作多台机械臂，不要设置重复的IP。

在运行脚本前，先在终端运行`z1-ctrl`。运行后会一直跳出警告`[WARNING] UDPPort::recv, unblock version, connect wit z1_sdk wait time out`，这是因为你还没有运行sdk进行通信，此时再运行你的脚本即可。

# ROS仿真

（to be updated)