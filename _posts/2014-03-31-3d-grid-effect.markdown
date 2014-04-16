---
layout: post
title: "3d grid effect"
date: 2014-03-31 16:43
categories: categories/css3
---


今天，我们想与你分享一个小动画概念。这是我们专注[this fantastic prototype app by Marcus Eckert](https://www.youtube.com/watch?v=sjGF6Mw6X_Y)原型得以再创造的结果。这个思想是为了旋转3D网格内容，扩大到全屏，显示一些内容。我们试图模仿应用行为，创建了两个演示。在第一个demo中，我们制作了垂直旋转网格和第二个水平旋转。

请注意，这仅仅是一个概念验证，我们使用一些css属性，这些属性可能无法在每一个浏览器中都能正常工作（pointer-events－指针事件, 3d Transforms－3d 变换, CSS Transitions－css过度）。它是高度实验性的，因为一些浏览器还不能支持这些属性，我们提供了一个简单的回退，仅仅显示和隐藏内容。

演示中令人惊奇的插图是来自Adam Quest。所有图片来自选定的社论2014期Behance，并访问了他的Facebook页面。

我们模拟在原型应用视频中看到的效果，采用的方式是通过创建一个占位符，它将有一个正面和一个背面。正面将包含网格项内容的副本，背面是空白的。当点击一个网格项的时候，我们添加一个绝对定位占位符，并将它定位在点击项目的位置上。然后，我们进行动画其宽度和高度，使其达到窗口的宽度和高度，并设置其top和left属性的负值，使它移动网格的外部进入页面左上角。当我们这样做，我们也会旋转3d元素，露出背面白色的占位符。一旦填满了整个屏幕，我们将fadeIn存贮在不同部分的内容。

实际上这个网格项目的飞出和旋转，是一种错觉，它是通过淡出单击的网格项来完成的，因此我们只看到占位符被移出网格。
<!-- The illusion, that it’s actually the grid item that flies out and rotates, is completed by fading out the clicked grid item so that we can only see the placeholder being moved out of the grid. -->

此外，占位符朝着浏览者的方向移动，我们也通过在z轴上转变网格使其移出。

请注意，这仅仅是一个概念验证。你也许想要动态的加载内容（看加载效果的模型）或者显示一些其他别的内容作为你的主要内容，如：一个全屏图片。回退也是非常容易和普遍的。

让我们看看下面的标签和一些重要的样式，理解这个概念是如何实现的吧。

我们有一个主要的 <code>section</code> 元素，它包含一个网格div和一个内容区：






{% highlight html %}
<section class="grid3d vertical" id="grid3d">
  <div class="grid-wrap">
    <div class="grid">
      <figure><img src="images/posts/1.jpg" alt="images01"></figure>
      <figure><img src="images/posts/2.jpg" alt="images02"></figure>
      <figure><img src="images/posts/3.jpg" alt="images03"></figure>
    </div>
  </div><!-- /grid-wrap -->
  <div class="content">
    <div>
      <div class="dummy-img"></div>
      <p class="dummy-text">some text1</p>
      <p class="dummy-text">some more text1</p>
    </div>
    <div>
      <div class="dummy-img"></div>
      <p class="dummy-text">some text2</p>
      <p class="dummy-text">some more text2</p>
    </div>
    <div>
      <div class="dummy-img"></div>
      <p class="dummy-text">some text3</p>
      <p class="dummy-text">some more text3</p>
    </div>
    <!-- ... -->
    <span class="loading"></span>
    <span class="icon close-content"></span>
  </div>
</section>
{% endhighlight %}

当我们点击网格项的时候，我们将按顺序旋转匹配的内容div。内容部分也包括两个span标签，一个是模拟加载的活动指示，一个是关闭X按钮。

为了旋转和放大的效果，占位符将被动态的添加到网格，结构如下：

{% highlight html %}
<div class="placeholder">
  <div class="front"><!-- content of clicked grid item --></div>
  <div class="back"></div>
</div>
{% endhighlight %}

接下来让我们看一些重要的样式。

_grid-wrap_ div标签是一个带有perspective属性的元素：

{% highlight css %}
.grid-wrap{
  margin: 10px auto 0;
  max-width: 1090px;
  width: 100%;
  padding: 0;
  perspective: 1500px;
}
{% endhighlight %}

除了设置了perspective属性值外，我们也设置了perspective origin（透视原点）。但是，我们根据视图动态的设置。例如，如果你在较小的设备上看这个网格，这个网格的高度将变得比较大，我们不希望默认perspective origin的50%－50%，因为一个项目的整个网格的中心旋转离远离视窗（下降或上升）。我们将设置原点以浏览者为中心。
<!-- In addition to the perspective value, we also set the perspective origin. But that we do dynamically depending on the view. If you, for example, view this grid on a smaller device where the grid height becomes very large, we don’t want the default perspective origin of 50% 50% because then an item that is far from the center of the whole grid will rotate away from the viewport (down or up). We’ll set the origin to be central to the viewer instead. -->


_grid_ div有一个transition过渡，我们需要分配一个transform-style: perserve-3d;的属性给它，因为我们想要它的children可以以3d的效果旋转。

{% highlight css %}
.grid{
  position: relative;
  transition: all 0.5s cubic-bezier(0,0,0.25,1);
  transform-style: persverve-3d;
}
{% endhighlight %}


当我们单击一个网格项的时候，我们添加一个类名为wiew-full给网格，这个class将使grid移出：

{% highlight css %}
.view-full .grid {
  transform: translateZ(-1500px);
}
{% endhighlight %}

当我们单击网格项的时候，我们让其褪出（占位符将被放在这个位置）：

{% highlight css %}
.grid figure.active{
  opacity: 0;
}
{% endhighlight %}

占位符的pointer-events被设置成none,并且设置为决定定位，不同于网格中的figures。它也需要transform-style: preserve-3d;这个属性，因为我们要翻转它的背面：

{% highlight css %}
.grid .placeholder{
  pointer-events: none;
  position: absolute;
  transform-style: preserve-3d;
  transition: all 0.5s ease-out;
}
{% endhighlight %}

下面是占位符正面和背面关键的3d 样式：

{% highlight css %}
.placeholder > div{
  display: block;
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
}
.placeholder .front img{
  width: 100%;
  height: 100%;
}
.placeholder .back{
  background: white;
  transform: rotateY(180deg);
}
{% endhighlight %}

我们添加到占位符正面的这个克隆图片是被扩大到完整的宽度和高度来填充所有的元素。

当我们打开一个网格项，我们希望过渡有一个延迟和一个自定义的定时功能：

{% highlight css %}
.view-full .placeholder{
  transition: all 0.5s cubic-bezier(0,0,0.25,1)
}
{% endhighlight %}



原文地址：[http://tympanus.net/codrops/2014/03/27/3d-grid-effect/](http://tympanus.net/codrops/2014/03/27/3d-grid-effect/)