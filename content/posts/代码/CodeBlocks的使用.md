---
layout: post
title: Code::Blocks的使用
date: 2023-04-01T23:19:00+08:00
lastmod: 2023-04-22T06:38:26+08:00
status: publish
author: heiyedao
categories: 
  - 代码
  - 经验
tags: 
  - code::blocks
  - 软件教程
  - 软件推荐
  - 编译器
advancedSettings: 
cover: https://heiyedao.top/usr/uploads/2023/04/2865391434.jpg
excerpt: code::blocks
PostType: post
showToc: 1
---

# 食用

Code::Blocks 是一个开放源码的全功能的跨平台C/C++集成开发环境(IDE)。

## 下载

官网链接 速度可以接受 [FossHUB][1] or [Sourceforge.net][2]
1. 一路按照操作引导下载即可，注意选择按照你的需求选择下载盘（这个不影响什么）
2. 如果你是下载在C盘之外，那需要设置一下编译器地址
![Snipaste_2023-04-04_23-18-14.png][3]

## 创建项目
使用此编译器需要一个完整的项目才能进行调试

**新建一个项目**

![Snipaste_2023-04-05_09-47-54.png][4]

**选择Console application**
![Snipaste_2023-04-05_09-48-16.png][5]

**选择对应的编译类型**
![Snipaste_2023-04-05_09-48-36.png][6]

**设定文件名称和目录，不要带有中文**
![Snipaste_2023-04-05_09-55-47.png][7]

![Snipaste_2023-04-05_09-57-00.png][8]

**之后就可以看到在左边的文件结构栏**
如果没有，按下shift+F2，或者打开view中的manager

![Snipaste_2023-04-05_10-27-26.png][9]

**打开查看变量窗口,可以自行调整界面布局，设置你的偏好**
![Snipaste_2023-04-05_10-21-48.png][10]
![Snipaste_2023-04-05_10-25-50.png][11]

## 运行和编译

**代码在main.cpp里编写**

![Snipaste_2023-04-05_10-08-39.png][12]

**从左到右依次是**
1.编译 ctrl+shift+F9**（编译当前文件）** 2.运行 ctrl+F10 3.编译并运行 F9
(注意：当打开工程文件时，会默认编译工程文件，想要编译其他文件，需要关闭工程文件)

Debug/Continue：启动调试
Run to cursor：执光标处（即你输入的光标在那就跳到那，注意不会跳出当前函数）
Next line：执行下一行代码
Step into：对于调用自定义函数的语句，此按钮可以进入到函数的内部，一步一步执行函数内部的代码
Step out：跳出当前函数
Next instruction：下一条指令
step into instruction：进入一条指令分步执行
break debugger：停止调试
Stop debugger：结束调试

![Snipaste_2023-04-05_10-15-07.png][13]

## 总结及注意事项
1. 编译需要创建一个工程项目，较为麻烦，可以只创建一个.cpp文件，如果需要编译就复制到项目的main.cpp文件进行编译
2. 如果你已经创建多个工程文件，确保你在编译时选择manager中你正在编写的文件夹，否则可能会出现一直在编译上一个工程文件
3. 打开code::blocks时软件图标会在任务栏疯狂跳动，这个bug可以追溯到13.xx版本，至今未修复，但不影响正常使用
4. 想要打开之前的工程文件，找到为.obj后缀的文件打开即可
5. 建议先编译看看报错信然后再运行



[1]: https://www.fosshub.com/Code-Blocks.html?dwl=codeblocks-20.03mingw-setup.exe
[2]: https://sourceforge.net/projects/codeblocks/files/Binaries/20.03/Windows/codeblocks-20.03mingw-setup.exe
[3]: https://img.imgdd.com/f78c9fe4-8495-48b0-acde-49bff9e0b551.png
[4]: https://img.imgdd.com/fce64ef9-58bc-4ed7-b938-c329229f2554.png
[5]: https://img.imgdd.com/d5a62e99-797d-4ca1-8006-8a1009b2d041.png
[6]: https://img.imgdd.com/d2c75a72-aa70-4803-a227-4100a77f4eb4.png
[7]: https://img.imgdd.com/f439868a-1170-4bc9-a60b-a7d60909b941.png
[8]: https://img.imgdd.com/9e25e83a-4737-4330-ad26-e6885c42c1f8.png
[9]: https://img.imgdd.com/b5075ab5-e0bd-4898-a829-adf438f43182.png
[10]: https://img.imgdd.com/942c6c23-3c61-49bb-b718-933becb15b92.png
[11]: https://img.imgdd.com/ceb0b125-f1d2-4329-9916-c66e49d60e19.png
[12]: https://img.imgdd.com/4edde2f3-a873-4ecc-981b-3bf6babddc9f.png
[13]: https://img.imgdd.com/e9737977-1e1c-47e8-9c35-93b6a4383a42.png
