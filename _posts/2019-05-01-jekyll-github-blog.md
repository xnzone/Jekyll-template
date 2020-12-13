---
layout: post 
title: "jekyll搭建github个人博客"
thumb: /img/in-post/thumbs/wiki.png
category: wiki
tags:  "blog"
---

# 写在前面
花了大概两天的时间把这个博客搭建好了，那么第一篇博客就献给如何搭建这个博客吧。

首先要感谢[fooleap](https://blog.fooleap.org/)提供的模板，本博客在原有的基础上做了一部分修改。喜欢这种简单的风格。同时还参考了[Hux](http://huangxuan.me/)的一部分代码

另外转载请注明来源，尊重别人的劳动成果。如果使用我的模板的话，麻烦给个star可以吧

其实用jekyll搭建github的个人博客无非分为以下几个步骤
- 生成自己的个人博客主页
- 修改相关配置
- 安装相关博客插件

下面讲对此一一讲解

# 生成自己的博客主页
## 注册github账号
这一步应该不用多说吧。相信来看这个博客的人，应该都有了自己的同性交友网站的账号了。
## fork模板
这一步你可以fork[我的模板](https://github.com/znfang/znfang.github.io)，当然你也可以fork上述我参考的jekyll官方模板,或者其他任何人的模板

可以参照下列步骤进行

![fork](/img/in-post/jekyll&github/fork.png){:width="100%"}
<!-- <img src="/img/in-post/jekyll&github/fork.png" /> -->

## 修改repo名字
fork之后，你会在自己的github账号下看到有这个repo，然后最后一个点击settings

![settings](/img/in-post/jekyll&github/settings.png){:width="100%"}

进入setting界面后，修改repo的名字，将其修改为 你的githu账号名.github.io的形式。如我的修改为znfang.github.io

![rename](/img/in-post/jekyll&github/rename.png){:width="100%"}

如果一切顺利的话，在浏览器中输入你刚刚输入的repo的名字，就可以看到我内容状态了，如我输入znfang.github.io。

![normal](/img/in-post/jekyll&github/normal.png){:width="100%"}

至此，自己的博客主页就已经生成完毕。接下来就是使用git配置自己的个人博客了。

## 一不小心404
上面都是正常的情况，如果你是正常的，那就直接跳过这一步，进行下一步的内容，但是如果你一不小心，打开那个地址时是404，那么请检查这几个内容
- repo名字是否设置正确
- 检查是否存在master分支
- 在setting界面，查看github pages选项是否显示正常
- 查看CNAME文件中是否存在其他域名，如果有，则删除CNAME中的域名或者替换成自己买的域名

如果上述几个选项都正常还404，那我也不知道了

# 修改相关配置
## git clone repo
这一步应该不需要多说，将自己账号下的repo，clone到本地进行修改.

<font color="#ff0000">注意:不要fork我的repo，否则后面push的时候，就一直提醒发到我的repo了</font>

## 安装jekyll
为了便于在本地调试，先把jekyll环境装好，安装jekyll环境，每种操作系统的安装步骤都不相同，本文由于是在linux操作系统下完成的，因此只说明linux系统下如何安装jekyll
>sudo apt-get install make build-essential    
sudo apt-get install ruby ruby-dev   

在~/.bashrc或者~/.zshrc中添加
>export GEM_HOME=$HOME/gems    
export PATH=$HOME/gems/bin:$PATH

使用gem安装jekyll和bundle
>gem install bundler    
gem install jekyll

具体的安装教程可以参考[云网牛站](https://ywnz.com/linuxyffq/4335.html)的操作

安装好jekyll之后，可以进入到刚刚git clone下来的repo，比如作者的目录是
>/home/znfang/Documents/blog/znfang.github.io
进入目录后，在此目录下打开终端，在终端中输入
>jekyll s    或者jekyll server
如果是低版本或者本地存在多个版本，则可以用
>bundle exec jekyll server

这两个命令是等价的。用此来启动服务器，如果不出意外是没有任何错误提示的，如果提示minima-theme can not found，可以在终端输入
>gem install minima-theme

或者出现其他的组件没有安装，则根据报错提示进行百度或者谷歌排查

如果警告gems已经被替换成plugins，则打开_config.yml文件，找到gems，将gems替换成pulgins即可，最中修改后的代码为
>\# Gems
plugins: [jekyll-paginate]

如果启动jekyll服务器时，没有任何错误，则可以在浏览器中输入
>localhost:4000    
或者    
127.0.0.1:4000

此时你应该可以看到博客界面，当然这个界面的内容都是别人的，如果你fork的是我的模板，则看到的应该是下面这个图，你需要修改相关的配置，使它成为你自己的

![normal](/img/in-post/jekyll&github/normal.png){:width="100%"}

## 网站架构
主要结构如下，看不懂是吧，我一开始也看不懂，但是我们可以在修改的过程中，去了解它。

![structure](/img/in-post/jekyll&github/structure.png){:width="100%"}

常用到的内容有[[1]][1]
>_config.yml    
img    
_includes    
_layouts    
_post

下面将逐一介绍该怎么使用这些文件

## 修改配置
### 修改_config.yml
config.yml文件主要是一些定义网站一些基本的东西，这个地方，你可以把所有关于其他人信息的东西修改成自己的。应该不需要多讲，一些英文描述都是很清楚的，有三个地方不要动，一个是Baidu Analytics，一个是Google Analytics，还有一个是disqus_username。这三个插件后面将会讲到，这个地方先不要动。

修改完成后，可以在本地看到相关的更新，如果要在域名上看到更新，则用git commit后，再用git push到远程分支即可。

### 修改_includes文件夹
这个文件夹下几个文件，只需要修改一个footer.html文件即可。这个文件只需要修改两个地方

将
>\<script async src="//dn-lbstatics.qbox.me/busuanzi/2.3/busuanzi.pure.mini.js"></script>

替换成
>\<script async src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>

- 调整你的博客初始运行的时间。这里有个bug，已经在代码中进行了注释

这两个是统计本站点访问的人数以及博客运行的时间，就是最底下的显示。

### 修改about.md
about.md是个人介绍，这个地方根据自己的兴趣修改。

### 修改img文件夹
这个文件夹放置的是博客使用的背景，以及文章中使用的图片（放置在img/in-post/文件夹下）。这个可根据自己的喜好修改。这个地方由于本博客主题页面限制问题，在插入图片时最好采用尾注的方式进行设置图片宽度。

总之，以上的文件修改的目的就是将别人的信息替换成自己的。一切以个人为准

### _post文件夹
这个文件夹是用来存放个人博客的，一般文件格式为'yyyy-mm-dd-'文件名称'.md'

# 插件安装
插件主要安装三个插件，一个是百度站点统计，一个是谷歌站点统计，一个是disqus评论
## 百度站点统计
打开[百度数据统计](https://tongji.baidu.com/web/welcome/login)网站，注册后，进入后打开管理界面，选择网站列表，点击新增网站.根据自己的情况填写内容

![baidu](/img/in-post/jekyll&github/baidu.png){:width="100%"}

填写好后，点击获取代码，复制hm.src这一行的最后一大串的数字和字母组成的编码，从问号开始，到最后。将其粘贴到_config.yml文件中的ba_track_id后面的值。如果要查看效果，则需要将代码push到远程repo

## 谷歌站点统计
同样的注册谷歌统计的账号，拿到track_id后，修改_config.yml文件即可

## disqus评论插件
首先到[disqus](https://disqus.com/)注册账号，注册完之后进入下面这个页面，如果没有进入的话，可以点右上角设置，add disqus to site 进入

![disqus-install](/img/in-post/jekyll&github/disqus-install.png){:width="100%"}

进入后填入相关信息，注意在short web中填入你github的username，比如我的是znfang，进入下一步后，选择jekyll，并且在setting界面，讲用户名设为你的github的username，然后打开_config.yml,将disqus_username修改为你自己的名字即可。

<font color="red">注意:使用disqus插件时，需要vpn，不然可能显示不成功</font>

至此就是整个的个人博客的搭建。然后开启自己的博客之旅吧

# 参考资料

[1]: https://github.com/qiubaiying/qiubaiying.github.io/wiki/ "博客搭建详细教程"