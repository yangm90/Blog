---
layout: post
title: ant打包策略
description: ant打包策略
category: blog
---

###操作流程
1.准备必要工具。
	- ​python2.X(注意，不能用3.X版本)
	- apache-ant-1.8.4(注意，一定要此版本)
	- android sdk
2.把python路径(如：c:\Python25)，ant路径(如d:\apache-ant-1.8.4\bin\),sdk工具路径(如d:\android-sdk\build-tools\18.1.1)加入PATH环境变量。
3.在CleanMaster工程所在路径，用python调用build/changebuildXXX/before.py脚本修改工程环境。(如果你想打国内版的包，就是changebuild0，如果想打国际版的包，就是changebuil1) 参看：如何构造一个指定包版本的工程代码环境
4.修改local.properties中配置的SDK路径。
5.修改proguard.cfg中-libraryjars开头的三行配置路径。
{% highlight java linenos %}
-libraryjars 'D:\Program Files\Java\jre6\lib\rt.jar'
-libraryjars 'D:\install\Android\android-sdk\platforms\android-17\android.jar'
-libraryjars 'D:\install\Android\android-sdk\platforms\android-17\data\layoutlib.jar'
{% endhighlight %}
6.修改custom_rules_commons.xml中配置的python路径。
7.在CleanMaster工程所在路径，执行ant clean。
8.在CleanMaster工程所在路径，执行ant cmrelease。构建成功后，安装包在bin/channel路径下。

###FAQ
1.如果出现下述报错，就是lint检查失败了，没有生成结果文件。
![Alt text]( /images/android/android_ant.jpg "Optional title")


[yangming]:  
