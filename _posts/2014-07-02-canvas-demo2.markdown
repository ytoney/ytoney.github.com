---
layout: post
title:  "canvas实例-太阳系"
date:   2014-07-02 17:00:34
categories: categories/demo
---


<canvas id="solar" width="800" height="800">您的浏览器不支持canvas元素</canvas>
<canvas id="canvas" width="800" height="800">您的浏览器不支持canvas元素</canvas>


<style type="text/css">
  #solar,#canvas{background: #000;}
</style>
<script type="text/javascript">
  // 获取canvas元素
  var solar = document.getElementById('solar');

  // 设置2d绘图元素
  var cxt = solar.getContext('2d');

  // 声明一个时间参数(1->1天)
  var time = 0;

  function draw(){
    // 清除画布（清除之前的内容，重新画）
    cxt.clearRect(0,0,800,800);
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
    //设置太阳的填充颜色（使用渐变色）
      //createRadialGradient(圆心x,圆心y,半径,圆心x,圆心y,外半径)
    var sunColor = cxt.createRadialGradient(400,400,0,400,400,20);
    sunColor.addColorStop(0,'#f00');
    sunColor.addColorStop(1,'#f90');
    cxt.fillStyle = sunColor;
    cxt.fill();
    // 画地球
    cxt.save();
      // 设置异次元空间的0,0点
      cxt.translate(400,400);
      // 设置旋转角度
      // cxt.rotate(90*Math.PI/180);
      // 地球公转一周需要365天，time=1天 一天转365/360度
      cxt.rotate(time*365/360*Math.PI/180);

      cxt.beginPath();
      cxt.arc(0,-100,10,0,360,false);
      cxt.closePath();
      // 设置地球的颜色
      var earthColor = cxt.createRadialGradient(0,-100,0,0,-100,10);
      earthColor.addColorStop(0,'#78b1e8');
      earthColor.addColorStop(1,'#050c12');
      cxt.fillStyle = earthColor;
      cxt.fill();
    cxt.restore();

    // 每画一次图像，时间加一
    time += 1;
  }
  // 使地球动起来
  setInterval(draw,10)



  var canvas = document.getElementById('canvas');
  var cxt2 = canvas.getContext('2d');

  // 轨道
  function drawTrack(){
    for(var i = 0; i < 8; i++){
      cxt2.beginPath();
      cxt2.arc(400,400,(i+1)*50,0,360,false);
      cxt2.closePath();
      // 设置笔触的颜色
      cxt2.strokeStyle = '#fff';
      cxt2.stroke();
    }
  }
  drawTrack();

  // 星球
  function Star(x,y,radius,cycle,sColor,eColor){
    // 画出星球需要哪些属性
    // 星球的坐标点
    this.x = x;
    this.y = y;
    // 星球的半径
    this.radius = radius;
    // 公转周期
    this.cycle = cycle;
    // 星球的颜色（开始色和结束色）
    this.sColor = sColor;
    this.eColor = eColor;
    // 新建一个渐变颜色空对象
    this.color = null;
    // 设置一个计时器
    this.time = 0;

    this.draw = function(){

      cxt2.save();
        // 重置0,0点
        cxt2.translate(400,400);
        // 设置旋转角度
        cxt2.rotate(this.time*(360/this.cycle)*Math.PI/180);
        // 画星球
        cxt2.beginPath();
        cxt2.arc = (this.x,this.y,this.radius,0,360,false);
        cxt2.closePath();
        // 填充星球颜色
        this.color = cxt2.createRadialGradient(this.x,this.y,0,this.x,this.y,this.radius);
        this.color.addColorStop(0,this.sColor);
        this.color.addColorStop(1,this.eColor);
        cxt2.fillStyle = this.color;
        cxt2.fill();
      cxt2.restore();
      // 执行完毕后时间增加
      this.time += 1;

    }
  }

  function Sun(){
    Star.call(this,0,0,20,0,'#f00','#f90');
  }
  var sunb = new Sun();
  sunb.draw();
















</script>