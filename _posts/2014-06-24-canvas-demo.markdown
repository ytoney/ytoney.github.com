---
layout: post
title:  "canvas实例1——时钟"
date:   2014-06-24 15:40:34
categories: categories/demo
---

<canvas id="clock" width="500" height="500">您的浏览器不支持canvas，无法看到时钟</canvas>

<script type="text/javascript">
  var clock = document.getElementById('clock');
  var cxt = clock.getContext('2d');

  function drawClock(){
    cxt.clearRect(0,0,500,500);
    var now = new Date();
    var sec = now.getSeconds();
    var min = now.getMinutes();
    var hour = now.getHours();
    // 小时必须获取浮点类型(小时+分针数转化为小时)
    hour = hour + min/60;


    // 问题  19:23:30
    // 将24小时进制转换为12小时
    hour = hour>12?hour-12:hour;

    // 表盘(蓝色)
    cxt.lineWidth = 10;
    cxt.strokeStyle='blue'
    cxt.beginPath();
    cxt.arc(250,250,200,0,360,false);
    cxt.closePath();
    cxt.stroke();

    // 刻度
      // 时刻度
        for(var i = 0; i < 12; i++){
          cxt.save();
          cxt.lineWidth = 7;
          cxt.strokeStyle = '#000000';
          // 设置0,0点
          cxt.translate(250,250);
          // 设置旋转角度
          cxt.rotate(i*30*Math.PI/180);//角度*Math.PI/180
          cxt.beginPath();
          cxt.moveTo(0,-170);
          cxt.lineTo(0,-190);
          cxt.closePath()
          cxt.stroke();
          cxt.restore();
        }

      // 分刻度
        for(var i = 0; i < 60; i++){
          cxt.save();
          cxt.lineWidth = 5;
          cxt.strokeStyle = '#000000';
          cxt.translate(250,250);
          cxt.rotate(i*6*Math.PI/180);
          cxt.beginPath();
          cxt.moveTo(0,-180);
          cxt.lineTo(0, -190);
          cxt.closePath();
          cxt.stroke();
          cxt.restore();
        }
    // 指针
      // 时针
        cxt.save();
        cxt.lineWidth = 7;
        cxt.strokeStyle = '#000';

        // 设置0,0点
        cxt.translate(250,250);
        // 设置旋转角度
        cxt.rotate(hour*30*Math.PI/180);
        cxt.beginPath();
        cxt.moveTo(0,-120);
        cxt.lineTo(0,10);
        cxt.closePath();
        cxt.stroke();

        cxt.restore();
      // 分针
        cxt.save();
        cxt.translate(250,250);//设置0,0点
        cxt.rotate(min*6*Math.PI/180);
        cxt.strokeStyle = '#000';
        cxt.lineWidth = 7;

        cxt.beginPath();
        cxt.moveTo(0,-160);
        cxt.lineTo(0,15);
        cxt.closePath();
        cxt.stroke();
        cxt.restore();

      // 秒针
        cxt.save();
        cxt.strokeStyle = '#ff0000';
        cxt.lineWidth = 3;
        // 设置0,0点
        cxt.translate(250,250);
        // 角度
        cxt.rotate(sec*6*Math.PI/180);
        // 画图
        cxt.beginPath();
        cxt.moveTo(0,-170);
        cxt.lineTo(0,20);
        cxt.closePath();
        cxt.stroke();
        // 画出时针、分针、秒针的交叉点
        cxt.beginPath();
        cxt.arc(0,0,5,0,360,false);
        cxt.closePath();
        // 设置填充样式
        cxt.fillStyle = '#000';
        // cxt.strokeStyle = 'red';
        cxt.fill();
        cxt.stroke();

        cxt.beginPath();
        cxt.arc(0,-150,3,0,360);
        cxt.closePath();
        cxt.fill();
        cxt.stroke();
        cxt.restore();

  }

  drawClock();
  // 使用setInterval(代码，毫秒时间),让时钟动起来
    setInterval(drawClock,1000)
</script>