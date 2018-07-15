---
title: html5
date: 2018-07-14 13:33:17
tag: 
- 开课吧
- html5
---
# html5版本

下面的代码为html5版本的代码
```html 
    <!doctype html>
    <html lang="en">
        <head>
            <meta charset="utf-8">
            <title>document</title>
        </head>
    </html>
```

# html5语义化标签
## 什么是语义化?
1.首先，语义化，顾名思义，就是你写的HTML结构，是用相对应的有一定语义的英文字母（标签）表示的，标记的，因为HTML本身就是标记语言。不仅对自己来说，容易阅读，书写。别人看你的代码和结构也容易理解，甚至对一些不是做网页开发的人来说，也容易阅读。那么，我们以后再开发的过程中，一定要注意了，尽量使用官方的有语义的标签，不要再使用一堆无意义的标签去堆你的结构。

怎么知道，自己的页面结构是否语义化，那就要看你的HTML结构，在去掉CSS样式表之后，是否，依然能很好的呈现内容的结构，代码结构。也就是说，脱掉css的外衣，依然头是头，脚是脚。赤裸裸的完整的一篇文档。这也就是，语义化之后文档的效果。

2.其实语义化，也无非就是自己在使用标签的时候多使用有英文语义的标签，比如h标签，在HTML中就是就是用来定义标题，还有p标签，英文是paragraph段落，table表格标签,等等。

## 语义化例子
请看下面的代码例子:
```html
    <!--语义化-->
    <!doctype html>
    <html lang="en">
        <head>
            <meta charset="utf-8">
            <title>title</title>
        </head>
        <body>
            <header><!--语义化标签-->
                <h1>html5语义化标签</h1>
                <nav><!--语义化标签-->
                    <h1>导航</h1>
                    <ul><!--语义化标签-->
                        <li>章节</li><!--语义化标签-->
                        <li>标签</li>
                        <li>热门</li>
                    </ul>
                </nav>
            </header>
        </body>    
    </html>
```

```html
    <!--非语义化-->
    <!doctype html>
    <html lang="en">
        <head>
            <meta charset="utf-8">
            <title>title</title>
        </head>
        <body>
            <div class="header">
                <h1>html5非语义化例子</h1>
                <div class="nav">
                    <h1>导航</h1>
                    <ul>
                        <li>章节</li>
                        <li>标签</li>
                        <li>热门</li>
                    </ul>
                </div>
            </div>
        </body>    
    </html>
```
## 语义化标签
下面我引用了一个语义化标签的表格(做得有点像元素周期表)

{% asset_img html-tag.png %}

# html5的兼容性问题

使用html5的标签在一些旧版本浏览器它是不显示的,这时候我们该怎么兼容这些浏览器呢,下面我们来介绍一下解决方法:

## 兼容性解决方法1
以header标签为例:

1. 设置该标签的样式属性`display: block`
2. 通过dom的方式添加这个标签 `document.createElement('header')`  
3. 这样我们的header标签就可以在旧的浏览器里面显示了

## 兼容性解决方法2

这个方法其实就是对上面的方法的补全,因为上面的方法只对header有效,但是html5的标签不可能只有header,所以我们需要引用外部的js库来帮我们把其余的html5标签都做上以上的工作

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/html5shiv/3.7.3/html5shiv.js"></script>
```

上面的例子就是引用外部js库来完成对就浏览器不支持html5标签的兼容支持

# audio 和 video
audio和video是html5的新标签,audio是影评播放器video是视频播放器当然也是可以播放音频的.

这两个标签的出现可以让我们不需要再依赖flash和silverlight这些插件就能原生的支持多媒体的播放.只需简单的添加audio标签或者video标签到我们的html代码当中就可以显示相应的播放器了.

## audio使用
```html 
<audio controls>
    <srouce src="horse.ogg" type="audio/ogg"/>
    <srouce src="horse.mp3" type="audio/mpeg"/>
  Your browser does not support HTML5 audio.
</audio>
```

## video使用
```html 
<video width="400" controls>
  <source src="http://vjs.zencdn.net/v/oceans.mp4" type="video/mp4">
  Your browser does not support HTML5 video.
</video>
```
> 使用这两个html5标签需要考虑兼容性问题,在各个浏览器的默认样式都可能不一样

> 特别注意:有时候你们会发现video标签在chrome浏览器的自动播放是随机的但是通过往video标签添加`muted`静音属性之后,则在chrome浏览器能自动播放(这其实是有原因的:下面我来给出解析)

>> video在chrome的特殊表现原因

如果你刚开始使用chrome浏览器并且没有任何浏览记录,则chrome会在超过1000多个热门网站上自动播放带声音的视频,之后chrome则随着用户浏览的网页的习惯来学习和改变这个自动播放的网站列表,并且在你最经常访问的网站上应许带声视频自动播放,而相反则会阻止你不太常访问的网站的带声视频的自动播放.google产品经理解析过:当你调教chrome浏览器时,你会发现你时不时的需要点击播放按流才会播放视频.但是总体来说这个策略会阻止大约一半的没必要的自动播放情况.所以当你第一次访问新网站时你可以避免一些不必要的噪音打扰.[引用于](https://www.theverge.com/2018/5/3/17251104/google-chrome-66-autoplay-sound-videos-mute)

