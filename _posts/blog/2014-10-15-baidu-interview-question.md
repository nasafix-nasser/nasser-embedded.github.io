---
layout: post
title: Baidu Iterview Question
category: blog
---

{{ page.title }}
================

<p class="meta">15 Oct 2014 - Beijing</p>

Question 
---

1. 简述源程序到可执行文件的全过程.
2. 简述动态库与静态库区别.
3. 简述TCP与UDP的区别, TCP怎么提供可靠的数据传输?
4. 简述多进程与多线程的区别?
5. 简述new和malloc的区别.
6. 实现strcpy, 考虑strcpy(p + 1, p).
7. 实现非递归快排. 

Answer
---

1. 2.
    [ COMPILER, ASSEMBLER, LINKER AND LOADER: A BRIEF STORY ](http://www.tenouk.com/ModuleW.html)

5.
    [google](http://209.116.186.231/#newwindow=1&q=new+malloc+difference)
    [stackoverflow](http://stackoverflow.com/questions/807939/what-is-the-difference-between-new-and-malloc-and-calloc-in-c)
    [stackoverflow](http://stackoverflow.com/questions/240212/what-is-the-difference-between-new-delete-and-malloc-free)

6. 7.
    [slice/cstring.cc](https://github.com/liuluheng/CTCI/blob/master/slice/cstring.cc)
    [slice/quicksort.cc](https://github.com/liuluheng/CTCI/blob/master/slice/quicksort.cc)
