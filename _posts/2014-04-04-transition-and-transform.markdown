---
layout: post
title:  "transition and transform"
date:   2014-04-04 16:51:34
categories: categories/css3
---

<!--
<a href="#summary">概括</a>
<a href="#syntax">语法</a>
<a href="#example">例子</a>
 -->

###transition###

transition属性是一个实验性的技术。

<p>因为这个技术的兼容性还不稳定，不能够兼容所有的浏览器。</p>

#####浏览器兼容性#####
<!-- Browser compatibility -->

######Desktop######

<table class="table table-bordered">
  <tbody>
   <tr>
    <th>Feature</th>
    <th>Chrome</th>
    <th>Firefox (Gecko)</th>
    <th>Internet Explorer</th>
    <th>Opera</th>
    <th>Safari</th>
   </tr>
   <tr>
    <td>Basic support</td>
    <td>1.0 <span class="inlineIndicator prefixBox prefixBoxInline" title="prefix">-webkit</span><br>
     26.0</td>
    <td>4.0 (2.0) <span class="inlineIndicator prefixBox prefixBoxInline" title="prefix">-moz</span><br>
     16.0 (16.0)</td>
    <td>10.0</td>
    <td>11.6 <span class="inlineIndicator prefixBox prefixBoxInline" title="prefix">-o</span><br>
     12.10 <a class="external" href="http://my.opera.com/ODIN/blog/2012/08/03/a-hot-opera-12-50-summer-time-snapshot" title="http://my.opera.com/ODIN/blog/2012/08/03/a-hot-opera-12-50-summer-time-snapshot">#</a></td>
    <td>3.0 <span class="inlineIndicator prefixBox prefixBoxInline" title="prefix">-webkit</span></td>
   </tr>
  </tbody>
</table>

######Mobile######

<table class="table table-bordered">
  <tbody>
   <tr>
    <th>Feature</th>
    <th>Android</th>
    <th>Firefox Mobile (Gecko)</th>
    <th>IE Mobile</th>
    <th>Opera Mobile</th>
    <th>Safari Mobile</th>
   </tr>
   <tr>
    <td>Basic support</td>
    <td>2.1 <span class="inlineIndicator prefixBox prefixBoxInline" title="prefix">-webkit</span></td>
    <td>4.0 (2.0) <span class="inlineIndicator prefixBox prefixBoxInline" title="prefix">-moz</span><br>
     16.0 (16.0)</td>
    <td><span style="color: rgb(255, 153, 0);" title="Compatibility unknown; please update this.">?</span></td>
    <td>10.0 <span class="inlineIndicator prefixBox prefixBoxInline" title="prefix">-o</span><br>
     12.10 <a class="external" href="http://my.opera.com/ODIN/blog/2012/08/03/a-hot-opera-12-50-summer-time-snapshot" title="http://my.opera.com/ODIN/blog/2012/08/03/a-hot-opera-12-50-summer-time-snapshot">#</a></td>
    <td>3.2 <span class="inlineIndicator prefixBox prefixBoxInline" title="prefix">-webkit</span></td>
   </tr>
  </tbody>
</table>

<h5 id="summary">概括</h5>

css transition属性是<code>transition-property</code>, <code>transition-duration</code>, <code>transition-timing-function</code>和<code>transition-delay</code>的简写方式。它允许在一个元素上定义两个声明之间的过渡。不同的声明也许用伪类定义，像:hover,:active或者通过js设置动态的效果。

<code>transition</code>：<过度属性名称> <过度时间> <过渡模式>

初始值：

<code>transition-delay: 0s</code>

<code>transition-duration: 0s</code>

<code>transition-property: all</code>

<code>transition-timing-function: ease</code>。transition-timing-function有5种过渡模式：<code>ease</code> 缓慢的开始，缓慢的结束；<code>linear</code> 匀速；<code>ease-in</code> 缓慢开始；<code>ease-out</code> 缓慢结束；<code>ease-in-out</code> 缓慢开始，缓慢结束（和ease稍有区别）；

<h5 id="syntax">语法</h5>

{% highlight css %}
语法形式：_[ none | <single-transition-property> ] || <time> || <timing-function> || <time>_
{% endhighlight %}

例：<code>transition: width 300ms, height 300ms, box-shadow 1500ms;</code>

实例：

<div class="transition_box"></div>
<a href="javascript:;" class="animitClass">click me!</a>

<style>
  .transition_box{
    width: 200px;
    height: 30px;
    /*visibility: hidden;*/
    margin: 20px;
    box-shadow: 0px 1px 1px rgba(0,0,0,.3);
    transition: width 300ms, height 300ms, box-shadow 1500ms;
  }
  .transition_box.active{
    width: 100%;
    height: 100px;
    /*visibility: visible;*/
    box-shadow: 0 11px 18px rgba(0,0,0,.2);
  }
</style>

<script>
  var transition_box = document.getElementsByClassName('transition_box')[0];
  document.getElementsByClassName('animitClass')[0].onclick = function(){
    transition_box.classList.toggle('active')
  }
</script>

<div class="transform_box" id="transform_box">
  <h5>Section 1</h5>
  第一最好不相见，如此便可不相恋。
  第二最好不相知，如此便可不相思。
  但曾相见便相知，相见何如不见时。
  安得与君相决绝，免教辛苦作相思。
</div>
<style type="text/css">
  .transform_box{
    display: inline-block;
    width: 150px;
    height: 200px;
    margin-top: 30px;
    padding: 10px;
    box-shadow: 0 1px 1px rgba(0,0,0,0.3);
    transform: translateY(0) scale(0.95,0.95);
    transition: all 0.5s cubic-bezier(0.190, 1.000, 0.220, 1.000);

    cursor: pointer;
  }
</style>

<script type="text/javascript">
  window.onload = function(){
    var flag = true;
    var transform_box = document.getElementById('transform_box');
    transform_box.onclick = function(){
      if (flag) {
        this.style.webkitTransform = 'translateY(-20px) scale(1.0,1.0)';
        this.style.boxShadow = '0 8px 30px rgba(0,0,0,0.3)';
        flag = false;
      }else{
        this.style.webkitTransform = 'translateY(0) scale(0.95,0.95)';
        this.style.boxShadow = '0 1px 1px rgba(0,0,0,0.3)';
        flag = true;
      }
    }
  }
</script>

<div class="ball"><span class="round"></span></div>
<style type="text/css">
  .ball{
    display: inline-block;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background-color: darkseagreen;
    box-shadow: 0 0 8px rgba(0,0,0,0.1);

    -webkit-animation: myrotate 5s linear 3s infinite alternate;
  }
  @-webkit-keyframes myrotate {
    0% {
      width: 50px;
      height: 50px;
      border-radius: 50px;
    }
    100% {
      -webkit-transform: translate(200px,0) rotate(360deg);
      -webkit-transition: transform 2s;
    }
  }

  /**/
  .round{
    display: inline-block;
    width: 100%;
    height: 100%;
    background: url(/images/posts/12.jpg) no-repeat -141px -35px;
    background-size: initial;
    border-radius: 50%;
    border: 0;
    transition: background-position 0.3s;
  }
  .ball:hover .round{
    background-position: -71px -61px;
    transition: background-position 0.3s;
  }
</style>


###transform###
