---
layout: post
title:  "Jekyll Syntax"
date:   2014-01-20 15:40:34
categories: jekyll-skill
---

启动服务器：

<pre>
  $ jekyll serve
</pre>

* #####使用一个或多个空行分隔内容段来生成段落     <p>######

* #####html中的h1~h6分别使用1~6个#号表示：如：# -> h1; ## -> h2; ### -> h3; ###### -> h6;######

  h4的表示：####this is a level-4 header####

* #####使用“>”作为段落前缀来标识引用文字段落######

  > 应用文字

* #####使用“*”来表示无序列表；使用数字加“.”表示有序列表######


* 使用 {% highlight ruby %}[test](http://example.net "optional title") {% endhighlight %}来标记普通链接。

* 使用 {% highlight ruby %}![img](http://example.net/img.png "optional title"){% endhighlight %} 来标记图片。


  引号内的 title 文字是可选的，链接也可以使用相对路径。

* 使用 * 或 _ 包裹文本产生 strong 效果：
{% highlight html %}
  _语气很重的文本_ 以及 **语气更重的文本**
{% endhighlight %}