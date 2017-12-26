title: 一个讨厌的Hexo报错(MODULE_NOT_FOUND)
date: 2016-9-01 18:29:00
description: 一个讨厌的Hexo报错(MODULE_NOT_FOUND)
categories:
- Hexo
tags: 
- Hexo
toc: true
author:
comments:
original:
permalink: 
---

　　**自用笔记：**本文属于自用笔记，不做详解，仅供参考。在此记录自己已理解并开始遵循的前端代码规范。What How Why
　　最近，使用Hexo遇到了很多问题，在设立进行整理。

<!-- more -->
问题描述，mac上hexo的命令今天突然出问题，所有hexo的命令都报错(Error: Cannot find module './build/Release/DTraceProviderBindings')，于是在网上搜索，发现遇到这个问题的朋友真不少，于是根据各种博客文章尝试，然而并没有什么卵用，最后还是在https://github.com/hexojs/hexo/issues/  上找到了解决的方法。

### Hexo 3.0 on Mac

报错信息图片：![hexo-error](/images/hexo-error.png) 

### 首先出现莫名其妙的 MODULE_NOT_FOUND 

```
{ [Error: Cannot find module './build/default/DTraceProviderBindings'] code: 'MODULE_NOT_FOUND' }
{ [Error: Cannot find module './build/Debug/DTraceProviderBindings'] code: 'MODULE_NOT_FOUND' }

```

参见 [Github上的问题1](https://github.com/hexojs/hexo-cli/issues/1)  。作者对此也没有权威解释，只是告诉加一个参数就可以了：

$ npm install -g hexo-cli --no-optional

or

$ npm install hexo --no-optional
if it doesn't work
try
$ npm uninstall hexo-cli -g
$ npm install hexo-cli -g

然而对于我并没有解决问题，我的是通过issue里面的这个答案解决的

> tommy351 commented on 17 Feb 2015
  Maybe it's related to  [trentm/node-bunyan#216](https://github.com/trentm/node-bunyan/issues/216) 
  
参考链接是https://github.com/trentm/node-bunyan/issues/216 ，执行命令：npm install bunyan，第一次还是报错，后来我先卸载npm uninstall bunyan,然后在执行npm install bunyan，在运行hexo的任何命令都正常工作了，此刻如卸重负，欢快的做自己想做的事情了！

### 补充：

#### The Wall

因为国内的网络情况，很多时候Ruby啊，Node的包管理器都会出现连接失效，这种情况下，或者使用代理（BTW：GoAgent已经不大好用了），或者使用国内的包镜像站，用代理的话，可以这么设置：

npm config set proxy=http://127.0.0.1:8087

不过用国内的镜像站应该是最省心的，改一下registry就好了：

npm config set registry=&quot;http://r.cnpmjs.org&quot;

如果你还遇到别的情况，参考这个链接吧，写的比较细： [npm_cross_wall](http://www.cnblogs.com/hustskyking/p/npm-cross-wall.html) 

#### hexo server

Hexo 3.0以后还有一个变化，就是server模块需要单独安装，在博客目录内执行如下命令即可：
npm install hexo-server --save

#### hexo generate

运行 hexo g 时发现，所有的markdown没有生成，发现和之前hexo版本不一样，需要来这么一下：

```
hexo init
npm install

```

#### github or git

Hexo 3.0后，需要把deployer的类型从github改成git，另外需要加入相应的包：

npm install hexo-deployer-git --save

最后，坑踩完了。需要提醒的是，遇到问题，主要参考hexo的github主页上的问题列表，作者tommy的主页，或者最后找不到只能谷而歌之。Happy blogging with Hexo 3.0!




