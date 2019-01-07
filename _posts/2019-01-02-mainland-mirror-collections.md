---
layout: post
title:  "国内服务器镜像"
date:   2019-01-02 10:30:58 +0800
categories: server mirror
---

# 镜像网址收集
- [清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/)

----------------
# 一、ruby gems仓库

原始URL|国内镜像|备注
:-:|:-:|:-:
https://rubygems.org|1.https://gems.ruby-china.com 2.https://ruby.taobao.org|

在命令行中敲入以下命令：
#删除默认的官方源
```
gem sources -r https://rubygems.org/
```
#添加淘宝源
```
gem sources -a https://gems.ruby-china.com
```
#查看当前源
```
gem sources -l
```

----------------
# 二、 msys2修改源（清华大学/中国科学技术大学的源均可）
帮助参考[https://mirrors.tuna.tsinghua.edu.cn/help/msys2/](https://mirrors.tuna.tsinghua.edu.cn/help/msys2/)

2.1 编辑 /etc/pacman.d/mirrorlist.mingw32 ，在文件开头添加：
```
Server = https://mirrors.tuna.tsinghua.edu.cn/msys2/mingw/i686
```
2.2 编辑 /etc/pacman.d/mirrorlist.mingw64 ，在文件开头添加：
```
Server = https://mirrors.tuna.tsinghua.edu.cn/msys2/mingw/x86_64
```
2.3 编辑 /etc/pacman.d/mirrorlist.msys ，在文件开头添加：
```
Server = https://mirrors.tuna.tsinghua.edu.cn/msys2/msys/$arch
```
2.4 然后执行 pacman -Sy 刷新软件包数据即可。
