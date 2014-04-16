---
layout: post
title:  "ie6兼容fixed定位"
date:   2014-01-17 15:40:34
categories: categories/ieHack
---

解决ie6下fixed定位问题

html:

{% highlight html %}
<div>
  <p id="back-top">
    <a href="#top"><img src="images/back_top.png"></a>
  </p>
</div>
{% endhighlight %}

css:

{% highlight css %}
div{width:1000px;height:1000px;min-height:600px;margin:0 auto;background:#ddd;}
#back-top{
  position:fixed;
  left:50%;
  top:40%;
  margin-left:500px;
  _position:absolute;
  _left:expression(eval(document.documentElement.scrollLeft+565));
  _top:expression(eval(document.documentElement.scrollTop+400));
}
{% endhighlight %}
