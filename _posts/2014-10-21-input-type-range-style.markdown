---
layout: post
title:  "input type range自定义样式"
date:   2014-10-21 10:53:09
categories: categories/css3
---




<div>
  默认样式：
  <input type="range">
</div>

<div class="myrange">
  自定义样式：
  <input type="range">
</div>



<style type="text/css">
.myrange input[type="range"] {
  display: inline-block;
  overflow: hidden;
  margin-top: 5px;
  margin-bottom: 5px;
  padding-right: 2px;
  padding-left: 1px;
  width: auto;
  height: 35px;
  outline: none;
  background: -webkit-gradient(linear, 50% 0%, 50% 100%, color-stop(0%, #ccc), color-stop(100%, #ccc));
  background: linear-gradient(to right, #ccc 0%, #ccc 100%);
  background-position: center;
  background-size: 99% 4px;
  background-repeat: no-repeat;
  -webkit-appearance: none; }
.myrange input[type="range"]::-webkit-slider-thumb {
    position: relative;
    width: 20px;
    height: 20px;
    border-radius: 10px;
    background-color: #fff;
    box-shadow: 0 0 2px rgba(0, 0, 0, 0.5), 1px 3px 5px rgba(0, 0, 0, 0.25);
    cursor: pointer;
    -webkit-appearance: none; }
.myrange input[type="range"]::-webkit-slider-thumb:before {
    /* what creates the colorful line on the left side of the slider */
    position: absolute;
    top: 8px;
    left: -2001px;
    width: 2000px;
    height: 4px;
    background: #444;
    content: ' '; }
.myrange input[type="range"]::-webkit-slider-thumb:after {
    /* create a larger (but hidden) hit area */
    position: absolute;
    top: -20px;
    left: -20px;
    padding: 30px;
    content: ' '; }

</style>


<pre>
.myrange input[type="range"] {
  display: inline-block;
  overflow: hidden;
  margin-top: 5px;
  margin-bottom: 5px;
  padding-right: 2px;
  padding-left: 1px;
  width: auto;
  height: 35px;
  outline: none;
  background: -webkit-gradient(linear, 50% 0%, 50% 100%, color-stop(0%, #ccc), color-stop(100%, #ccc));
  background: linear-gradient(to right, #ccc 0%, #ccc 100%);
  background-position: center;
  background-size: 99% 4px;
  background-repeat: no-repeat;
  -webkit-appearance: none; }
.myrange input[type="range"]::-webkit-slider-thumb {
    position: relative;
    width: 20px;
    height: 20px;
    border-radius: 10px;
    background-color: #fff;
    box-shadow: 0 0 2px rgba(0, 0, 0, 0.5), 1px 3px 5px rgba(0, 0, 0, 0.25);
    cursor: pointer;
    -webkit-appearance: none; }
.myrange input[type="range"]::-webkit-slider-thumb:before {
    /* what creates the colorful line on the left side of the slider */
    position: absolute;
    top: 8px;
    left: -2001px;
    width: 2000px;
    height: 4px;
    background: #444;
    content: ' '; }
.myrange input[type="range"]::-webkit-slider-thumb:after {
    /* create a larger (but hidden) hit area */
    position: absolute;
    top: -20px;
    left: -20px;
    padding: 30px;
    content: ' '; }

</pre>