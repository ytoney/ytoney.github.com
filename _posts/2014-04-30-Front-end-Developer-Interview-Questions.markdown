---
layout: post
title:  "Front-end-Developer-Interview-Questions"
date:   2014-04-30 11:38:34
categories: categories/others
---


####你在昨天/本周学到了什么？####
用框架做网站一定要用框架的最新版本！

####编写代码的哪些方面能够使你兴奋或感兴趣？####
完成一个很炫的效果。

####在制作一个Web应用或Web站点的过程中，你是如何考虑他的UI、安全性、高性能、SEO、可维护性以及技术因素的？####
语义化编写，合理布局，必要的地方添加注释，表现、内容和行为分离，延缓js文件的加载，

[参考](http://sohtml5.diandian.com/)

####谈谈你喜欢的开发环境。(例如操作系统，编辑器，浏览器，工具等等。)####
喜欢Mac OS操作系统（因为自己的就是呀，嘻嘻），用户体验、页面效果展示等方面都很好；sublime编辑器高效方便快捷；chrome简洁、兼容性好、很多插件、代码调试也很方便；

####你能描述一下当你制作一个网页的工作流程吗？####
浏览设计稿，构思页面结构与布局；切图，将会用到的图片切下来，icon图片做成imgage sprite；用html和css布局页面；测试浏览器兼容性；用js制作特效；

####你能描述一下渐进增强和优雅降级之间的不同吗?####
优雅降级：主要体现在浏览器上、在最强大的浏览器上例如chrome或safari做出完整的体验，然后在ie6上根据差异修改一些重大bug、或做出一个体验不那么强的版本。

渐进増强，意为先做出一个可以兼容所有浏览器的版本，然后逐步提升体验效果。其实软件的迭代或者说网页的发展过程，从html到javascript到html5、css3就是一个渐进增强的过程。

<span class="text-error">如果提到了特性检测，可以加分</span>

####请解释一下什么是“语义化的 HTML”。####
例如，将强调的内容用strong标签包裹，代替用样式定义；将文章的标题设置为h1~h6；列表用ul或者ol；文字段落用p等等带有语义的标签。不仅仅是让机器能够读懂，在团队协作开发中，能够让人读懂也很重要。
[参考1](http://justineo.github.io/slideshows/semantic-html/)
[参考2](http://www.zhihu.com/question/20455165)
[参考3](http://www.css88.com/archives/1668)

####你如何对网站的文件和资源进行优化？####
<span class="text-error">期待的解决方案包括：</span>
<ul>
  <li>文件合并</li>
  <li>文件最小化/文件压缩</li>
  <li>使用 CDN 托管</li>
  <li>缓存的使用</li>
  <li>其他</li>
</ul>

####为什么利用多个域名来提供网站资源会更有效？####
<span class="text-error">浏览器同一时间可以从一个域名下载多少资源？</span>

[参考](http://www.zhihu.com/question/19997004)

####请说出三种减少页面加载时间的方法。（加载时间指感知的时间或者实际加载时间）####
合并压缩文件，优化图片，减少http请求次数；JavaScript 与CSS置于外部文件，将js文件放在底部；减少不必要的页面元素；缓存网页。

####如果你参与到一个项目中，发现他们使用 Tab 来缩进代码，但是你喜欢空格，你会怎么做？####
1.建议这个项目使用像 EditorConfig (http://editorconfig.org/) 之类的规范
2.为了保持一致性，接受项目原有的风格
3.直接使用 VIM 的 retab 命令

####请写一个简单的幻灯效果页面####
<span class="text-error">如果不使用JS来完成，可以加分。</span>






[参考答案](http://www.camnpr.com/archives/front-end-developer-interview-answers.html)