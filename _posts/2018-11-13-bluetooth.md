---
layout: post
title: 蓝牙
subtitle: ===>
bigimg: /img/path.jpg
tags: [arch,蓝牙]
---
## arch 安装蓝牙
```bash
# 安装协议和工具包
sudo pacman -S bluez bluez-utils 
# 加载驱动模块
modprobe btusb
# 查看驱动是否加载
lsmod |grep btusb 
# 驱动蓝牙服务,可设置为开机启动
sudo systemctl start bluetooth.service 
```

## 命令行配置蓝牙
**Bluetoothctl**
```bash
bluetoothctl #启动交互命令。可以输入 help 列出所有有效的命令。
power on #打开控制器电源。默认是关闭的。
devices #获取要配对设备的 MAC 地址。
#如果设备未在清单中列出，输入 scan on 命令设置设备发现模式
scan on 
agent on #打开代理。
pair MAC Address #配对（支持 tab 键补全）。
#如果使用无 PIN 码设备，再次连接可能需要手工认证。输入 trust MAC Address 命令。
#最后，用 connect MAC_address 命令建立连接。
```

## gnome下自带管理工具.
