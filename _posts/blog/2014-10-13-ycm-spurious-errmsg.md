---
layout: post
title: YouCompleteMe Spurious Errmsg
category: blog
---

{{ page.title }}
================

<p class="meta">13 Oct 2014 - Beijing</p>

昨天(10.12)参加完百度面试伤心得不行，决定自己实现下`string.h`里边的函数，所以在[slice](https://github.com/liuluheng/CTCI/tree/master/slice)目录新建了一个`cstring.cc`的文件。我用VIM一直在里边写代码，测试各个函数
也都是输出到stdout,在tmux里的另一个panel。后来几个函数写差不多也测试的差不多了，打算换成更加优雅的assert(:)..) 调试方式，然后噩梦就开始了。我加上
`#include <cassert>` 后可能重新触发了YCM的预处理命令，此后就一直报`cout undefined`, 简直就是莫名其妙啊！`#include <iostream>` 报缺`}`
`#include <cassert>` 报invalide UTF-8 filetype, google 查吧，有说编译系统崩溃了的, 别的就根本与这种情况没有关系了...很无语。以前在/home/test/(我的垃圾
试验场）也出现过这种情况,本来就不明所以，心想怎么漫延到这里了，难不成YCM真的挂了?因为用clang编译文件还是可以的。更新下YCM吧(很不情愿，这个还要重新编译，
    重新读安装文档，我已经越来越不愿做这种跟写程序没关的事了)废劲更新完已经是13:30了(问题11:00左右出现,中间吃了个午饭),发现还是不行,一样报错。无语了，差点
就要重新安装YCM了,很受挫，中间就干了点别的事，直接说重点吧，我发现在别的文件夹里YCM是正常工作的，只有在两个文件夹下有问题，所以我猜测肯定是文件夹下可能多了什么东西，`ls -a`也没发现什么，`make clean`下吧，干净些，ding dong, The GOD lighten me,再打开文件问题消失了，很诡异有没有！！我就立马想到.ycm_extra_conf.py
里有个`-I .`,这下可算知道原因了，因为`cstring`是C++的一个头文件，`iostream`里边肯定包含了这个文件，致使出现以上难以理解的bug,其实这个技巧在陈硕的书里提到过
,用来测试iostream里包含string头文件.问题解决了就是爽！！！！还不写出来得瑟下？？！！！：）））不过这已经是下午16:00后的事了!!!Fucking wasting TIME!!啊！！！

