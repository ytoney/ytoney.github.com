---
layout: post
title:  "canvas实例-太阳系"
date:   2014-07-02 17:00:34
categories: categories/demo
---


<canvas id="solar" width="800" height="800">您的浏览器不支持canvas元素</canvas>


<style type="text/css">
  #solar{background: #000;}
</style>
<script type="text/javascript">
  // 获取canvas元素
  var solar = document.getElementById('solar');

  // 设置2d绘图元素
  var cxt = solar.getContext('2d');

  // 画轨道
  cxt.strokeStyle = '#fff';//设置笔触颜色

  cxt.beginPath();
  cxt.arc(400,400,100,0,360,false);
  cxt.closePath();
  cxt.stroke();

  // 画太阳
  cxt.beginPath();
  cxt.arc(400,400,20,0,360,false);
  cxt.closePath();
  cxt.fillStyle = 'red';//设置填充颜色（使用渐变色）
  cxt.fill();
  // 画地球
</script>