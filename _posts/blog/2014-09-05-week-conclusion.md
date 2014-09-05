---
layout: post
title: Week Conclusion(14.09.05)
category: blog
---

{{ page.title }}
================

<p class="meta">05 Sep 2014 - Beijing</p>

feof/fseek
---
这周实验室项目要读一个二进制文件，用到了**feof/fseek**.
类似下面这样，
<script src="https://gist.github.com/liuluheng/71fb1b2539dd4610b980.js"></script>
然后直接busy loop了，原因是fseek即使到了文件结尾也不会设置eof标志([代码](https://github.com/liuluheng/How-to-Make-a-Computer-Operating-System/blob/master/src/sdk/src/libc/src/stdio/fseek.c#L12)),fseek直接调用lseek后者直接调用系统调用([代码](https://github.com/liuluheng/How-to-Make-a-Computer-Operating-System/blob/master/src/sdk/src/libc/src/unistd/lseek.c#L13)),fseek只是多了一层对FILE结构体的清理.


**解决办法:**添加fread, 在fread后加feof判断,

Looks like

    while (1) {
        fread(dummy_buf, size, nmemb, file);
        if (feof(file)) {
            break;
        }
        fseek(file, offset, SEEK_CUR);
    }

fseek在处理文件偏移的时候比fread高效, fread uses fgetc, so we keep fseek, and only need a single fread to check the eof.


Algorithm
---
Read the [cracking the code interview](http://hawstein.com/posts/ctci-solutions-contents.html) till to Chapter 5.
And some [leetcode](https://github.com/liuluheng/leetcode/tree/master/C%2B%2B)

Algorithm is useful, when I doing my project, I will always thinking to use some algorithms or some cool data structures. That is funny.
Programming gets funny for me when I get to use one algorithm or a language feature.

Effective STL
---
review some items..
* Item 7. When using containers of newed pointers, remember to delete the pointers before the container is destroyed.
* Item 9. Choose carefully among erasing options.
* Item 26. 27. 28. 29. all about Iterators..

Gists
---
<script src="https://gist.github.com/liuluheng/cc8b14ef3cb53d7b94ea.js"></script>
<script src="https://gist.github.com/sing1ee/727ccecc0f512d672ad1.js"></script>
<script src="https://gist.github.com/liuluheng/4db9fc0a7ee58ddbeb54.js"></script>
