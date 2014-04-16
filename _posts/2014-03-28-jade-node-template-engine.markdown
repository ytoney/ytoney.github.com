---
layout: post
title: "about jade"
date: 2014-03-28 17:22
categories: categories/js
---

####实例：layout.jade —— 页面头部和脚部公共部分####

{% highlight html %}
doctype html
html(lang="en")
  head
    title iColor手机版
    meta(charset="UTF-8")
    meta(name="viewport",content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=0")
    meta(content="yes",name="apple-mobile-web-app-capable")
    meta(content="black",name="apple-mobile-web-app-status-bar-style")
    meta(content="telephone=no",name="format-detection")

    link(rel="stylesheet",href="css/bootstrap.css")
    link(rel="stylesheet",href="css/wap-v2.css")

    block head

  body.bg-gray
    div#header.bg-slash
      div.navbar-header
        block logoTitle
        button.navbar-toggle(type="button",data-toggle="collapse",data-target=".bs-navbar-collapse")
          span.sr-only Toggle navigation
          - for (var x = 0; x < 3; x++)
            span.icon-bar
      - var navbar_collapse = ['collapse', 'navbar-collapse', 'bs-navbar-collapse']
      div(class=navbar_collapse,role="navigation")
        span.nav-collarrow
        ul.nav.navbar-nav.navbar-right
          each href, val in {'首页':'home.html','对话名人':'famous.html','业主通道':'channel.html','装修图库':'design_images.html','设计王牌':'designers.html','设计鉴赏':'#'}
            li
              a(href=href)
                span.pull-right &rsaquo;
                = val

    block content

    p.copyright.text-center © 2014 iColor 家的设计师

    div#footer.text-center
      div#homekey
        a.homebtn(href="javascript:;")
          img(src="images/home-btn.png",alt="homeKey",title="home")
      - var switch_btn = ['btn','btn-gray','switch-dev']
      a(class=switch_btn,href="home.html") 手机版
      a(class=switch_btn,href="../icolor2/index.html") 电脑版

    script(type="text/javascript",src="js/jquery-1.11.0.min.js")
    script(type="text/javascript",src="js/bootstrap.min.js")

    block tail

{% endhighlight %}

所有标签的属性写在小括号里，跟在标签之后，属性之间逗号隔开：如

meta(name="viewport",content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=0")。

编译后的结果为：

{% highlight html %}
<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=0">
{% endhighlight %}

标签的class和id用'.'&'#'跟在标签之后。如：div#footer.text-center

编译后的结果为：

{% highlight html %}
<div id="footer" class="text-center">
  something...
</div>
{% endhighlight %}

layout.jade可以看作一个模版页面。通过在新页面的顶部添加：_extends layout_来引用layout.jade文件中的内容。

然后把新页面中的内容通过：**block append**添加到相对应的地方，如上述的例子中：_block head_、_block logoTitle_、_block content_、_block tail_（自己任意定义）。

我们可以将内容添加到head的位置：

{% highlight html %}
block append head
  something...
{% endhighlight %}

实例：
{% highlight html %}
block append head
  link(rel="stylesheet",href="css/index.css")
{% endhighlight %}

我们可以将内容添加到logoTitle的位置：

{% highlight html %}
block append logoTitle
  something...
{% endhighlight %}

实例：
{% highlight html %}
block append logoTitle
  a.navbar-brand(href="home.html",title="iColor|家的设计师")
    img(src="images/logo.png")
{% endhighlight %}


我们可以将内容添加到tail的位置：

{% highlight html %}
block append tail
  something...
{% endhighlight %}

实例：

{% highlight html %}
block append tail
  script(type="text/javascript", src="js/spin.js")
{% endhighlight %}

可以在jade文件模板中编写行内JavaScript代码。

如上例中的：

{% highlight html %}
ul.nav.navbar-nav.navbar-right
  each href, val in {'首页':'home.html','对话名人':'famous.html','业主通道':'channel.html','装修图库':'design_images.html','设计王牌':'designers.html','设计鉴赏':'#'}
    li
      a(href=href)
        span.pull-right &rsaquo;
        = val
{% endhighlight %}

编译后的html为：

{% highlight html %}
<ul class="nav navbar-nav navbar-right">
  <li><a href="home.html"><span class="pull-right">&rsaquo;</span>首页</a></li>
  <li><a href="famous.html"><span class="pull-right">&rsaquo;</span>对话名人</a></li>
  <li><a href="channel.html"><span class="pull-right">&rsaquo;</span>业主通道</a></li>
  <li><a href="design_images.html"><span class="pull-right">&rsaquo;</span>装修图库</a></li>
  <li><a href="designers.html"><span class="pull-right">&rsaquo;</span>设计王牌</a></li>
  <li><a href="#"><span class="pull-right">&rsaquo;</span>设计鉴赏</a></li>
</ul>
{% endhighlight %}

通过这个实例发现代码变得非常简洁，缩进清晰，公共的样式内容可以共用。

但是感觉手写html的代码输入量并没有比我平时输入的少——通过zencoding。

...

更多的语法请参考：

[Language Reference](http://jade-lang.com/reference/)
