---
layout: post
title: android辅助工具 
description: 存在感对于每个人的生活有多么的重要，可能平时并不是太关注，其实他就是生活的全部
category: blog
---
##android lint工具
###使用了高版本的API
在开发中,常常会不小心用到了高版本的API, 这样会导致程序在低于API版本设备上崩溃. 这样的崩溃无法被catch
{% highlight java linenos %}
# 在工程目录下执行
$ lint --check NewApi .
{% endhighlight %}

结果
{% highlight java linenos %}
src/com/cleanmaster/security/scan/ui/dialog/SecurityVirusDialog.java:94: Error: Call requires API level 11 (current min is 8): android.widget.TextView#setAlpha [NewApi]
   subtitleTv.setAlpha(0.75f);
              ~~~~~~~~
src/com/cleanmaster/ui/widget/ShareBar.java:25: Error: Call requires API level 11 (current min is 8): new android.widget.LinearLayout [NewApi]
        super(context, attrs, defStyle);
        ~~~~~
{% endhighlight %}

然而需要注意, Lint输出的这些信息并不一定真正会出问题. 所以你需要看代码确定一下:

{% highlight java linenos %}
public void show(

         if (SDKUtils.isAboveSDK14()) {
             ///< 4.0以下没有这个方法，所以只在4.0及4.0以上增加以下alpha值处理
             subtitleTv.setAlpha(0.75f);
			 }

{% endhighlight %}
[yangming]:  
