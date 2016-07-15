---
layout: post
title: Linux 进程管理
categories: Linux
description: Linux 进程管理
keywords: Linux, 
---

# 进程管理





这一节我们介绍进程管理工具；      
使用进程管理工具，我们可以查询程序当前的运行状态，或终止一个进程；       
任何进程都与文件关联；我们会用到lsof工具（list opened files），作用是列举系统中已经被打开的文件。在linux环境中，任何事物都是文件，设备是文件，目录是文件，甚至sockets也是文件。用好lsof命令，对日常的linux管理非常有帮助。





## 查询进程





查询正在运行的进程信息




    
    <code>$ps -ef</code>





eg:查询归属于用户colin115的进程




    
    <code class="lang-shell">$ps -ef | grep colin115
    $ps -lu colin115</code>





以完整的格式显示所有的进程




    
    <code>$ps -ajx</code>





显示进程信息，并实时更新




    
    <code>$top</code>





查看端口占用的进程状态：




    
    <code>lsof -i:3306</code>





查看用户username的进程所打开的文件




    
    <code>$lsof -u username</code>





查询init进程当前打开的文件




    
    <code>$lsof -c init</code>





查询指定的进程ID(23295)打开的文件：




    
    <code>$lsof -p 23295</code>





查询指定目录下被进程开启的文件（使用+D 递归目录）：




    
    <code>$lsof +d mydir1/</code>





## 终止进程





杀死指定PID的进程 (PID为Process ID)




    
    <code>$kill PID</code>





杀死相关进程




    
    <code>kill -9 3434</code>





杀死job工作 (job为job number)




    
    <code>$kill %job</code>





## 综合运用





将用户colin115下的所有进程名以av_开头的进程终止：




    
    <code>ps -u colin115 |  awk '/av_/ {print "kill -9 " $1}' | sh</code>





## 总结





ps top lsof kill





Posted by: DY



