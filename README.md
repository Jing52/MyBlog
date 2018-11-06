# MyBlog
我的博客的备份
# 前言

之前搭建的博客基本功能已经实现了，现在就折腾着好好维护一下[我的博客](https://nullcxy.github.io/)了，于是参考着别人的博客添加一些小功能，并且整理了下来。

<!-- more -->

新搭建的博客的默认主题都是`landscape`，我的主题是基于[`yelee`]( https://github.com/MOxFIVE/hexo-theme-yelee)风格的，作者也是在[hexo-theme-yilia](https://github.com/litten/hexo-theme-yilia)的基础上进行的修改。

具体的使用可以参考[官方文档](http://moxfive.coding.me/yelee/)

首先给大家介绍下添加的功能吧

# 主题更改

## 下载主题

```
git clone https://github.com/MOxFIVE/hexo-theme-yelee.git
```

## 修改主题

打开项目目录下的_config.yml文件

主题更改，注意的是在yelee前面有个空格

```
theme: yelee
```

# 语言更换

打开项目目录下的_config.yml文件

```
# Site
language: zh-Hans
```

目前可用语言:

| **en**         | **English**               | **英语**     |
| -------------- | ------------------------- | ------------ |
| **zh-Hans**    | **Chinese (Simplified)**  | **大陆简体** |
| **zh-Hant-HK** | **Chinese (Traditional)** | **港澳繁體** |
| **zh-Hant-TW** | **Chinese (Traditional)** | **台灣正體** |

# 个人头像

默认头像存储于 `yelee/source/img/avatar.png`

配置中对应填写 `/img/avatar.png`，可替换图片或指定新地址

`themes/yelee/_config.yml` 背景参数:

```yaml
avatar: /img/avatar.png
```

# 文章摘要

目前主题可使用两种方式在首页显示文章摘要而不是全文。

## 方法一: `<!-- more -->`

```diff
title: Hello World
date: 2015-12-03 00:00:00
---
<Excerpt in index | 首页摘要> 
<!-- more -->
<The rest of contents | 余下全文>
```

>  `<!-- more -->` 之前最好不要有空格等字符；

## 方法二: `description` in [Front-matter](https://hexo.io/zh-cn/docs/front-matter.html)

```diff
title: Hello World
date: 2015-12-03 00:00:00
description: "Welcome to Hexo! This is your very first post."
---
<Contents>
```

> 通过 `description` 添加的摘要只能为纯文本；

> `description` 中的内容加引号，可以避免一些程序错误，例如当内容里包含英文冒号时。

![摘要](https://user-gold-cdn.xitu.io/2018/11/6/166e7f7fa8dbe935?w=1240&h=419&f=png&s=164051)

# 主菜单

按下面格式添加边栏菜单，菜单前的 `#` 表示注释掉该行，即隐藏掉该条目

`themes/yelee/_config.yml` 背景参数:

```yaml
menu:
  主页: /
  所有文章: /archives/
  #随笔: /tags/随笔
  标签云: /tags/
  关于我: /about/
```

# 标签云

使用 Hexo 命令新建一个名为 `tags` 的页面即可

```
hexo new page tags
```

> 该页面标题可以在文件 `\hexo\source\tags\index.md` 中修改

> 同一篇文章设置多个分类后的问题 [issue#4](https://github.com/MOxFIVE/hexo-theme-yelee/issues/4)

![标签云](https://user-gold-cdn.xitu.io/2018/11/6/166e7f7fa90cb2c7?w=1240&h=628&f=png&s=138149)

# 关于我的页面

使用 Hexo 命令新建一个名为 `about` 的页面即可

```
hexo new page about
```

> 该页面内容在文件 `\hexo\source\about\index.md` 中修改

![关于我](https://user-gold-cdn.xitu.io/2018/11/6/166e7f7fa915e303?w=1240&h=345&f=png&s=38050)

# 本地搜索

使用搜索需先安装对应插件，用于生成索引数据

> 插件主页: [hexo-generator-search](https://github.com/PaicHyperionDev/hexo-generator-search)

> `#on: true` 改为 `on: true`即为启用搜索

```yaml
search: 
  #on: true
  onload: false
```

`onload: true` : 索引数据 `search.xml` 随页面一起加载 `[效率优先]
`

`onload: false` : 当激活搜索框时再下载索引数据 `[按需加载]

![搜索](https://user-gold-cdn.xitu.io/2018/11/6/166e7f7fa9128a91?w=592&h=1102&f=png&s=156188)

# 站点小图标

若将图标存储于 `yelee/source/favicon.png`

则配置中对应填写 `/favicon.png`，另外填网络图片的地址也可

`themes/yelee/_config.yml` 背景参数:

```
favicon: /favicon.png
```

![图标](https://user-gold-cdn.xitu.io/2018/11/6/166e7f7fa9247685?w=390&h=112&f=png&s=25205)

# 社交图标

去掉设置前的 `#` 再填写链接即可

`themes/yelee/_config.yml` 背景参数:

```
subnav:
  Email: "mailto:1287530995@qq.com"
  #新浪微博: "sina weibo"
  GitHub: https://github.com/nullcxy
  #V2EX: "#"
  #RSS: "/atom.xml"
```

> 设置 Email 时保留 `mailto:` 可考虑加密邮件地址 <http://ctrlq.org/encode/>

> 使用 RSS 需先安装对应插件 <https://github.com/hexojs/hexo-generator-feed>

![社交](https://user-gold-cdn.xitu.io/2018/11/6/166e7f7fa93f4cfb?w=516&h=224&f=png&s=20006)

# 网站成立年份

`themes/yelee/_config.yml` 背景参数:

```
since: 2016
```

> 默认为 `2016`，若填入年份小于当前年份，则显示为 `2015-2016` 类似的格式

![年份](https://user-gold-cdn.xitu.io/2018/11/6/166e7f7fdbe689eb?w=428&h=186&f=png&s=9089)

# 背景图片

背景图文件所在路径:

```
/yelee/source/background/
```

`themes/yelee/_config.yml` 背景参数:

```yaml
background_image: 5
```

- 默认值为5，可按需修改
- "5": 设置`/yelee/source/background/`文件夹中 `bg-1.jpg` 到 `bg-5.jpg` 这5张图片为背景
- "0": 取消网页背景图，使用淳朴的灰白主题

![背景](https://user-gold-cdn.xitu.io/2018/11/6/166e7f7fdc81a038?w=1240&h=709&f=png&s=592278)



# 文章目录

配置中启用目录

`themes/yelee/_config.yml` 背景参数:

```yaml
toc:
  on: true
```

指定文章中关闭目录 `toc: false`

```
title: Hello World
date: 2015-08-19 00:00:00
toc: false
---
```

![目录](https://user-gold-cdn.xitu.io/2018/11/6/166e7f7fdbf2d5fb?w=600&h=468&f=png&s=61700)

# 版权

配置中启用目录

`themes/yelee/_config.yml` 背景参数:

```yaml
copyright: true
```

指定文章中关闭目录 `original: false`

```yaml
title: Hello World
date: 2015-08-19 00:00:00
original: false
---
```

原始链接设置

修改 [站点配置](https://hexo.io/zh-cn/docs/configuration.html#%E7%BD%91%E5%9D%80) 文件中 `url` 的值为你的网站域名

```
url: http://MOxFIVE.xyz
```

![版权](https://user-gold-cdn.xitu.io/2018/11/6/166e7f7fdc1548c1?w=1240&h=288&f=png&s=135941)

# 左边主菜单鸟屋

`themes/yelee/_config.yml` 背景参数:

## 左边栏鸟屋

![边栏鸟屋](https://user-gold-cdn.xitu.io/2018/11/6/166e7f7fecc82836?w=275&h=156&f=png&s=7608)

## 关闭鸟屋

```yaml
# 边栏多标签切换
tagcloud: false
```

## 友情链接

```yaml
## 编辑友链
friends:
  Hexo: https://hexo.io
  GitHub: https://pages.github.com/
  MOxFIVE: http://moxfive.xyz/

## 关闭友链
friends: false
```

## 关于我

```
# 是否开启“关于我”。
aboutme: 专注于前端

# 关闭“关于我”
aboutme: false
```

# 评论

## 来必力评论

### 介绍

yelee原生是支持Disqus、多说和有言的，可以参考[官网-评论系统](http://moxfive.coding.me/yelee/2.Basic-Usage/comment.html)

但是多说已经关闭，有言支持又不友好，又发现Disqus在手机上展示不出来，发现还需要翻墙，那实在对用户太不友好了，于是我选择使用[来必力](https://www.livere.com/)评论系统

![来必力](https://user-gold-cdn.xitu.io/2018/11/6/166e7f7fe14a13b8?w=1240&h=518&f=png&s=438156)

### 注册

注册后可以查看数据分析

![数据分析](https://user-gold-cdn.xitu.io/2018/11/6/166e7f7ffb193c60?w=1240&h=744&f=png&s=109674)

代码管理，我们需要用到这个data-uid

![代码](https://user-gold-cdn.xitu.io/2018/11/6/166e7f8006d5cf22?w=1240&h=761&f=png&s=253156)

## 集成

### 添加data-uid

打开`theme/yelee/_config.yml`，添加配置信息

```
 livere:
    on: true
    livere_uid: Your uid
```

### 创建ejs文件

在`themes/yelee/layout/_partial/comments`文件夹创建`livere.ejs`文件，将代码拷贝进去，将你注册后的代码拷贝到<section></section>里面。

```
<section class="livere" id="comments">
    <!-- 来必力City版安装代码 -->
    <div id="lv-container" data-id="city" data-uid="Your uid">
    <script type="text/javascript">
   (function(d, s) {
       var j, e = d.getElementsByTagName(s)[0];

       if (typeof LivereTower === 'function') { return; }

       j = d.createElement(s);
       j.src = 'https://cdn-city.livere.com/js/embed.dist.js';
       j.async = true;

       e.parentNode.insertBefore(j, e);
       })(document, 'script');
    </script>
    <noscript> 为正常使用来必力评论功能请激活JavaScript</noscript>
    </div>
    <!-- City版安装代码已完成 -->
</section>
```

### 追加逻辑判断

打开`themes/yelee/layout/_partial/article.ejs`，在下图位置插入下面的逻辑判断代码

```
else if (theme.livere.on) { %>
	<%- partial('comments/livere') %>
<% } 
```

![判断](https://user-gold-cdn.xitu.io/2018/11/6/166e7f8010c2a007?w=792&h=688&f=png&s=190947)

如此，就大功告成，可以进行留言了，看下效果：

![评论](https://user-gold-cdn.xitu.io/2018/11/6/166e7f8013508b1e?w=1240&h=266&f=png&s=41836)

# 文章字数统计以及阅读时长

## 前言

next主题是已经集成这个功能的，但是yelee就需要我们自己配置了，可以看下官网对[hexo-wordcount](https://link.jianshu.com/?t=https%3A%2F%2Fwww.npmjs.com%2Fpackage%2Fhexo-wordcount)的介绍

## 集成

### 安装hexo-wordcount

```
npm i --save hexo-wordcount
```

### 文件配置

在`yelee/layout/_partial/post/word.ejs`下创建`word.ejs`文件：

```
<div style="margin-top:10px;">
    <span class="post-time">
      <span class="post-meta-item-icon">
        <i class="fa fa-keyboard-o"></i>
        <span class="post-meta-item-text">  字数统计: </span>
        <span class="post-count"><%= wordcount(post.content) %>字</span>
      </span>
    </span>

    <span class="post-time">
      &nbsp; | &nbsp;
      <span class="post-meta-item-icon">
        <i class="fa fa-hourglass-half"></i>
        <span class="post-meta-item-text">  阅读时长: </span>
        <span class="post-count"><%= min2read(post.content) %>分</span>
      </span>
    </span>
</div>
```

然后添加逻辑判断

打开 `themes/yelee/layout/_partial/article.ejs`

```
<% if(theme.word_count && !post.no_word_count){ %>
	<%- partial('post/word') %>
<% } %>
```

在下图位置添加

![判断](https://user-gold-cdn.xitu.io/2018/11/6/166e7f808285b09a?w=1074&h=488&f=png&s=123625)

`word_count` 是主题`_config.yml`中配置是否需要添加字数统计功能控制 flag，

`no_word_count`即配置文章是否需要显示字数统计的功能。

看一下效果吧

![统计](https://user-gold-cdn.xitu.io/2018/11/6/166e7f8083075b7e?w=1236&h=358&f=png&s=47257)

# 网易云音乐

## 前言

对于一名`Android`开发者来讲，`网易云音乐`是必不可少的功能，那博客也要添加这个功能咯。	

## 集成

`MarkDown` 是支持 `h5` 代码的，所以集成过来很简单，打开[网易云音乐](https://link.jianshu.com/?t=https%3A%2F%2Fmusic.163.com)，搜索你想要的音乐

![网易云](https://user-gold-cdn.xitu.io/2018/11/6/166e7f80874a83b0?w=1240&h=1011&f=png&s=308204)

点击对应的`生成外链播放器`，当然前提是要有版权的，很多音乐还是没有版权的，可以设置尺寸，是否自动播放，最后拷贝对应的代码，拷贝到你想要放置的位置即可。

![iframe](https://user-gold-cdn.xitu.io/2018/11/6/166e7f8088f6f30d?w=1240&h=1108&f=png&s=181898)

看一下效果吧

![音乐](https://user-gold-cdn.xitu.io/2018/11/6/166e7f808e5391a6?w=1240&h=328&f=png&s=52942)

# 鼠标点击桃心效果

## 前言

如果鼠标点击的时候出现特效，那一定会使整个博客的颜值提升一大截

## 集成

### 拷贝需要的文件

进入[我的备份](https://github.com/nullcxy/MyBlog)，拷贝需要的文件

![桃心](https://user-gold-cdn.xitu.io/2018/11/6/166e7f80a82da073?w=420&h=484&f=png&s=43854)

### 添加配置

打开`themes/yelee/layout/_partial/after-footer.ejs`文件，添加刚刚添加文件的配置。

```
<script type="text/javascript" src="/resources/float.js"></script>
<script type="text/javascript" src="/resources/love.js"></script>
<script type="text/javascript" color=0,104,183 opacity=1 zindex=-1 count=50 src="/resources/particle.js"></script>
<script type="text/javascript" src="/resources/typewriter.js"></script>
```

![配置](https://user-gold-cdn.xitu.io/2018/11/6/166e7f80ac5dd7df?w=1240&h=118&f=png&s=118866)

点击页面查看一下效果

![桃心效果](https://user-gold-cdn.xitu.io/2018/11/6/166e7f80b2fb6f3d?w=662&h=410&f=png&s=41910)

# 添加可爱的萌妹子或者萌宠

## 前言

如果在页面上添加个萌宠或者萌妹纸，那是不是很卡哇伊呢。大家可以查看[源码](https://github.com/xiazeyu/live2d-widget-models)来挑选自己喜欢的模型。

## 集成

### 安装

```
npm install --save hexo-helper-live2d
```

### 配置

在站点的 `_config.yml` 下配置

```
live2d:
  enable: true
  scriptFrom: local
  model:
    use: live2d-widget-model-miku
  display:
    position: right
    width: 150
    height: 300
  mobile:
    show: true
```

其中，live2d.model.use使用来配置对应的萌宠模型，我这边是live2d-widget-model-miku

看一下效果吧

![萌妹](https://user-gold-cdn.xitu.io/2018/11/6/166e7f812cb9f099?w=1240&h=1174&f=png&s=603476)

# 添加网站运行时间

## 前言

可以实时展示自己的博客的运行时间，还是蛮有成就感的。

## 集成

在 `hexo/themes/yelee/layout` 文件夹下找到你的 `footer` 文件，即脚布局文件，在对应的位置添加一下代码。

```
<span id="timeDate">载入天数...</span><span id="times">载入时分秒...</span>
<script>
    var now = new Date(); 
    function createtime() { 
        var grt= new Date("02/14/2018 12:49:00");//此处修改你的建站时间或者网站上线时间 
        now.setTime(now.getTime()+250); 
        days = (now - grt ) / 1000 / 60 / 60 / 24; dnum = Math.floor(days); 
        hours = (now - grt ) / 1000 / 60 / 60 - (24 * dnum); hnum = Math.floor(hours); 
        if(String(hnum).length ==1 ){hnum = "0" + hnum;} minutes = (now - grt ) / 1000 /60 - (24 * 60 * dnum) - (60 * hnum); 
        mnum = Math.floor(minutes); if(String(mnum).length ==1 ){mnum = "0" + mnum;} 
        seconds = (now - grt ) / 1000 - (24 * 60 * 60 * dnum) - (60 * 60 * hnum) - (60 * mnum); 
        snum = Math.round(seconds); if(String(snum).length ==1 ){snum = "0" + snum;} 
        document.getElementById("timeDate").innerHTML = "本站已安全运行 "+dnum+" 天 "; 
        document.getElementById("times").innerHTML = hnum + " 小时 " + mnum + " 分 " + snum + " 秒"; 
    } 
setInterval("createtime()",250);
</script>
```

运行效果

![运行时长](https://user-gold-cdn.xitu.io/2018/11/6/166e7f812cc8c69b?w=872&h=266&f=png&s=75171)

