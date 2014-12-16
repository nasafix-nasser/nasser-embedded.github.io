---
layout: post
title: Internals Archives
category: blog
---

{{ page.title }}
================

<p class="meta">16 Dec 2014 - Beijing</p>

[Gustavo Duarte blog](http://duartes.org/gustavo/blog/archives/)

[其中一些文章的中文翻译](http://blog.csdn.net/drshenlei/article/category/551407)

我的关于linux页表的一些[理解](http://blog.csdn.net/drshenlei/article/details/4277959#quote)

"在32位的线性地址中，31－22位用来索引页目录项的地址，该目录项中含的是页表的物理地址；21－12位在对应的页表中索引对应页的物理地址；0－11位是在前两步索引出来的页（该页的物理地址低12位为0 ）中的偏移地址。所以最终线性（虚拟）地址到物理地址的映射中，低12位的值其实既是32位线性地址的组成部分也是物理地址的组成部分。高20位则不然。所以可以利用线性地址的低12位（0－11位或者子集）来进行L1 cache的组索引。"

