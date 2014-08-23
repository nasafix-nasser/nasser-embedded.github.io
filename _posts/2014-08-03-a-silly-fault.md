---
layout: post
title: A Silly Fault
---

{{ page.title }}
================

<p class="meta">03 Aug 2014 - Bei jing</p>

愚蠢的错误
====
上周五，不小心把/usr/local/include/里边的内容都删了,导致所有c++的东西都编译不过。而我的gcc4.8.2又是手动编译安装的，都装在了/usr/local/下，bin文件还在，但是include头文件不在了。

尝试apt-get install gcc4.8，成功安装后，还是不能编译文件。而且/usr/bin/下边也都有。
可以用
```
g++ -E -x c++ - -v < /dev/null
```
查看，g++ 编译程序时搜索的头文件的路径。

这验证了apt-get install只会安装文件在/usr/下面，而不会安装在/usr/local/下面，后者是大多数库手动编译安装的默认位置。

通过apt-get 安装gcc4.8之所以还不能用是因为，在PATH里边，/usr/local/bin/路径先于/usr/bin路径，所以系统在local目录下找到以前的gcc/g++之后就会使用，相当于没有改变。

解决办法有
---
* 把原来local目录的bin文件删掉
* 再重新源码编译安装。
  奇怪的是，以前我编译安装gcc4.8.2的build目录不能用了。编译安装clang的能使。而且我猜测不删local目录下的gcc/g++连gcc源码也编译不过。成鸡与蛋的问题了。

所以选择第一种方法最可靠。

唉，愚蠢的错误啊，
```
sudo rm -rf *
```
的时候一定要注意！！！
