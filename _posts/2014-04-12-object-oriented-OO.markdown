---
layout: post
title:  "面向对象的程序设计"
date:   2014-04-12 07:30:34
categories: categories/js
---

ECMA-262把对象定义为：“无序属性地集合，其属性可以包括基本值、对象或者函数”。对象的每个属性或者方法都有一个名字，而每个名字都映射到一个值。正因为这样，我们可以把ECMAScript的对象想象成散列表：无非就是一组名值对，其中值可以是数据或函数。


<h2>创建对象</h2>

每个对象都是基于一个引用类型创建的。

创建自定义对象的最简单方式就是创建一个Object的实例，然后再为它添加属性和方法，如下所示：

<pre>
  var person = new Object();
  person.name = "Nicholas";
  person.age = 29;
  person.job = "Software Engineer";

  person.sayName = function(){
   alert(this.name)
  };

  person.sayName()
</pre>

<h4>对象字面量</h4>
<pre>
  var person = {
  name: 'Nicholas',
  age: 29,
  job: 'engineer',
  sayName: function(){
  alert(this.name)
}
};
</pre>

<p>以上这种创建新对象的方式有个明显的缺点：使用同一个接口创建很多对象，会产生大量的重复代码。为解决这个问题人们开始使用工厂模式的一种变体。</p>

<h2>工厂模式</h2>
<p>用函数来封装以特定接口创建对象的细节，如下面的例子所示：</p>

<pre>
  function createPerson(name, age, job){
    var o = new Object();
    o.name = name;
    o.age = age;
    o.job = job;
    o.sayName = function(){
    alert(this.name);
  };
    return o;//
  }

  var person1 = createPerson('jane','28','web-developer');
  person1.sayName();
</pre>
<p>工厂模式，虽然解决了创建多个相似对象的问题，但却没有解决对象识别的问题（即怎样知道一个对象的类型）。又出现了一个新的模式。</p>

<h2>构造函数模式</h2>


<script>
  var person = new Object();
  person.name = 'Nicholas00';
  person.age = 29;
  person.job = 'web-developer';
  person.sayName = function(){
    console.log(person.name)
  };
  // person.sayName()


  //工厂模式
  // var createPerson = function(name,age,job){
  function createPerson (name,age,job){
    var o = new Object();
    o.name = name;
    o.age = 28;
    o.job = job;
    o.sayName = function(){
      console.log(o.name)
    };
    return o;
  };

  person1 = createPerson('Jane',29,'web-developer')
  // person1.sayName()

  //构造函数模式
  function Person(name,age,job){
    this.name = name;
    this.age = age;
    this.job = job;
    this.sayName = function(){
      console.log(this.name)
    };
  }

  var person1 = new Person('Jane',29,'web-developer');
  // person1.sayName()
  Person('Greg',20,'engineer')
  // window.sayName()

  function Person(name,age,job){
    this.name = name;
    this.age = age;
    this.job = job;
    this.sayName = sayName;
  }

  function sayName() {
    console.log(this.name)
  }

  var person1 = new Person('jane',10,'FE');
  var person2 = new Person('jane2',20,'WD');
  // person1.sayName()
  // person2.sayName()
  console.log(person1.sayName == person2.sayName)
</script>
