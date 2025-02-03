---
layout: post
title: minecraft基岩版纹理包制作
date: 2023-01-10T09:55:00+08:00
lastmod: 2023-04-22T06:41:06+08:00
status: publish
author: heiyedao
categories: 
  - 代码
  - 经验
tags: 
  - minecraft
  - 我的世界
  - 纹理包
  - 材质包
  - 制作教程
advancedSettings: 
cover: https://heiyedao.top/usr/uploads/2023/01/60992796.png
excerpt: 纹理包入门的教程
PostType: post
showToc: 1
---

# 首先熟悉一下纹理包的构成，本文仅讲解纹理包创建，贴图修改，文字修改
## 声明一个概念：纹理包和材质包的定义不同，材质包包括光影，光影不在纹理包的范围
**[纹理包模板 蓝奏][1]，密码:53hk，这个需要先下载，对照里面的文件理解更清楚**
## 一个完整的纹理包包括
credits:打败末影龙后显示的那段文字的文件夹
font: Minecraft Bedrock默认字体包
materials:应是渲染部分
models:实体模型json
sounds: Minecraft Bedrock音效包
texts:游戏中显示的所有文字所在的文件夹
**textures:材质文件夹**
ui:控制游戏UI的文件夹
blocks.json:方块模型文件
**loading_messages.json:游戏中的提示**
(tips)manifest.json:材质属性清单
manifest_publish.json:和上面的类似(在Minecraft商店中发布材质时会用到)
**pack_icon.png:纹理包图片**
sounds.json:音效文件
**splashes.json:进入游戏界面显示的小黄字**
### textures（方块贴图文件夹）目录下的文件
**blocks:方块贴图的文件夹**
colormap:一些生物群系的颜色渲染图文件夹
**entity:实体模型贴图文件夹**
**environment:生态环境贴图文件夹**
gui: UI贴图文件夹
**items:手持贴图文件夹**
map:地图贴图
**misc:放有带上南瓜的后遮挡视线的贴图**
**models:玩家盔甲装备贴图**
**painting:画**
particle:粒子效果贴图
ui: UI贴图
flame_atlas.png:动态贴图
flipbook_textures.json:实现游戏动态材质的
jsonitem_texture.json:控制手持贴图
terrain_texture.json:记录blocks文件夹中所有的贴图
textures_list.json:所有的材质列表

***加粗的是比较容易修改的地方，也是修改后见效比较快的地方***
# 重要文件讲解

## [manifest.json][2]（模板链接）
**这个json文件是纹理包的核心，包含材质名称,简介,版本和材质id**
文件模板
    {
        "format_version": 2,
        "header": {
            "description": "你的纹理包介绍",
            "name": "纹理包名称，可以使用§加数字改变颜色例子：§3黑夜岛",
            "uuid": "在网站上生成，网站地址https://uutool.cn/uuid/",
            "version": [0, 0, 0],	//你的纹理包版本号
            "min_engine_version": [1, 16, 0]  //纹理包需要的最低游戏版本
        },
        "modules": [
            {
                "description": "纹理包介绍，可以和上面不同",
                "type": "resources",	//这个是类型设置为纹理包，无需改动
            "uuid": "在网站上生成，网站地址https://uutool.cn/uuid/，要和前面的不同！！",
                    "version": [0, 0, 1]	//你的纹理包版本号
            }
        ]
    }
## pack_icon.png纹理包图片
这个必须是1:1比例大小的图片,建议不超过100kb
## [splashes.json][3]副标题,是主页面minecarft右下角的字
splashes模板
    {
      "splashes": [
        "test",
        "test"
      ]
    }
## [loading_messages.json][4]加载世界时候的文字
    {
      "loading_messages": [//加载世界时候的文字
        "本纹理包由黑夜岛制作",
        "……"
      ]
    }//按照此模板填写
## textures:材质文件夹
下面的文件夹我会一一讲解，贴图可以自己制作，下载下来用软件修改，如aseprite；或者去找其他允许二创的纹理包把贴图复制过来
### blocks 方块贴图
我一般在这里加上矿物描边，透明玻璃，底火，羊毛材质等
### entity 实体贴图
这个文件夹我改了床的贴图
### items 手持贴图文件夹
这里玩PVP的可以改工具贴图，如短剑等。加上了刷怪蛋贴图等
### models 玩家盔甲装备贴图
玩PVP的可以改一下啦
### painting 画的图片
这里就可以导入自己喜欢的图片啦，这里可以让世界[hidden]涩彩[/hidden]更丰富
### misc 带上南瓜头后的贴图
这里我放出没有去除遮挡视野的图片[pumpkinblur.png][5]，文件名无需更改，放在misc文件夹即可
### environment 生态环境贴图文件夹
这个文件夹也比较重要，可以更改挖掘方块的贴图（共十张）
然后就是天空背景，这个需要自己裁剪背景图片为大小相同的6张正方形图片，可以去找大佬制作好的，看看他们的图片连接顺序，**不要把图片顺序弄成，图片方向弄混，报错两行泪**。但Java版纹理包转基岩版需要更改图片方向这个需要自己调试了，两者的贴图文件不同需要进行裁剪和变换方向

**大家可以看视频操作**

<iframe src="//player.bilibili.com/player.html?aid=636386876&bvid=BV1Lb4y177FA&cid=505517820&page=1&high_quality=1&danmaku=0" allowfullscreen="allowfullscreen" width="100%" height="500" scrolling="no" frameborder="0" sandbox="allow-top-navigation allow-same-origin allow-forms allow-scripts"></iframe>

**这个视频操作出来的全景图不是360°全景图，作者自己也说了，如果想要好看的背景还是去找pvp纹理包里面比较好天空贴图使用，效果很好**

### ui 操作面板的贴图
这里是最好进阶的地方，需要你熟悉json语言使用方法、minecraft的格式要求，不容易上手，这篇文章讲不了这么多，略过
主页的背景贴图，这里和前面的天空背景一样，也需要裁成6张图片，麻烦的是它的文件顺序和天空贴图不同，需要修改

**纹理包讲解大概就是这些，这里只是引入门的教程，按照这里操作，一个简单的纹理包就可以制作出来**

  [1]: https://heiyedao.lanzouw.com/ijJNJ0klygif
  [2]: https://heiyedao.top/usr/uploads/2023/01/2918867742.json
  [3]: https://heiyedao.top/usr/uploads/2023/01/3981267547.json
  [4]: https://heiyedao.top/usr/uploads/2023/01/2941087290.json
  [5]: https://heiyedao.top/usr/uploads/2023/01/983475658.png
