---
layout: post
title:  "js-Tab切换"
date:   2014-10-03 15:00:34
categories: categories/demo
---

<style type="text/css">
  *{
    margin: 0;
    padding: 0;
    list-style: none;
    font-size: 12px;
  }
  .clear{
    *zoom: 1;
  }
  .clear:before,
  .clear:after{
    display: table;
    line-height: 0;
    content: '';
  }
  .clear:after{
    clear: both;
  }
  /* notice box */
  .notice,
  .notice-delay,
  .notice-auto{
    width: 298px;
    height: 98px;
    border: 1px solid #eee;
    /*margin: 10px;*/
    overflow: hidden;
    display: inline-block;
  }
   /* tabs-nav */
  .notice-tit,
  .notice-delay-tit,
  .notice-auto-tit{
    height: 27px;
    position: relative;
    background-color: #f7f7f7;
  }
  .notice-tit ul,
  .notice-delay-tit ul,
  .notice-auto-tit ul{
    /*clear: both;*/
    margin: 0;
  }
  .notice-tit li,
  .notice-delay-tit li,
  .notice-auto-tit li{
    float: left;
    line-height: 27px;
    width: 20%;
    text-align: center;
    overflow: hidden;
    border-bottom: 1px solid #eee;
  }
  .notice-tit li.active,
  .notice-delay-tit li.active,
  .notice-auto-tit li.active{
    background-color: #fff;
    border-bottom-color: #fff;
  }
  .notice-tit li.active a,
  .notice-delay-tit li.active a,
  .notice-auto-tit li.active a{
    display: block;
    border-left: 1px solid #eee;
    border-right: 1px solid #eee;
  }
  .notice-tit li.active:first-child a,
  .notice-delay-tit li.active:first-child a,
  .notice-auto-tit li.active:first-child a{
    border-left: 0;
  }
  .notice-tit li.active:last-child a,
  .notice-delay-tit li.active:last-child a,
  .notice-auto-tit li.active:last-child a{
    border-right: 0;
  }
  .notice-tit li a,
  .notice-delay-tit li a,
  .notice-auto-tit li a{
    display: block;
  }
  .notice li a,
  .notice-delay li a,
  .notice-auto li a{
    color: #000;
  }
  .notice li a:link,
  .notice li a:visited,
  .notice-delay li a:link,
  .notice-delay li a:visited,
  .notice-auto li a:link,
  .notice-auto li a:visited{
    text-decoration: none;
  }
  .notice-tit li a:hover,
  .notice-delay-tit li a:hover,
  .notice-auto-tit li a:hover{
    color: red;
  }

  /* tabs contents */
  .notice-con .mod,
  .notice-delay-con .mod,
  .notice-auto-con .mod{
    display: none;
  }
  .notice-con .mod.active,
  .notice-delay-con .mod.active,
  .notice-auto-con .mod.active{
    display: block;
  }
  .notice-con .mod ul,
  .notice-delay-con .mod ul,
  .notice-auto-con .mod ul{
    margin-left: 0;
    margin-bottom: 0;
    padding: 15px 10px;
    *zoom: 1;/* 清除浮动 */
  }
  .notice-con .mod li,
  .notice-delay-con .mod li,
  .notice-auto-con .mod li{
    float: left;
    width: 46%;
    height: 20px;
    padding-left: 2%;
    padding-right: 2%;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
  }
  /* 清除浮动 = .clear */
  .notice-con .mod ul:before,
  .notice-con .mod ul:after,
  .notice-delay-con .mod ul:before,
  .notice-delay-con .mod ul:after,
  .notice-auto-con .mod ul:before,
  .notice-auto-con .mod ul:after{
    display: table;
    line-height: 0;
    content: '';
  }
  .notice-con .mod ul:after,
  .notice-delay-con .mod ul:after,
  .notice-auto-con .mod ul:after{
    clear: both;
  }
  /**/
</style>
<div class="notice" id="notice">
  <div id="notice-tit" class="notice-tit">
    <ul class="clear">
      <li class="active"><a href="#">公告</a></li>
      <li><a href="#">规则</a></li>
      <li><a href="#">论坛</a></li>
      <li><a href="#">安全</a></li>
      <li><a href="#">公益</a></li>
    </ul>
  </div>
  <div id="notice-con" class="notice-con">
    <div class="mod active">
      <ul class="clear">
        <li><a href="#">事件流：事件冒泡、事件捕获</a></li>
        <li><a href="#">使用事件处理程序的方法</a></li>
        <li><a href="#">HTML事件处理程序</a></li>
        <li><a href="#">DOM0级事件处理程序</a></li>
      </ul>
    </div>
    <div class="mod">
      <ul>
        <li>
          <span><a href="#">[通知]</a></span>
          <a href="#">事件流：事件冒泡、事件捕获</a>
        </li>
        <li>
          <span><a href="#">[通知]</a></span>
          <a href="#">使用事件处理程序的方法</a>
        </li>
        <li>
          <span><a href="#">[通知]</a></span>
          <a href="#">HTML事件处理程序</a>
        </li>
        <li>
          <span><a href="#">[通知]</a></span>
          <a href="#">DOM0级事件处理程序</a>
        </li>
      </ul>
    </div>
    <div class="mod">
      <ul>
        <li>
          <span><a href="#">[聚焦]</a></span>
          <a href="#">事件流：事件冒泡、事件捕获</a>
        </li>
        <li>
          <span><a href="#">[聚焦]</a></span>
          <a href="#">使用事件处理程序的方法</a>
        </li>
        <li>
          <span><a href="#">[聚焦]</a></span>
          <a href="#">HTML事件处理程序</a>
        </li>
        <li>
          <span><a href="#">[聚焦]</a></span>
          <a href="#">DOM0级事件处理程序</a>
        </li>
      </ul>
    </div>
    <div class="mod">
      <ul>
        <li>
          <span><a href="#">[安全]</a></span>
          <a href="#">事件流：事件冒泡、事件捕获</a>
        </li>
        <li>
          <span><a href="#">[安全]</a></span>
          <a href="#">使用事件处理程序的方法</a>
        </li>
        <li>
          <span><a href="#">[安全]</a></span>
          <a href="#">HTML事件处理程序</a>
        </li>
        <li>
          <span><a href="#">[安全]</a></span>
          <a href="#">DOM0级事件处理程序</a>
        </li>
      </ul>
    </div>
    <div class="mod">
      <ul>
        <li><a href="#">事件流：事件冒泡、事件捕获</a></li>
        <li><a href="#">使用事件处理程序的方法</a></li>
        <li><a href="#">HTML事件处理程序</a></li>
        <li><a href="#">DOM0级事件处理程序</a></li>
      </ul>
    </div>
  </div>
</div>


<!-- 延迟切换 -->
<div class="notice-delay" id="notice-delay">
  <div id="notice-delay-tit" class="notice-delay-tit">
    <ul class="clear">
      <li class="active"><a href="#">公告</a></li>
      <li><a href="#">规则</a></li>
      <li><a href="#">论坛</a></li>
      <li><a href="#">安全</a></li>
      <li><a href="#">公益</a></li>
    </ul>
  </div>
  <div id="notice-delay-con" class="notice-delay-con">
    <div class="mod active">
      <ul class="clear">
        <li><a href="#">事件流：事件冒泡、事件捕获</a></li>
        <li><a href="#">使用事件处理程序的方法</a></li>
        <li><a href="#">HTML事件处理程序</a></li>
        <li><a href="#">DOM0级事件处理程序</a></li>
      </ul>
    </div>
    <div class="mod">
      <ul>
        <li>
          <span><a href="#">[通知]</a></span>
          <a href="#">事件流：事件冒泡、事件捕获</a>
        </li>
        <li>
          <span><a href="#">[通知]</a></span>
          <a href="#">使用事件处理程序的方法</a>
        </li>
        <li>
          <span><a href="#">[通知]</a></span>
          <a href="#">HTML事件处理程序</a>
        </li>
        <li>
          <span><a href="#">[通知]</a></span>
          <a href="#">DOM0级事件处理程序</a>
        </li>
      </ul>
    </div>
    <div class="mod">
      <ul>
        <li>
          <span><a href="#">[聚焦]</a></span>
          <a href="#">事件流：事件冒泡、事件捕获</a>
        </li>
        <li>
          <span><a href="#">[聚焦]</a></span>
          <a href="#">使用事件处理程序的方法</a>
        </li>
        <li>
          <span><a href="#">[聚焦]</a></span>
          <a href="#">HTML事件处理程序</a>
        </li>
        <li>
          <span><a href="#">[聚焦]</a></span>
          <a href="#">DOM0级事件处理程序</a>
        </li>
      </ul>
    </div>
    <div class="mod">
      <ul>
        <li>
          <span><a href="#">[安全]</a></span>
          <a href="#">事件流：事件冒泡、事件捕获</a>
        </li>
        <li>
          <span><a href="#">[安全]</a></span>
          <a href="#">使用事件处理程序的方法</a>
        </li>
        <li>
          <span><a href="#">[安全]</a></span>
          <a href="#">HTML事件处理程序</a>
        </li>
        <li>
          <span><a href="#">[安全]</a></span>
          <a href="#">DOM0级事件处理程序</a>
        </li>
      </ul>
    </div>
    <div class="mod">
      <ul>
        <li><a href="#">事件流：事件冒泡、事件捕获</a></li>
        <li><a href="#">使用事件处理程序的方法</a></li>
        <li><a href="#">HTML事件处理程序</a></li>
        <li><a href="#">DOM0级事件处理程序</a></li>
      </ul>
    </div>
  </div>
</div>

<!-- 自动切换 -->
<div class="notice-auto" id="notice-auto">
  <div id="notice-auto-tit" class="notice-auto-tit">
    <ul class="clear">
      <li class="active"><a href="#">公告</a></li>
      <li><a href="#">规则</a></li>
      <li><a href="#">论坛</a></li>
      <li><a href="#">安全</a></li>
      <li><a href="#">公益</a></li>
    </ul>
  </div>
  <div id="notice-auto-con" class="notice-auto-con">
    <div class="mod active">
      <ul class="clear">
        <li><a href="#">事件流：事件冒泡、事件捕获</a></li>
        <li><a href="#">使用事件处理程序的方法</a></li>
        <li><a href="#">HTML事件处理程序</a></li>
        <li><a href="#">DOM0级事件处理程序</a></li>
      </ul>
    </div>
    <div class="mod">
      <ul>
        <li>
          <span><a href="#">[通知]</a></span>
          <a href="#">事件流：事件冒泡、事件捕获</a>
        </li>
        <li>
          <span><a href="#">[通知]</a></span>
          <a href="#">使用事件处理程序的方法</a>
        </li>
        <li>
          <span><a href="#">[通知]</a></span>
          <a href="#">HTML事件处理程序</a>
        </li>
        <li>
          <span><a href="#">[通知]</a></span>
          <a href="#">DOM0级事件处理程序</a>
        </li>
      </ul>
    </div>
    <div class="mod">
      <ul>
        <li>
          <span><a href="#">[聚焦]</a></span>
          <a href="#">事件流：事件冒泡、事件捕获</a>
        </li>
        <li>
          <span><a href="#">[聚焦]</a></span>
          <a href="#">使用事件处理程序的方法</a>
        </li>
        <li>
          <span><a href="#">[聚焦]</a></span>
          <a href="#">HTML事件处理程序</a>
        </li>
        <li>
          <span><a href="#">[聚焦]</a></span>
          <a href="#">DOM0级事件处理程序</a>
        </li>
      </ul>
    </div>
    <div class="mod">
      <ul>
        <li>
          <span><a href="#">[安全]</a></span>
          <a href="#">事件流：事件冒泡、事件捕获</a>
        </li>
        <li>
          <span><a href="#">[安全]</a></span>
          <a href="#">使用事件处理程序的方法</a>
        </li>
        <li>
          <span><a href="#">[安全]</a></span>
          <a href="#">HTML事件处理程序</a>
        </li>
        <li>
          <span><a href="#">[安全]</a></span>
          <a href="#">DOM0级事件处理程序</a>
        </li>
      </ul>
    </div>
    <div class="mod">
      <ul>
        <li><a href="#">事件流：事件冒泡、事件捕获</a></li>
        <li><a href="#">使用事件处理程序的方法</a></li>
        <li><a href="#">HTML事件处理程序</a></li>
        <li><a href="#">DOM0级事件处理程序</a></li>
      </ul>
    </div>
  </div>
</div>

<pre>
  // 把获取id单独封装为一个函数
  function _$(id){
    return typeof id === 'string' ? document.getElementById(id) : id;
  }

  window.onload = function(){
    // 没有延迟的切换效果========================================================
    // 获取鼠标滑过或点击的标签和要切换内容的元素
    var titles = _$('notice-tit').getElementsByTagName('li'),
        divs = _$('notice-con').getElementsByTagName('div');
        // alert(titles.length)
    if (titles.length != divs.length) {
      return;
    }

    // 遍历titles下的所有li
    for (var i = 0;i < titles.length; i++) {
      titles[i].id = i;
      titles[i].onmouseover = function(){ // onclick
        // alert(this.id);
        // 清楚所有li上的class
        for (var j = 0; j < titles.length; j++) {
          titles[j].className = '';
          divs[j].style.display = 'none';
        }
        //设置当前为高亮显示
        this.className = 'active';
        divs[this.id].style.display = 'block';
      }
    }



    // 延迟切换 beginning ====================================================
    // 标签的索引
    var index = 0;
    var timer = null;

    var delayTits = _$('notice-delay-tit').getElementsByTagName('li'),
        delayDivs = _$('notice-delay-con').getElementsByTagName('div');

    if (delayTits.length != delayDivs.length) {
      return;
    }
    // console.log(delayDivs.length)
    // 遍历所有的页签
    for(var m = 0; m < delayTits.length; m++){
      delayTits[m].id = 'delay' + m;
      delayTits[m].onmouseover = function(){
        // 用that这个变量来引用当前滑过的li
        var that = this;
        // 如果存在了准备执行的定时器，立刻清除，只有当前停留时间大于500ms时才开始执行
        if (timer) {
          clearTimeout(timer);
          timer = null;
        }
        // 延迟半秒执行
        timer = setTimeout(function(){ //setTimeout()的全称是window.setTimeout(),setTimeout()是window的方法。window的所有方法和属性都可以省略window,所以此时的this是window
          for(var n = 0; n < delayTits.length; n++){
            delayTits[n].className = '';
            delayDivs[n].style.display = 'none';
          }
          // alert(this);// 此时的this变成了window
          delayTits[that.id].className = 'active';
          delayDivs[that.id.slice(5)].style.display = 'block';
        }, 500);

      }
    }



    // 自动切换 beginning ====================================================
    // 当前高亮显示的页签的索引
    var index = 0;
    var timerAuto = null;

    var autoTits = _$('notice-auto-tit').getElementsByTagName('li'),
        autoDivs = _$('notice-auto-con').getElementsByTagName('div');

    // 变量每一个页签且给他们绑定事件
    for(var x = 0; x < autoTits.length; x++){
      autoTits[x].id = 'auto' + x;
      autoTits[x].onmouseover = function(){
        clearTimeout(timerAuto);
        changeOption(this.id.slice(4));
      }
      autoTits[x].onmouseout = function(){
        // clearTimeout(timerAuto);
        timerAuto = setInterval(autoPlay, 2000);
      }
    }

    if (timerAuto) {
      clearTimeout(timerAuto);
      timerAuto = null;
    }
    // 添加定时器，改变当前高亮的索引
    timerAuto = setInterval(autoPlay, 2000);

    function autoPlay(){
      index++;
      if (index >= autoTits.length) {
        index = 0;
      }
      changeOption(index);
    }

    function changeOption(curIndex){
      for(var d = 0; d < autoTits.length; d++){
        autoTits[d].className = '';
        autoDivs[d].style.display = 'none';
      }
      // console.log(index);
      autoTits[curIndex].className = 'active';
      autoDivs[curIndex].style.display = 'block';
      index = curIndex;
    }
  }
</pre>


<script type="text/javascript">
  // 把获取id单独封装为一个函数
  function _$(id){
    return typeof id === 'string' ? document.getElementById(id) : id;
  }

  window.onload = function(){
    // 没有延迟的切换效果========================================================
    // 获取鼠标滑过或点击的标签和要切换内容的元素
    var titles = _$('notice-tit').getElementsByTagName('li'),
        divs = _$('notice-con').getElementsByTagName('div');
        // alert(titles.length)
    if (titles.length != divs.length) {
      return;
    }

    // 遍历titles下的所有li
    for (var i = 0;i < titles.length; i++) {
      titles[i].id = i;
      titles[i].onmouseover = function(){ // onclick
        // alert(this.id);
        // 清楚所有li上的class
        for (var j = 0; j < titles.length; j++) {
          titles[j].className = '';
          divs[j].style.display = 'none';
        }
        //设置当前为高亮显示
        this.className = 'active';
        divs[this.id].style.display = 'block';
      }
    }



    // 延迟切换 beginning ====================================================
    // 标签的索引
    var index = 0;
    var timer = null;

    var delayTits = _$('notice-delay-tit').getElementsByTagName('li'),
        delayDivs = _$('notice-delay-con').getElementsByTagName('div');

    if (delayTits.length != delayDivs.length) {
      return;
    }
    // console.log(delayDivs.length)
    // 遍历所有的页签
    for(var m = 0; m < delayTits.length; m++){
      delayTits[m].id = 'delay' + m;
      delayTits[m].onmouseover = function(){
        // 用that这个变量来引用当前滑过的li
        var that = this;
        // 如果存在了准备执行的定时器，立刻清除，只有当前停留时间大于500ms时才开始执行
        if (timer) {
          clearTimeout(timer);
          timer = null;
        }
        // 延迟半秒执行
        timer = setTimeout(function(){ //setTimeout()的全称是window.setTimeout(),setTimeout()是window的方法。window的所有方法和属性都可以省略window,所以此时的this是window
          for(var n = 0; n < delayTits.length; n++){
            delayTits[n].className = '';
            delayDivs[n].style.display = 'none';
          }
          // alert(this);// 此时的this变成了window
          delayTits[that.id].className = 'active';
          delayDivs[that.id.slice(5)].style.display = 'block';
        }, 500);

      }
    }



    // 自动切换 beginning ====================================================
    // 当前高亮显示的页签的索引
    var index = 0;
    var timerAuto = null;

    var autoTits = _$('notice-auto-tit').getElementsByTagName('li'),
        autoDivs = _$('notice-auto-con').getElementsByTagName('div');

    // 变量每一个页签且给他们绑定事件
    for(var x = 0; x < autoTits.length; x++){
      autoTits[x].id = 'auto' + x;
      autoTits[x].onmouseover = function(){
        clearTimeout(timerAuto);
        changeOption(this.id.slice(4));
      }
      autoTits[x].onmouseout = function(){
        // clearTimeout(timerAuto);
        timerAuto = setInterval(autoPlay, 2000);
      }
    }

    if (timerAuto) {
      clearTimeout(timerAuto);
      timerAuto = null;
    }
    // 添加定时器，改变当前高亮的索引
    timerAuto = setInterval(autoPlay, 2000);

    function autoPlay(){
      index++;
      if (index >= autoTits.length) {
        index = 0;
      }
      changeOption(index);
    }

    function changeOption(curIndex){
      for(var d = 0; d < autoTits.length; d++){
        autoTits[d].className = '';
        autoDivs[d].style.display = 'none';
      }
      // console.log(index);
      autoTits[curIndex].className = 'active';
      autoDivs[curIndex].style.display = 'block';
      index = curIndex;
    }
  }
</script>