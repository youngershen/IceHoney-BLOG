---
layout: post
title: "Archlinux折腾笔记"
date: 2014-04-20 19:52
comments: true
tags: notes linux
---

四月也算过去了一大半了,经过了一个月的奔波与折腾,总算安顿好自己了.在学校本地找了一个还算不错的实习.
阴差阳错的选择了Web开发工程师的职位,其实我最想做的是后端开发,前端也还是比较喜欢的.但是我有个很大的
缺点就是不会设计... 不会设计的前端开发工程师很鸡肋的,每次网站开发都是同学出设计图我来做的.这样不行的,
我必须能独当一面才算能在公司站得住脚.

近况就是这些,接下来就是记录下自己在Archlinux下折腾的东西.方便自己以后查询使用.

#Linux下视频截图制作动态GIF

观看视频遇到经典的镜头当然得录下来做成GIF~
首先需要安装 `imagemagick` 这个软件包才行  

	mplayer -vo png -ss 00:08:28 -frames 200 123.mp4 
	mogrify -resize 848x480 *.png
	convert -delay 4  *.png ry.gif

第一句话是利用mplayer输出png格式图片,从8分28秒开始,截图200帧,也可以换成  

	mplayer -vo png:z=1 -ss 00:08:28 -endpos 8  123.mp4

这样就是截取8秒,png后面的z=1是压缩比例从0到9 压缩程度递增,压缩速度也递增.
第二行便是修改尺寸,毕竟720p的GIF实在是吃不消啊.然后第三行变把这些png生成GIF了.

#sudo设置环境变量

有时候程序需要使用root权限,但当我使用sudo的时候结果发现这时候程序又使用root用户的配置文件了.  
现在的需求就是程序使用root权限运行但是执行时候读取HOME变量还是当前用户.  
[Run_X11_apps_using_sudo](https://wiki.archlinux.org/index.php/Sudo#Run_X11_apps_using_sudo)
wiki上有清楚的讲解这样的解决办法.

