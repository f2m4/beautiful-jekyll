---
layout: post
title: arch安装vmwre折腾记
subtitle: vmware我放弃你了
bigimg: /img/path.jpg
tags: [arch,vmware]
---

## 开篇
上篇刚记录了使用aur安装vmware的过程.以为安装成功了.  
建立一个虚拟机,启动.出现了一个错误vmmon找不到.MD真没有啊.  
各种搜索,无果.怀疑是linux内核的原因.  
最新版的15不支持我的老cpu.无法安装.  
旧版的又有一个vmmon错误.  
最后一次,使用官方教程安装.用bundle文件.更改执行权限,sudo sh安装.  
vmware11的安装界面是命令行的.简单设置一下就ok.安装也顺利.只是arch使用了
systemd管理,所以init哪里报了个警告.无妨.  
建立system启动管理文件.并启动.  
直接打不开......问题更多.现在开始放弃.  
可这种安装方式怎么卸载呢?去vmware官网查看.一个命令足矣.  
报错....郁闷.  
## 经历
使用aur安装的程序,都是编译后用pacman -U安装.所以卸载的时候也可以使用pacman -R.可使用bundle安装的怎么办.  
想着是不是能用aur覆盖安装,然后再使用bundle卸载?  
结果依然是不行,安装过程中报错,提示目录已经存在,中断安装.  

看来还是得使用它自带的命令vmware-install -u vmware-workstation  
从报错开始.发现一个语法错误.由于卸载程序是使用python写的.怀疑是python版本的问题.本地默认使用python3.用python2试试.
找到/usr/lib/vmware-installer/2.1.0/里面是一个安装工具.  
使用 python2 vmware-installer.py -u vmware-workstation  
提示缺少一个库lxml.安装即可.但不想破坏本地python2的环境,麻烦点建立虚拟环境.  
```bash
virtualenv --python=python2 py2
source ./py2/bin/activate
pip install lxml
sudo python vmware-installer.py -u vmware-workstation
```
ok!世界清净了.中间也有好多错误.主要是直接使用vmware-install命令会出错,需要找到它的链接文件,其实就是一个py脚本.这个脚本也会把自己删除.但由于使用python,该目录可能会有残留.强制删除即可.  

## 总结
问一下,自己为何非要vmware呢?  
本来考虑的是.为了方便用别用的虚拟机.人家用的是vmware.  
现在看来得不偿失.干嘛不自己做个呢.用virtualbox挺好.  
所以,以后不再linux上安装非开源软件了.太麻烦.费心.  

