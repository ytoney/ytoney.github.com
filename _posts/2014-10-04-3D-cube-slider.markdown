---
layout: post
title:  "css3-3D立方体图片旋转"
date:   2014-10-04 23:00:34
categories: categories/demo
---


<div id="wrapper" class="clearfix">
  <div class="slider-outer">
    <div class="slider-inner rotate" id="slider-inner">
      <div data-slide="1" class="slide front">
        <div class="slide-title">Slide 1<i class="fa fa-html5"></i></div>
      </div>
      <div data-slide="2" class="slide top">
        <div class="slide-title">Slide 2<i class="fa fa-css3"></i></div>
      </div>
      <div data-slide="3" class="slide back">
        <div class="slide-title">Slide 3<i class="fa fa-android"></i></div>
      </div>
      <div data-slide="4" class="slide bottom">
        <div class="slide-title">Slide 4<i class="fa fa-mobile-phone"></i></div>
      </div>
    </div>
  </div>
  <nav id="nav" class="clearfix">
    <ul class="clearfix unstyled">
      <li><a href="href" data-slide="1" class="btn active">1</a></li>
      <li><a href="href" data-slide="2" class="btn">2</a></li>
      <li><a href="href" data-slide="3" class="btn">3</a></li>
      <li><a href="href" data-slide="4" class="btn">4</a></li>
    </ul>
  </nav>
</div>

<style type="text/css">
  .slider-outer{
    -webkit-perspective: 1600px;
    -moz-perspective: 1600px;
    -o-perspective: 1600px;
    -ms-perspective: 1600px;
  }
  .slider-inner{
    width: 100%;
    height: 200px;
    margin: 0 auto;
    position: relative;

    -webkit-transform-style: preserve-3d;
    -moz-transform-style: preserve-3d;
    -o-transform-style: preserve-3d;
    -ms-transform-style: preserve-3d;
    -webkit-transition: all 0.3s linear;
    -moz-transition: all 0.3s linear;
    -o-transition: all 0.3s linear;
    -ms-transition: all 0.3s linear;
    -webkit-transform-origin: 50% 100%;
    -moz-transform-origin: 50% 100%;
    -o-transform-origin: 50% 100%;
    -ms-transform-origin: 50% 100%;
  }
  .slider-inner.rotate.one{
    /*transform: rotateX(0) translateY(200px);*/
  }
  .slider-inner.rotate.two{
    transform: rotateX(-90deg) translateY(200px);
  }
  .slider-inner.rotate.three{
    transform: rotateX(-180deg) translateY(200px) translateZ(200px);
  }
  .slider-inner.rotate.four{
    transform: rotateX(-270deg) translateY(0) translateZ(200px);
  }

  .slide-title{
    font-size: 70px;
    line-height: 70px;
    font-weight: 100;
  }

  .slide{
    position: absolute;
    width: 94%;
    height: 160px;
    padding: 20px 3%;
    color: #4ecdc4;

    -webkit-transform-origin: 0% 0%;
    -moz-transform-origin: 0% 0%;
    -o-transform-origin: 0% 0%;
    -ms-transform-origin: 0% 0%;
  }
  .slide.front{
    background-color: beige;
    opacity: 0.9;
  }
  .slide.top{
    background-color: #556270;
    opacity: 0.9;
    z-index: 1;

    transform: rotateX(90deg) translateY(-200px);
  }
  .slide.back{
    background-color: #ff4747;
    opacity: 0.9;
    color: #fff;

    transform: rotateX(180deg) translateY(-200px) translateZ(200px);
  }
  .slide.bottom{
    background: #4ecdc4;
    background-color: #36c1b7;
    opacity: 0.9;
    color: #fff;

    transform: rotateX(-90deg) translateZ(200px);
  }

  /*nav*/
  #nav {
    display: block;
    position: relative;
    width: 100%;
    margin-top: 27px;
    z-index: 10;
  }
  #nav ul {
    display: block;
    padding: 0;
    margin: 0;
    text-align: center;
  }
  #nav ul li {
    display: inline-block;
    font-size: 18px;
  }
  #nav ul li:nth-of-type(4) {
    margin-right: 0;
  }
  #nav ul li a.btn {
    display: block;
    width: 20px;
    height: 20px;
    padding: 3px;
    color: #4ecdc4;
    border: 1px solid #4ecdc4;
    border-radius: 50%;
    font-weight: 300;
    line-height: 20px;
    text-align: center;
    text-decoration: none;
    background-image: none;
    background-color: transparent;
    box-shadow: inset 0 0 2px rgba(78,205,196, 0.3);
    -webkit-transition: all 0.2s linear;
    -moz-transition: all 0.2s linear;
    -o-transition: all 0.2s linear;
    -ms-transition: all 0.2s linear;
  }
  #nav ul li a.btn:focus, #nav ul li a.btn:hover,#nav ul li a.btn.active {
    color: #ff6b6b;
    border-color: #ff6b6b;
    background-color: transparent;
    box-shadow: inset 0 0 2px rgba(255,107,107, 0.3);

  }
</style>

<script type="text/javascript">
  window.onload = function () {
    var curA = document.getElementById('nav').getElementsByTagName('a');
    var sliderInner = document.getElementById('slider-inner');
    var innerClass = {
      1: 'one',
      2: 'two',
      3: 'three',
      4: 'four'
    }
    for(var i = 0; i < curA.length; i++){
      curA[i].onclick = function(){
        var curIndex = parseInt(this.getAttribute('data-slide'))-1;
        for(var j = 0; j<curA.length; j++){
          curA[j].className = 'btn';
          curA[curIndex].className = 'btn active';
          // console.log(curIndex)
          console.log(innerClass[curIndex+1])
          sliderInner.className = 'slider-inner rotate';
          sliderInner.className = 'slider-inner rotate ' + innerClass[curIndex + 1];
        }

      }
    }
  }
</script>