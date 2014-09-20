---
layout: post
title: github 和jekyll方法
description: 关于如何使用github和如何去使用jekyll的总结 
category: blog
---


###github常用命令

<ul>
	<li>git clone git@github.com:username/xxxxxx.github.com.git//本地如果无远程代码，先做这步，不然就忽略</li>
	<li>git pull origin master //先同步远程文件，后面的参数会自动连接你远程的文件/li>
	<li>git status //查看本地自己修改了多少文件</li>
	<li>git添加文件:git add .</li>
	<li>git提交文件: git commit -m "first commit"</li>
	<li>git push origin master //更新到远程服务器上</li>
</ul>

###jekyll常用命令
<ul>
	<li>jekyll打开本地服务jekyll serve</li>
	<li>关于jekyll的 Address already in use - bind(2):</br>
		先采用lsof -wni tcp:4000 或者使用 ps aux |grep "jek"</br>
		再采用kill -9 PID命令
		</li>
	
</ul>


###vim常用命令
<ul>
	<li>复制单行:yy</li>
	<li>复制单个单词:yw</li>
	<li>粘贴单行:p</li>
	<li>删除单行:dd </li>
	<li>删除单个单词:diw</li>
</ul>


###shell常用命令
<ul>
	<li></li>
	<li></li>
	<li></li>
	<li></li>
</ul>

linux上进程有5种状态:
1. 运行(正在运行或在运行队列中等待)</br>
2. 中断(休眠中, 受阻, 在等待某个条件的形成或接受到信号)</br>
3. 不可中断(收到信号不唤醒和不可运行, 进程必须等待直到有中断发生)</br>
4. 僵死(进程已终止, 但进程描述符存在, 直到父进程调用wait4()系统调用后释放)</br>
5. 停止(进程收到SIGSTOP, SIGSTP, SIGTIN, SIGTOU信号后停止运行运行)</br>
 
1）ps a 显示现行终端机下的所有程序，包括其他用户的程序。</br>
2）ps -A   显示所有程序。</br>
3）ps c    列出程序时，显示每个程序真正的指令名称，而不包含路径，参数或常驻服务的标示。</br>
4）ps -e  此参数的效果和指定"A"参数相同。</br>
5）ps e   列出程序时，显示每个程序所使用的环境变量。</br>
6）ps f    用ASCII字符显示树状结构，表达程序间的相互关系。</br>
7）ps -H    显示树状结构，表示程序间的相互关系。</br>
8）ps -N   显示所有的程序，除了执行ps指令终端机下的程序之外。</br>
9）ps s     采用程序信号的格式显示程序状况。</br>
10）ps S     列出程序时，包括已中断的子程序资料。</br>
11）ps -t <终端机编号> 　指定终端机编号，并列出属于该终端机的程序的状况。</br>
12）ps u 　 以用户为主的格式来显示程序状况。</br>
13）ps x 　 显示所有程序，不以终端机来区分。</br>
14）ps -l     較長,較詳細的顯示該PID的信息  </br>



[BeiYuu]:    http://beiyuu.com  "BeiYuu"
