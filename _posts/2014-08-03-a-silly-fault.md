---
layout: post
title: A Silly Fault
---

{{ page.title }}
================

<p class="meta">03 Aug 2014 - Beijing</p>

上周五(08.01)，不小心把/usr/local/include/里边的内容都删了,导致所有c++程序都编译不过,奇怪的是c程序能编译(为啥?)。
当初学CPPPrimer要用到c++11特性，所以手动编译安装了gcc-4.8.2，都装在了/usr/local/下，这样bin文件还在，但是include头文件不在了。

尝试apt-get install gcc4.8，成功安装后，还是不能编译文件。
用
```
g++ -E -x c++ - -v < /dev/null
```
查看g++ 编译程序时搜索头文件的路径, 确定此g++用的还是/usr/local下的g++。

通过apt-get 安装gcc4.8之所以还不能用是因为，在$PATH里边，/usr/local/bin/路径先于/usr/bin路径，
所以系统在local目录下找到以前的gcc/g++之后就会直接使用。

**apt-get install只会在/usr/下面安装程序，而不会在/usr/local/下面安装程序，后者是大多数库手动编译安装的默认位置。**

解决办法有
---
* 把原来local目录的bin文件删掉
* 再重新源码编译安装。
  - 奇怪的是，以前我编译安装gcc-4.8.2的build目录不能用了。我也手动编译安装过clang,但是clang的能使。
  - 而且我猜测不删local目录下的gcc/g++连gcc源码也编译不过。这是鸡与蛋的问题了。

所以选择第一种方法。

```
sudo rm -rf *
```
的时候一定要注意！
