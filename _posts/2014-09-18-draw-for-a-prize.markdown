---
layout: post
title:  "js-抽奖系统-键盘事件"
date:   2014-09-18 18:00:34
categories: categories/demo
---

<h3 class="text-center text-error" id="title">马上抽奖</h3>
<div class="btns text-center">
  <span id="start" class="btn btn-small">开始</span>
  <span id="stop" class="btn btn-small">停止</span>
</div>

<script type="text/javascript">
  var data = ['phone5', 'iPad', '佳能数码相机', '惠普打印机', '50元充值卡', '1000超市购物卡', '戴尔笔记本', '美的空调'],
      timer = null,
      flag = 0;

  window.onload = function () {
    var start = document.getElementById('start'),
        stop = document.getElementById('stop');


    // 开始抽奖
    start.onclick = startFun;
    stop.onclick = stopFun;
    // 键盘事件
    document.onkeyup = function(event){
      event = event || window.event;
      // console.log(event.keyCode);  //获取键码
      if (event.keyCode == 13) {
        if (flag == 0) {
          startFun();
          flag = 1;
        }else {
          stopFun();
          flag = 0;
        }
      }
    }
  }
  function startFun (){
    // var that = this;
    var start = document.getElementById('start');
    var title = document.getElementById('title');
    // 清除定时器
    clearInterval(timer); // 设定下一个定时器之前要先清除定时器；
    timer = setInterval(function(){
      var random = Math.floor(Math.random()*data.length);
      // console.log(random);
      title.innerHTML = data[random];
    }, 50);
    start.style.background = '#ddd';
  }
  function stopFun(){
    clearInterval(timer);
    start.style.background = '';
  }
</script>