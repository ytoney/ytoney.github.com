---
layout: post
title:  "My first Blog"
date:   2014-01-13 15:40:34
categories: categories/others
---


###我的第一篇博客——<small class="muted">初识GitHub Pages & Jekyll 搭建博客</small>###

GitHub，它是一个具有版本管理功能的代码仓库，每个项目都有一个主页，列出项目的源文件。它还提供模板，允许站内生成网页。GitHub Pages就是可以用户自己编写静态网页托管在github上，然后上传。

Jekyll（发音/'dʒiːk əl/，"杰克尔"）是一个静态站点生成器，它会根据网页源码生成静态文件。它提供了模板、变量、插件等功能，所以实际上可以用来编写整个网站。

Jekyll is a simple, blog-aware, static site generator perfect for personal, project, or organization sites. Think of it like a file-based CMS, without all the complexity. Jekyll takes your content, renders Markdown and Liquid templates, and spits out a complete, static website ready to be served by Apache, Nginx or another web server. Jekyll is the engine behind GitHub Pages, which you can use to host sites right from your GitHub repositories.


#####安装jekyll#####

<pre>gem install jekyll</pre>

搭建github博客的环境：你必须已经安装了git，并且有github账户:

#####第一步，创建项目。#####

<pre>
  $ mkdir ThreeMonths
</pre>

对该目录进行git初始化。
<pre>
  $ cd ThreeMonths
  $ git init
</pre>

然后，创建一个没有父节点的分支master。因为github规定，只有该分支中的页面，才会生成网页文件。<br>以下所有动作，都在该分支下完成。

<pre>
  $ git checkout --orphan master
</pre>

#####第二步，创建设置文件。#####

#####第三步，创建模板文件。#####

在项目根目录下，创建一个_layouts目录，用于存放模板文件。
<pre>
  $ mkdir _layouts
</pre>

进入该目录，创建一个default.html文件，作为Blog的默认模板。


#####第四步，创建文章。#####

回到项目根目录，创建一个_posts目录，用于存放blog文章。

<pre>
  $ mkdir _posts
</pre>

进入该目录，创建第一篇文章。文章就是普通的文本文件，文件名假定为2012-08-25-hello-world.html。(注意，文件名必须为"年-月-日-文章标题.后缀名"的格式。如果网页代码采用html格式，后缀名为html；如果采用markdown格式，后缀名为md。）

在该文件中，填入以下内容：（注意，行首不能有空格）

{% highlight html %}
  ---
　layout: default
　title: 你好，世界
　---
　<h2>{ { page.title }}</h2>
　<p>我的第一篇文章</p>
　<p>{ { page.date | date_to_string }}</p>
{% endhighlight %}

每篇文章的头部，必须有一个yaml文件头，用来设置一些元数据。它用三根短划线"---"，标记开始和结束，里面每一行设置一种元数据。"layout:default"，表示该文章的模板使用_layouts目录下的default.html文件；"title: 你好，世界"，表示该文章的标题是"你好，世界"，如果不设置这个值，默认使用嵌入文件名的标题，即"hello world"。

在yaml文件头后面，就是文章的正式内容，里面可以使用模板变量。{ { page.title }}就是文件头中设置的"你好，世界"，{ { page.date }}则是嵌入文件名的日期（也可以在文件头重新定义date变量），"| date_to_string"表示将page.date变量转化成人类可读的格式。

#####第五步，创建首页。#####

回到根目录，创建一个index.html文件，填入以下内容。

{% highlight html %}
  ---
　layout: default
　title: 你好，世界
　---
　<h2>{ { page.title }}</h2>
　<p>最新文章</p>
　<ul>
　　 { % for post in site.posts %}
    <li>{ { post.date | date_to_string }} <a href="{ { site.baseurl }}{ { post.url }}">{ { post.title }}</a></li>
    { % endfor %}
　</ul>
{% endhighlight %}


#####第六步，发布内容。#####

现在，这个简单的Blog就可以发布了。先把所有内容加入本地git库。

<pre>
  $ git add .
  $ git commit -m "first post"
</pre>

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



在github上搭建blog的步骤及原文参考网址：

[jekyll Quick-start guide](http://jekyllrb.com/docs/quickstart/ "jekyll guide")

[http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html][step]


<!-- Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll's GitHub repo][jekyll-gh]. -->

[jekyll-gh]: https://github.com/mojombo/jekyll
[step]:    http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html
