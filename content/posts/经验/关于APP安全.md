---
layout: post
title: 关于APP安全
date: 2023-04-02T10:28:00+08:00
lastmod: 2023-04-22T06:37:26+08:00
status: publish
author: heiyedao
categories: 
  - 经验
tags: 
  - app
  - 个人信息安全
  - 时政
advancedSettings: 
cover: https://heiyedao.top/usr/uploads/2023/04/1081720602.jpg
excerpt: 最近看到了一个比较有争议的事件，就拿出来分析一下
PostType: post
showToc: 0
---

**最近看到了一个比较有争议的事件，就拿出来分析一下**

本文章仅对网络信息收集整理h和分析信息的真实性，无任何相关倾向与不良导向

## 信息源缺乏
关于这件事，在网上是被封掉的，在各个平台和渠道收集的g信息都有不确定性，所以在一番收集后才准备发出来

> 本月早些时候，独立安全研究机构DarkNavy发表文章披露， 一些APP可以通过Android系统漏洞提权使其难以卸载

*该信息应该是事件萌发的苗头，但无法求证*

> Android漏洞 CVE-2023-20963 。该漏洞是Google在今年3月6日公开的，利用该漏洞可以提权，而且整个过程不需要用户交互。两周前修复补丁才提供给终端用户。

*确实有这个漏洞*

> Google强制禁用？！！

*这个情况确实发生，Google的安全服务会有提示*

该事件在外网上似乎7d没有太多人去关注，更多的是在讨论系统问题

现在这个事情没有一个定论，如果觉得有被App利用漏洞的，可以在IOS或者在Android13，安卓补丁2023-4-1的机器上用。因为IOS禁止动态dex下发，同时其应用商店审核相对较严，而Android 13对于相关API做了调整，防止本地提权绕过管理。

## 相关文章链接，但皆未能求证

Maybe it was a joke from the beginning or there really is some mystical force preventing it…

1. [《当App有了系统权限，真的可以为所欲为？》][1]

2. [《「 深蓝洞察 」2022 年度最“不可赦”漏洞》][2]

3. [《apk内嵌提权代码，及动态下发dex分析》][3]

4. [《APP恶意代码样本和脱壳机》][4]

5. [《中文版详细报告》][5]

6. [《app利用0day漏洞控制用户手机及r1窃取数据的分析，含分析指引》][6]

[hidden]629494354[/hidden]

  [1]: https://heiyedao.top/usr/uploads/2023/04/3241475641.txt
  [2]: https://heiyedao.top/usr/uploads/2023/04/3241475641.txt
  [3]: https://heiyedao.top/usr/uploads/2023/04/878613358.txt
  [4]: https://heiyedao.top/usr/uploads/2023/04/878613358.txt
  [5]: https://heiyedao.top/usr/uploads/2023/04/878613358.txt
  [6]: https://heiyedao.top/usr/uploads/2023/04/878613358.txt
  [7]: http://
