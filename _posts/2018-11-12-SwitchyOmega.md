---
layout: post
title: chrome翻出来
subtitle: 翻出来看世界
bigimg: /img/path.jpg
tags: [switchyomega,chrome]
---

# 浏览器代理设置
> ssr代理做好了,现在需要让浏览器代理出来.推荐使用-switchyomega  

## 安装
1. 链接到chrome商店,下载安装插件
    > [点击进入](https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif?utm_source=chrome-ntp-icon)  
网上好多都是这样的教程.可这是一个悖论.因为google商店也在外面,进不去怎么装.思路就剩下手动安装了,可以找第三方插件转存或者别人共享的.可隐患还是有,而且版本未必最新.为何不去github上找找呢.
2. github安装  
[git项目](https://github.com/FelisCatus/SwitchyOmega)顺手点个star吧.  
[插件下载](https://github.com/FelisCatus/SwitchyOmega/releases) 下载crx文件.  
地址栏进入 **chrome://extensions/**  
打开右上角的开发者模式.
![img](http://phguzqfjx.bkt.clouddn.com/2018-11-12-16-50-01-的屏幕截图.png)  
拖进去,允许一下就ok.

3. 使用
![img](http://phguzqfjx.bkt.clouddn.com/2018-11-12-22-06-14-的屏幕截图.png)  
如图,新建一个规则即可.
用的时候选上就好.不过这样是全局的.国内有点不好用,而且流量也跑的快不是吗.
![img](http://phguzqfjx.bkt.clouddn.com/2018-11-12-22-07-56-的屏幕截图.png)
这是自动方案.符合规则的走代理.规则外直连.  
规则就是 _gfwlist_  
https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt  
点一下立即更新情景模式.列表会载入规则.  
记得保存一下.使用的时候点选自动.




