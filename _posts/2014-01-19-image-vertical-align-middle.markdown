---
layout: post
title:  "未知高度图片的垂直、水平居中显示"
date:   2014-01-19 13:40:34
categories: categories/css
---



例一：兼容标准浏览器和ie7及ie以上版本

{% highlight html %}
<div class="a_img_v">
  <a href="#"><img src="/images/posts/12.jpg" /></a>
</div>
<div class="a_img_v2">
  <a href="#"><img src="/images/posts/196.jpg" /></a>
</div>


.a_img_v{display:table-cell;width:400px;height:300px;text-align:center;vertical-align:middle;*line-height:300px;border:1px solid #ddd;}
.a_img_v2{display:table-cell;width:1000px;height:300px;text-align:center;vertical-align:middle;*line-height:300px;border:1px solid #ddd;}
{% endhighlight %}

<div class="a_img_v">
  <a href="#"><img src="/images/posts/12.jpg" /></a>
</div>
<div class="a_img_v2">
  <a href="#"><img src="/images/posts/196.jpg" /></a>
</div>

<style type="text/css">
.a_img_v{display:table-cell;width:400px;height:300px;text-align:center;vertical-align:middle;*line-height:300px;border:1px solid #ddd;}
.a_img_v2{display:table-cell;width:1000px;height:300px;text-align:center;vertical-align:middle;*line-height:300px;border:1px solid #ddd;}
</style>


例二：兼容标准浏览器和ie6/7

{% highlight html %}
<div class="box_five">
    <img src="/images/posts/12.jpg" alt="" />
</div>
<div class="box_five">
    <img src="/images/posts/196.jpg" alt="" />
</div>

.box_five{
    width:500px;height:400px;
    text-align:center;
    border:1px solid #d3d3d3;background:#ddd;

    /* 兼容标准浏览器 */
    display: table-cell;
    vertical-align:middle;

    /* 兼容IE6/IE7 */
    *display:block;
    *font-size:349px;  /* 字体大小约为容器高度的0.873倍 400*0.873 = 349 */
    *font-family:Arial;  /* 防止非utf-8引起的hack失效问题，如gbk编码 */
}

.box_five img{
    vertical-align:middle;
}
{% endhighlight %}

<div class="box_five">
    <img src="/images/posts/12.jpg" alt="" />
</div>
<div class="box_five">
    <img src="/images/posts/196.jpg" alt="" />
</div>

<style type="text/css">
  .box_five{
    width:500px;height:400px;
    text-align:center;
    border:1px solid #d3d3d3;background:#ddd;

    /* 兼容标准浏览器 */
    display: table-cell;
    vertical-align:middle;

    /* 兼容IE6/IE7 */
    *display:block;
    *font-size:349px;  /* 字体大小约为容器高度的0.873倍 400*0.873 = 349 */
    *font-family:Arial;  /* 防止非utf-8引起的hack失效问题，如gbk编码 */
  }

  .box_five img{
      vertical-align:middle;
  }
</style>


其他方法：

{% highlight html %}
<div class="box_four">
    <p><img src="/images/posts/12.jpg" alt="" /></p>
</div>
<div class="box_four">
    <p><img src="/images/posts/196.jpg" alt="" /></p>
</div>


.box_four{
    width:500px;height:400px;
    text-align:center;
    border:1px solid #d3d3d3;background:red;
}
.box_four p{
    width:500px;height:400px;
    line-height:400px;  /* 行高等于高度 */
}

/* 兼容标准浏览器 */
.box_four p:before{
    content:".";  /* 具体的值与垂直居中无关，尽可能的节省字符 */
    margin-left:-5px; font-size:10px;  /* 修复居中的小BUG */
    visibility:hidden;  /*设置成隐藏元素*/
}

.box_four p img{
    *margin-top:expression((400 - this.height )/2);  /* CSS表达式用来兼容IE6/IE7 */
    vertical-align:middle;
    border:1px solid #ccc;
}
{% endhighlight %}


{% highlight html %}
<div class="box_three">
    <i></i><img src="/images/posts/196.jpg" alt="" />
</div>﻿
<div class="box_three">
    <i></i><img src="/images/posts/12.jpg" alt="" />
</div>﻿

.box_three{
width:500px;height:400px;
display:table-cell;
text-align:center;
vertical-align:middle;
border:1px solid #d3d3d3;background:red;
}
.box_three img{
border:1px solid #ccc;
}
<!--[if IE]>
<style type="text/css">﻿
.box_three i {
    display:inline-block;
    height:100%;
    vertical-align:middle
    }
.box_three img {
    vertical-align:middle
    }
</style>
<![endif]-->
{% endhighlight %}



{% highlight html %}
<div class="box_two">
    <span><img src="/images/posts/12.jpg" alt="" /></span>
</div>
<div class="box_two">
    <span><img src="/images/posts/196.jpg" alt="" /></span>
</div>

.box_two{
    margin:0 auto;
    width:500px;height:400px;
    overflow:hidden;
    position:relative;
    display:table-cell;
    text-align:center;
    vertical-align:middle;
    border:1px solid #d3d3d3;background:red;
}
.box_two span{
    position:static;
    *position:absolute; /*针对IE6/7的Hack*/
    top:50%; /*针对IE6/7的Hack*/
}
.box_two img {
    position:static;
    *position:relative; /*针对IE6/7的Hack*/
    top:-50%;left:-50%; /*针对IE6/7的Hack*/
    border:1px solid #ccc;
}
{% endhighlight %}


{% highlight html %}
<div class="box">
  <span><img src="/images/posts/196.jpg" alt="" /></span>
</div>
<div class="box">
    <span><img src="/images/posts/12.jpg" alt="" /></span>
</div>

.box{
    margin:0 auto;
    width:500px;height:400px;
    display:table;
    text-align:center;
    border:1px solid #d3d3d3;background:#ff0000;
}
.box span{
    display:table-cell;
    vertical-align:middle;
}
.box img{
    border:1px solid #ccc;
}
<!--[if lte IE 7]>
<style type="text/css">﻿
.box{
    position:relative;
    overflow:hidden;
}
.box span{
    position:absolute;
    left:50%;top:50%;
}
.box img{
    position:relative;
    left:-50%;top:-50%;
}
</style>
<![endif]-->
{% endhighlight %}

