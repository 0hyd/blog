---
layout: post
cid: 27
title: 博客的搭建教程（基于Apache和typecho）使用MySQL，CURL和mbstring
slug: 27
date: 2022-12-27T22:13:00+08:00
lastmod: 2023-04-22T06:46:31+08:00
status: publish
author: heiyedao
categories: 
  - 代码
  - 经验
tags: 
  - typecho
  - 博客搭建
  - linux
advancedSettings: 
cover: https://heiyedao.top/usr/uploads/2023/01/3424891629.jpg
excerpt: 本文将会总结我个人博客搭建经验，有搭建博客想法的可以按以下步骤一步步来
PostType: post
showToc: 1
---


#本文将会总结我个人博客搭建经验，有搭建博客想法的可以按以下步骤一步步来（保姆级教程，确保小白也可食用）

##首先确保你有条件搭建博客，可以连接服务器的电脑，如果没有电脑，手机也不是不可以，但会复杂很多，[juicessh][1]  密码:81bq，手机连接服务器软件我先放出来,这里我不对手机操作进行讲解

###网站搭建好后还需要备案，备案周期时间需要20天左右的时间，暂不在本篇文章进行介绍，若不知道网站备案是什么的[备案介绍传送门][2]

###这里可以参考一下[typecho的官方帮助文档][3]，考虑要不要搭建博客

**搭建好后的例子** |´・ω・)ノ 
就是这个网站啦，网站框架基于typecho和ubuntu云服务器搭建，使用~~小姨子~~xyz域名

**搭建个人博客需要以下准备**
1. 一台~~能用的过去即可~~电脑或者手机（不建议）
2. 购买服务器
3. 服务器配置
4. typecho配置
5. 购买域名

----------

##搭建教程

### 1. *服务器购买*
可以先从阿里云，腾讯云，华为云入手，大厂一般都会有新用户免费使用一个月的福利，也可以趁这个机会搭建一个练练手，再判断要不要开长期服务器，放出各家服务器官网 [腾讯云][4] [阿里云][5] [华为云][6]
服务器性能不用太高，大概最低的1核1G的性能就可以，一年在60r左右的价格，如果你有rmb，可以适当提高一下CPU
官网操作流程
1. 注册一个账号，进行实名认证
2. 选择合适的服务器进行购买
3. 规格只需要改为离你近的服务器地区，选择Ubuntu长期支持版本（为什么不选window10？这个性能是带不动一个系统桌面加上一个网站的）
4. 买好了就可以到官网的控制台管理你的服务器


----------


### 2. *服务器配置* 
**这个是部分比较复杂，很多人就是被这里劝退，即使按照我的步骤进行，可能也会出现一些特殊情况，有问题可以在评论区留言**
**接下来的操作需要记录一些密码，IP之类的建议使用记事本记录放在桌面，方便取用**
|**SSH连接**|
|:----------:|
下载网络连接软件ssh，这里我推荐Xshell 7和Xftp（网络传输文件），下载官网[家庭/学校免费版][7]

![7][8]

填写你的名字（随便一个都可以）和邮箱，获取地址到邮箱查看

|**连接服务器**|
|:---:|
打开你购买服务器的官网，进入控制台（腾讯云可以在微信小程序里操作），重置服务器密码

**记下用户名和密码，等下会用到**。复制你的服务器IP地址（公网IP）

![8][9]![9][10]

####打开刚刚下载好的Xshell 7 ,点击新建会话

![8][11]

####然后输入IP地址即可

![9][12]

####输入用户名，（选上记住用户名）

![10][13]

####输入密码（选上记住密码）

![11][14]

####看到这个界面就意味者成功连接了

![12][15]
#### 设置root用户密码
在连接时使用的用户大多是没有太多权限的，需要登陆为管理员root，这样才能保证你对这台服务器有绝对控制权。一开始root是没有密码的，输入指令设置密码
    sudo passwd root
输入两次密码，**密码是默认不在屏幕上显示的，输入后看不见是正常的**
设置成功后输入指令登陆到root用户
    su root
    password:你的密码
登陆后你的指令前的"$"变为"#"，这样就拥有了root级别的权限，在root用户下，下文的指令中sudo就可以去掉，否则需要加上（sudo是获取root级别权限的指令）

####这里是重点，需要往服务器添加一些基础配置，确保typecho可以正常使用，这里typecho官方清单列得很清楚
![16][16]
**如何添加**  这里使用指令进行下载
添加MySQL
    sudo apt-get install mysql-server
添加PHP和Apache2
    sudo apt update
    sudo apt install php libapache2-mod-php
添加php-mysqli，php-curl，php-mbstring
    sudo apt install php-mysqli  php-curl php-mbstring
**若中通遇到[y/n],就是问需不需要继续安装，输入“y”即可**
建议先添加MySQL，若中途在配置MySQL出了问题，就直接去服务器官网控制台重装系统
####MySQL的配置
MySQL是一个数据库，[常用指令传送门][17]，需要设置一下用户密码，由于MySQL在服务器的设置很玄乎，似乎不同服务器下载下来的MySQL的版本不同，有些指令不是通用的，这里列出几种方法
**注意：mysql指令后面都需要加上“；”结束指令**
1. 刚开始MySQL是没有密码的，可以直接登陆，输入
         sudo mysql -uroot -p
然后直接回车就可以直接进入数据库
输入指令
        ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by '114514';
***114514*是你要设置的密码**
2. MySQL在一开始是有默认密码的，输入下面指令获取
        sudo cat /etc/mysql/debian.cnf

    ![password][18]
   图片中password是密码，例子P8hdnr0U3oQ8OCNi，然后输入
        mysql -u debian-sys-maint -p
        这个debian-sys-maint是用户名，然后在“-p”后面输入密码，密码是类似上面一串数字的
接着重复上面的指令，逐个尝试
        set password for root@localhost = password('114514');
        alter user 'root'@'localhost' identified by '114514';
        set password for 'root'@'localhost' = password('114514');​
        ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by '114514';
这几条指令的作用是一样的，但只有一条是有用的，请挨个尝试，***114514*是你要设置的密码**

####判断成功的方法，输入
    sudo mysql -uroot -p123456
若可以成功进入即可，记下你设置的密码，之后需要用到
![18][19]
进入之后添加typecho数据库，输入
    create database +数据库名称;
    例子：create database typecho;
建议设置为typecho,接下来需要使用
MySQL退出指令
    quit;
**访问在浏览器你的公网ip,你可以看到php的默认界面，这意味着你的网站php配置成功，到这里就完成一半以上了，可以接着下面操作**

####上传typecho
从官网下载  [下载链接][20]或者[蓝奏云网盘V1.2.0版目前最新][21]，密码:hamw，下载完后解压
需要给服务器文件夹写入权限，在服务器输入指令
    cd /var/www
    sudo chmod 777 *
设置文件夹777权限（777就是rwxrwxrwx，意思是该登录用户（可以用命令id查看）、所在的组和其他人都有最高权限。）

然后在Xshell 7打开Xftp，可以不用再次输入密码

![22][22]
![23][23]

####在服务器文件地址栏输入/var/www/hmtl,回车，转到该目录下，或者你可以自己翻一下，熟悉服务器目录，然后你可以看到一个文件hmtl.php，这个是刚刚在浏览器看到的php默认页面，**进行删除**
打开**解压后**的typecho文件夹，把**里面的**文件复制到服务器/var/www/hmtl目录下

![24][24]

####回到指令控制台，输入以下指令
    cd /var/www/html/usr
    sudo chmod 777 uploads

####配置完成后需要重启
1. 方案一：输入指令来重启程序
        sudo service apache2 restart
        sudo service php-fpm restart
2. 方案二：去服务器运营商重启服务器,过程2分钟左右，好处是全部重启，比较彻底，坏处是需要重新连接一下服务器


####然后在浏览器访问ip,可以看到typecho的安装向导

![25][25]

####初始化配置那一步应该是可以直接过去了，如果你按照我的教程一步步进行，若有提示配置缺失，请根据页面提示查找我教程的是不是在操作过程中有哪步遗漏了，或者请教度娘

####接下来是第三步
**前三项不需要改动，在数据库密码填写之前记下的root（用户）密码**

![26][26]

**数据库前缀也无需改动，然后配置你的服务器**

![27][27]

接下来就是配置成功的界面啦 ::(太开心) 

![28][28]
![28][29]

####自此，网站的搭建就完成了，如果想像我的网站一样富有特色，请到typecho官网论坛下载主题，插件等  [传送门][30]


  [1]: https://heiyedao.lanzouw.com/iRmv20dxsidg
  [2]: https://help.aliyun.com/knowledge_detail/36907.html
  [3]: http://docs.typecho.org/install
  [4]: https://activity.huaweicloud.com/
  [5]: https://www.aliyun.com/
  [6]: https://activity.huaweicloud.com/
  [7]: https://www.xshell.com/zh/free-for-home-school/
  [8]: https://cdn.staticaly.com/gh/0hyd/picture@main/QQ%E6%88%AA%E5%9B%BE20221227141613.png
  [9]: https://cdn.staticaly.com/gh/0hyd/picture@main/%C2%B75.png
  [10]: https://cdn.staticaly.com/gh/0hyd/picture@main/%C2%B76.png
  [11]: https://cdn.staticaly.com/gh/0hyd/picture@main/%C2%B71.png
  [12]: https://cdn.staticaly.com/gh/0hyd/picture@main/QQ%E6%88%AA%E5%9B%BE20221227142229.png
  [13]: https://cdn.staticaly.com/gh/0hyd/picture@main/%C2%B72.png
  [14]: https://cdn.staticaly.com/gh/0hyd/picture@main/%C2%B73.png
  [15]: https://cdn.staticaly.com/gh/0hyd/picture@main/%C2%B74.png
  [16]: https://cdn.staticaly.com/gh/0hyd/picture@main/%C2%B77.png
  [17]: https://blog.csdn.net/lllliulin/article/details/51526569
  [18]: https://cdn.staticaly.com/gh/0hyd/picture@main/%C2%B78.png
  [19]: https://cdn.staticaly.com/gh/0hyd/picture@main/%C2%B79.png
  [20]: http://typecho.org/download
  [21]: https://heiyedao.lanzouw.com/iDZb60jj4ihi
  [22]: https://cdn.staticaly.com/gh/0hyd/picture@main/%C2%B70.png
  [23]: https://cdn.staticaly.com/gh/0hyd/picture@main/%C2%B710.png
  [24]: https://cdn.staticaly.com/gh/0hyd/picture@main/%C2%B711.png
  [25]: https://cdn.staticaly.com/gh/0hyd/picture@main/%C2%B712.png
  [26]: https://cdn.staticaly.com/gh/0hyd/picture@main/%C2%B713.png
  [27]: https://cdn.staticaly.com/gh/0hyd/picture@main/%C2%B715.png
  [28]: https://cdn.staticaly.com/gh/0hyd/picture@main/%C2%B717.webp
  [29]: https://cdn.staticaly.com/gh/0hyd/picture@main/%C2%B716.png
  [30]: https://typecho.me/