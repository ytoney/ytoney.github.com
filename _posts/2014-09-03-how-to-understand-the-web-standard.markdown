---
layout: post
title:  "对web标准的理解"
date:   2014-01-13 16:40:34
categories: categories/html
---

文章来自： <a href="http://blog.sina.com.cn/s/blog_5fb4754f0100d38a.html">张鹏的博客</a>

<pre>
  Web标准不是某一个标准，而是由一系列标准组合而成。网页主要由三部分组成：结构、表现和行为。对应的标准也分三方面：结构化标准语言主要包括XHTML和HTML以及XML，表现标准语言主要包括CSS，行为标准主要包括对象模型（如W3C DOM）、ECMAScript等。这些标准大部分由W3C起草和发布，也有一些是其他标准组织制订的标准。我简单了解一下这些标准：
1．结构标准语言
   （1）、XML
   XML是The Extensible Markup Language(可扩展标识语言)的简写。目前推荐遵循的是的XML1.0，和HTML基本一样，XML是一种能定义其他语言的语。XML最初设计的目的是弥补HTML的不足，以强大的扩展性满足网络信息发布的需要，后来逐渐用于网络数据的转换和描述，算是最理想的一种语言。
   （2）、XHTML
   XHTML是The Extensible HyperText Markup Language可扩展标识语言的缩写。最初是1989年由Tim Berners-Lee发明的。XML虽然数据转换能力强大，完全可以替代HTML，但面对成千上万已有的站点，直接采用XML还为时过早。简单的说，建立XHTML的目的就是实现HTML向XML的过渡。
2.表现标准语言
   CSS是Cascading Style Sheets层叠样式表的缩写。W3C创建CSS标准的目的是以CSS取代HTML表格式布局、帧和其他表现的语言。
3.行为标准
   （1）、DOM
   DOM是Document Object Model文档对象模型的缩写。DOM是一种与浏览器，平台，语言的接口，使得你可以访问页面其他的标准组件。简单理解，DOM解决了Netscaped的Javascript和Microsoft的Jscript之间的冲突，给予web设计师和开发者一个标准的方法，让他们来访问他们站点中的数据、脚本和表现层对像。
    (2) 、ECMAScript
  ECMAScript是ECMA(European Computer Manufacturers Association)制定的标准脚本语言（JAVAScript）。
</pre>