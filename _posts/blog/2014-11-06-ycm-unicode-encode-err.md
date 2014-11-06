---
layout: post
title: YouCompleteMe UnicodeEncodeError
category: blog
---

{{ page.title }}
================

<p class="meta">06 Nov 2014 - Beijing</p>

Question 
---
前段时间升级了下YouCompleteMe 把里边(应该是vimsupport.py)自己添加的两行设置字符编码的代码给删了(:(),导致现在路径里包含中文,跳转就会出错.

        /home/beginner/.vim/bundle/YouCompleteMe/autoload/../python/ycm/vimsupport.py:309: UnicodeWarning: Unicode unequal comparison failed to convert both arguments 
        to Unicode - interpreting them as being unequal                                                                                                                
          if filename != GetCurrentBufferFilepath():                                                                                                                   
          Traceback (most recent call last):                                                                                                                             
            File "<string>", line 1, in <module>                                                                                                                         
              File "/home/beginner/.vim/bundle/YouCompleteMe/autoload/../python/ycm/youcompleteme.py", line 198, in SendCommandRequest                                     
                  return SendCommandRequest( arguments, completer )                                                                                                          
                    File "/home/beginner/.vim/bundle/YouCompleteMe/autoload/../python/ycm/client/command_request.py", line 79, in SendCommandRequest                             
                        request.RunPostCommandActionsIfNeeded()                                                                                                                    
                          File "/home/beginner/.vim/bundle/YouCompleteMe/autoload/../python/ycm/client/command_request.py", line 70, in RunPostCommandActionsIfNeeded                  
                              self._response[ 'column_num' ] )                                                                                                                           
              File "/home/beginner/.vim/bundle/YouCompleteMe/autoload/../python/ycm/vimsupport.py", line 321, in JumpToLocation                                            
                EscapedFilepath( filename ) ) )                                                                                                                            
            UnicodeEncodeError: 'ascii' codec can't encode characters in position 30-32: ordinal not in range(128)  



现在也还没找到解决办法, 只能不包含中文了.

关于编码问题这个[字符串和编码](http://www.liaoxuefeng.com/wiki/001374738125095c955c1e6d8bb493182103fac9270762a000/001386819196283586a37629844456ca7e5a7faa9b94ee8000)讲得不错.

以后解决了再补充.

