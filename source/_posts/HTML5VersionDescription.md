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
1.首先，语义化，顾名思义，就是你写的HTML结构，是用相对应的有一定语义的英文字母（标签）表示的，标记的，因为HTML本身就是标记语言。不仅对自己来说，容易阅读，书写。别人看你的代码和结构也容易理解，甚至对一些不是做网页开发的人来说，也容易阅读。那么，我们以后再开发的过程中，一定要注意了，尽量使用官方的有语义的标签，不要再使用一堆无意义的标签去堆你的结构。

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
下面我引用了一个语义化标签的表格(做得有点像元素周期表)

{% asset_img html-tag.png %}

# html5的兼容性问题

使用html5的标签在一些旧版本浏览器它是不显示的,这时候我们该怎么兼容这些浏览器呢,下面我们来介绍一下解决方法:

## 兼容性解决方法1
以header标签为例:

1. 设置该标签的样式属性`display: block`
2. 通过dom的方式添加这个标签 `document.createElement('header')`  
3. 这样我们的header标签就可以在旧的浏览器里面显示了

## 兼容性解决方法2

这个方法其实就是对上面的方法的补全,因为上面的方法只对header有效,但是html5的标签不可能只有header,所以我们需要引用外部的js库来帮我们把其余的html5标签都做上以上的工作

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/html5shiv/3.7.3/html5shiv.js"></script>
```

上面的例子就是引用外部js库来完成对就浏览器不支持html5标签的兼容支持

# audio 和 video
audio和video是html5的新标签,audio是影评播放器video是视频播放器当然也是可以播放音频的.

这两个标签的出现可以让我们不需要再依赖flash和silverlight这些插件就能原生的支持多媒体的播放.只需简单的添加audio标签或者video标签到我们的html代码当中就可以显示相应的播放器了.

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
> 使用这两个html5标签需要考虑兼容性问题,在各个浏览器的默认样式都可能不一样

> 特别注意:有时候你们会发现video标签在chrome浏览器的自动播放是随机的但是通过往video标签添加`muted`静音属性之后,则在chrome浏览器能自动播放(这其实是有原因的:下面我来给出解析)

>> video在chrome的特殊表现原因

如果你刚开始使用chrome浏览器并且没有任何浏览记录,则chrome会在超过1000多个热门网站上自动播放带声音的视频,之后chrome则随着用户浏览的网页的习惯来学习和改变这个自动播放的网站列表,并且在你最经常访问的网站上应许带声视频自动播放,而相反则会阻止你不太常访问的网站的带声视频的自动播放.google产品经理解析过:当你调教chrome浏览器时,你会发现你时不时的需要点击播放按流才会播放视频.但是总体来说这个策略会阻止大约一半的没必要的自动播放情况.所以当你第一次访问新网站时你可以避免一些不必要的噪音打扰.[引用于](https://www.theverge.com/2018/5/3/17251104/google-chrome-66-autoplay-sound-videos-mute)

# html5 form 新特性

这里有14个新的form属性我们将会在下面的段落介绍和接触:

* placeholder
* list
* formaction
* autofocus
* multiple
* formentype
* autocomplete
* novalidate
* formmethod
* required
* formnovalidate
* formtarget
* pattern
* form

## placeholder
第一个属性就是placeholder,中文直译就是占位符.当输入框没有输入任何字符串时,如果设置了placeholder的值的话,输入框会默认显示placeholder的字符,这个字符可以当做提示性的消息不能当做输入框的值.

{% raw %}
<p data-height="265" data-theme-id="0" data-slug-hash="MBKBoN" data-default-tab="html,result" data-user="somiframe" data-embed-version="2" data-pen-title="input placeholder" class="codepen">See the Pen <a href="https://codepen.io/somiframe/pen/MBKBoN/">input placeholder</a> by somi (<a href="https://codepen.io/somiframe">@somiframe</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
{% endraw %}

## autofocus
`autofocus`能实现它字面上的意思:自动获取焦点,添加这个属性到input可以使input在页面渲染完成后自动把光标对焦到该input中.

{%raw%}
<p data-height="265" data-theme-id="0" data-slug-hash="rrxrqe" data-default-tab="html,result" data-user="somiframe" data-embed-version="2" data-pen-title="input autofocus" class="codepen">See the Pen <a href="https://codepen.io/somiframe/pen/rrxrqe/">input autofocus</a> by somi (<a href="https://codepen.io/somiframe">@somiframe</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
{%endraw%}

## autocomplete
`autocomplete`属性可以帮助用户根据先前的数据来完成表单输入框的输入.这个属性默认是自动填充内容的.
如果你想不要这个自动填充效果只需要把这个`autocomplete`设置为`off`就可以了.

{%raw%}
<p data-height="265" data-theme-id="0" data-slug-hash="KBVBLK" data-default-tab="html,result" data-user="somiframe" data-embed-version="2" data-pen-title="input autocomplete" class="codepen">See the Pen <a href="https://codepen.io/somiframe/pen/KBVBLK/">input autocomplete</a> by somi (<a href="https://codepen.io/somiframe">@somiframe</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
{%endraw%}

## required
`required`属性无需太多的介绍了,相信很多人在表单使用的时候都会用到这个.其实就是把带有`required`属性的input设置为必填项.

{%raw%}
<p data-height="265" data-theme-id="0" data-slug-hash="WKrgve" data-default-tab="html,result" data-user="somiframe" data-embed-version="2" data-pen-title="input required" class="codepen">See the Pen <a href="https://codepen.io/somiframe/pen/WKrgve/">input required</a> by somi (<a href="https://codepen.io/somiframe">@somiframe</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
{%endraw%}

## pattern

`pattern`属性可能是一个领开发人员非常兴奋的东西了.它可以通过使用正则表达式来校验输入框的值.

{%raw%}
<p data-height="265" data-theme-id="0" data-slug-hash="MBKPxZ" data-default-tab="html,result" data-user="somiframe" data-embed-version="2" data-pen-title="input pattern" class="codepen">See the Pen <a href="https://codepen.io/somiframe/pen/MBKPxZ/">input pattern</a> by somi (<a href="https://codepen.io/somiframe">@somiframe</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
{%endraw%}

## list 和 datalist 元素
`list` 属性允许用户关联一个带制定项的可选列表(datalist).input输入框里面的`list`属性的值一定要跟`datalist`的id保持一致这样才能关联起来.

{% raw %}
<p data-height="265" data-theme-id="0" data-slug-hash="qybQKr" data-default-tab="html,result" data-user="somiframe" data-embed-version="2" data-pen-title="input list attribute" class="codepen">See the Pen <a href="https://codepen.io/somiframe/pen/qybQKr/">input list attribute</a> by somi (<a href="https://codepen.io/somiframe">@somiframe</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
{% endraw %}

## multiple
`multiple`属性可以让input接受多个值.

{%raw%}
<p data-height="265" data-theme-id="0" data-slug-hash="WKrLbe" data-default-tab="html,result" data-user="somiframe" data-embed-version="2" data-pen-title="input multiple" class="codepen">See the Pen <a href="https://codepen.io/somiframe/pen/WKrLbe/">input multiple</a> by somi (<a href="https://codepen.io/somiframe">@somiframe</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
{%endraw%}

## novalidate 和 formnovalidate
`novalidate`和`formnovalidate`属性可以让form表单在提交的时候不校验内容.`formvalidate`可以在type类型为`submit`和`image`的input中,而`novalidate`只能添加到`form`元素中.

{%raw%}
<p data-height="265" data-theme-id="0" data-slug-hash="wxMRoV" data-default-tab="html,result" data-user="somiframe" data-embed-version="2" data-pen-title="form novalidate" class="codepen">See the Pen <a href="https://codepen.io/somiframe/pen/wxMRoV/">form novalidate</a> by somi (<a href="https://codepen.io/somiframe">@somiframe</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
{%endraw%}

## form 
`form`属性可以关联`input`,`select`或者`textarea`元素到`form`属性指定的form表单中即使是处于form外部也可以关联.

{%raw%}
<p data-height="265" data-theme-id="0" data-slug-hash="oMbJeM" data-default-tab="html,result" data-user="somiframe" data-embed-version="2" data-pen-title="input form" class="codepen">See the Pen <a href="https://codepen.io/somiframe/pen/oMbJeM/">input form</a> by somi (<a href="https://codepen.io/somiframe">@somiframe</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
{%endraw%}


## formaction, formenctype, formmethod, 和 formtarget
这是个新的属性如果把前面的form都去掉之后再看看是不是有点眼熟?没错它们就是form元素的属性`action`,`enctype`,`method`,`target`.但是跟form表单的属性不同的是它们只用在type为`submit`和`image`的input中.
{%raw%}
<p data-height="265" data-theme-id="0" data-slug-hash="djGwBL" data-default-tab="html,result" data-user="somiframe" data-embed-version="2" data-pen-title="formaction, formenctype, formmethod, 和 formtarget" class="codepen">See the Pen <a href="https://codepen.io/somiframe/pen/djGwBL/">formaction, formenctype, formmethod, 和 formtarget</a> by somi (<a href="https://codepen.io/somiframe">@somiframe</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
{%endraw%}


# html5 dom selector
html5新增一个新的选择器;

`document.querySelector(arg)`,`document.querySelectorAll(arg)`,
`document.getElementsByClassName(arg)`

能返回被选择的dom元素数组.


# html5 element.classList

html5的一个新特性就是在element里面的属性classList
它包含有六个方法:

 `classList.add()`,`classList.remove()`,`classList.item()`,`classList.toggle()`,`classList.contains()`,`classList.replace()`.


# html5 element.dataset

`element.dataset`是html5对元素新增的一个自定义属性的特性:

当需要往元素节点添加一些自定义数据的时候可以通过添加以`data-`为前缀的自定义数据,例如:

```html
<div data-name="somi" data-age="18" id="testdom">testdom</div>
<script>
    console.log(document.getElementById('testdom').dataset.age) //18
    console.log(document.getElementById('testdom').dataset.somi) //somi
</script>
```


# html5 FileReader

`FileReader`允许网页程序异步读取本地文件内容.

{%raw%}
<p data-height="265" data-theme-id="0" data-slug-hash="MByGeK" data-default-tab="js,result" data-user="somiframe" data-embed-version="2" data-pen-title="html5 filereader" class="codepen">See the Pen <a href="https://codepen.io/somiframe/pen/MByGeK/">html5 filereader</a> by somi (<a href="https://codepen.io/somiframe">@somiframe</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
{%endraw%}

# html5 network state

{%raw%}
<p data-height="265" data-theme-id="0" data-slug-hash="bjpjMx" data-default-tab="js,result" data-user="somiframe" data-embed-version="2" data-pen-title="html5 network state" class="codepen">See the Pen <a href="https://codepen.io/somiframe/pen/bjpjMx/">html5 network state</a> by somi (<a href="https://codepen.io/somiframe">@somiframe</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
{%endraw%}

