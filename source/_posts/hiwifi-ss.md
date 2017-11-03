---
title: 极路由Shadowsocks家庭无痛翻墙插件
date: 2016-09-01 14:12:16
tags: [hiwifi,ss,Shadowsocks,fuck-gfw]
---

## 1、准备工作
* ①. 首先你得有一台极路由，型号随意，要求系统版本必须低于``1.0``，否则安装会出错。
* ②. 然后你得有一个Shadowsocks帐号，可以自己在服务器上搭建，也可以购买，我这里不提供、也不出售。
* ③. 然后需要开启开发者权限，具体请参考官方的《[开发者模式功能开放公告](http://bbs.hiwifi.com/thread-74899-1-1.html)》。
<!--more-->

## 2、安装SS
* ①. 使用putty连接路由器：[下载地址](http://pan.baidu.com/s/1jGivsOm)
![](http://7xoatu.com1.z0.glb.clouddn.com/o_1af3br9sfect8rckt56l6hg5a.png)
点击open,会出现命令框：
![](http://7xoatu.com1.z0.glb.clouddn.com/o_1af3bs0itgv05361e7u10h71rb4a.png)
提示使用`root帐号`连接路由，密码是你的后台登陆密码。
* ②. 输入安装SS命令，按回车键： 
``cd /tmp && curl -k -o 01.sh http://mytv-10005639.file.myqcloud.com/01.sh && sh 01.sh && rm 01.sh``

## 3、配置SS
* ①. 登陆极路由后台开启Shadowsocks插件:
![](http://7xoatu.com1.z0.glb.clouddn.com/o_1af3c0jfl1afp1ehd19m713c58baa.jpg)
* ②. 在表单中填写你的SS帐号密码和加密方式，选择智能模式，保存，只要提示``运行中 已加速``就表示已经成功连上SS了。

#### 注意：
* ①.请关闭极路由的`自动更新`功能，要不每次路由器升级后，会删除SS插件。
* ②.若Shadowsocks选项显示的是：``{ "msg": "请求的接口不存在.", "code": 560 }``,请重启路由器。
这个时候，连接极路由的所有设备，理论上都可以无痛翻墙了。

## 4、更新gfwlist列表
* ①. SSH登录极路由：``ssh root@192.168.199.1 -p 1022`` 使用root帐号连接路由，端口为1022，密码为后台登陆密码。
* ②. 输入更新命令，按回车键：``cd /etc/gw-redsocks/gw-shadowsocks && wget http://mytv-10005639.file.myqcloud.com/gfwlist.txt && cat gfwlist.txt >> gw-shadowsocks.dnslist && /etc/init.d/dnsmasq restart``