---
layout: post
title: 2020-01-03 Linux中root用户找不到JAVA_HOME
date: 2020-01-03
description: "。。。"
tag: 学习 linux
renderNumberedHeading: true
grammar_cjkRuby: true
---   
### 概述：
><p>linux普通用户安装了java，切换到root用户却提示找不到java环境 </p>
``` javascript
browser.sh: 12: browser.sh: java: not found
```

### 原因及解决方案  
>在Ubuntu环境中安装好Java环境后设置环境变量：在/etc/profile中设置好了JAVA_HOME变量并引入到PATH中，用于Ubuntu默认是不以root用户登录的，这时echo $PATH可以看到JAVA_HOME已经被设置好了，java命令也可以执行。

>接下来su root，再输入java命令提示找不到java命令，$PATH中也找不到JAVA_HOME这个路径了。查了很久的资料也没有找到原因，后来偶然切换用户的时候用了su - root命令，这时又可以找到JAVA_HOME这个变量了。

 

>对比了一下su和su - 这两个命令的差别才明白：
su是切换用户存取权限，但是没有获得环境变量，所以PATH没有被带入；su -是完全的切换用户，可以获得环境变量，所以可以找到JAVA_HOME。



### 总结：
 > su root
	  su - root 为完全切换用户
	  可根据自己需要进行选择