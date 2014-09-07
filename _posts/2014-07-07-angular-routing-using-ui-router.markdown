---
layout: post
title:  "angular-routing-using-ui-router"
date:   2014-07-07 14:59:34
categories: categories/js
---



使用UI-Router的AngularJS路由

AngularJS为制作单页的应用程序提供了一个强大的方式。我们在创建单页的应用程序时，路由是很重要的。我们希望我们的导航感觉像一个正常的网站，，还不使我们的网站刷新。我们已经仔细讲解过使用通常的ngRoute方法的Angular路由。

今天我们将看看使用UI-Router的路由。

概述

什么是AngularUI Router?

UI-Router是一个路由框架，它被用于AngularUI团队开发的AngularJS。这个框架提供一个与ngRoute不同的方法，这种方法改变你的应用程序视图基于应用程序的状态，而且也不只是路由URL。

States vs URL Route

使用这种方法，你的视图和路由并没有被绑定到该网站的URL上。这种方式，你可以改变你网站的部分使用路由，即使URL并没有改变。

当使用ngRoute的时，你必须要使用ngInclude或者其他的方法，这可能会让人困惑。现在你所有的状态、路由和视图都是通过你的.config()处理的，这将有助于自顶向下查看你的应用程序。


Sample Application

让我们做一些类似于其他路由教程，创建一个Home和About页面。

Setup

让我们开始我们的应用程序。我们将需要以下几个文件：

<pre>
- index.html          // will hold the main template for our app
- app.js            // our angular code
- partial-about.html      // about page code
- partial-home.html       // home page code
- partial-home-list.html    // injected into the home page
- table-data.html         // re-usable table that we can place anywhere
</pre>

理解我们的应用程序结构，编写一些文件：

{% highlight html%}
<!-- index.html -->

<!DOCTYPE html>
<html>
<head>

    <!-- CSS (load bootstrap) -->
    <link rel="stylesheet" href="//netdna.bootstrapcdn.com/bootstrap/3.1.1/css/bootstrap.min.css">
    <style>
        .navbar { border-radius:0; }
    </style>

    <!-- JS (load angular, ui-router, and our custom js file) -->
    <script src="http://code.angularjs.org/1.2.13/angular.js"></script>
    <script src="//cdnjs.cloudflare.com/ajax/libs/angular-ui-router/0.2.8/angular-ui-router.min.js"></script>
    <script src="app.js"></script>
</head>

<!-- apply our angular app to our site -->
<body ng-app="routerApp">

<!-- NAVIGATION -->
<nav class="navbar navbar-inverse" role="navigation">
    <div class="navbar-header">
        <a class="navbar-brand" ui-sref="#">AngularUI Router</a>
    </div>
    <ul class="nav navbar-nav">
        <li><a ui-sref="home">Home</a></li>
        <li><a ui-sref="about">About</a></li>
    </ul>
</nav>

<!-- MAIN CONTENT -->
<div class="container">

  <!-- THIS IS WHERE WE WILL INJECT OUR CONTENT ============================== -->
    <div ui-view></div>

</div>

</body>
</html>
{% endhighlight end %}

这是我们的HTML文件。我们将使用Bootstrap框架来改善我们的样式。请注意，我们除了载入Angular之外也加载了ui-router。UI Router从Angular核心被分离，就像ngRoute被分离一样。

用UI-Router创建链接的时候，你要使用ui-sref。通过ui-sref生成href，可以让它指向你的应用程序的某个状态。这些都是在你的app.js中被创建的。

{% highlight html %}
我们也可以用<div ui-view></div>代替ngRoute的<div ng-view></div>。
{% endhighlight %}

现在，让我们来看下Angular应用中的app.js吧。

{% highlight html %}
// app.js
var routerApp = angular.module('routerApp', ['ui.router']);

routerApp.config(function($stateProvider, $urlRouterProvider) {

    $urlRouterProvider.otherwise('/home');

    $stateProvider

        // HOME STATES AND NESTED VIEWS ========================================
        .state('home', {
            url: '/home',
            templateUrl: 'partial-home.html'
        })

        // ABOUT PAGE AND MULTIPLE NAMED VIEWS =================================
        .state('about', {
            // we'll get to this in a bit
        });

});
{% endhighlight %}

现在我们已经创建了这个routerApp，它已经被应用到index.html文件中的body上了。

在app.js中我们为home和about分别创建了.state()。在home页面中，我们使用了partial-home.html模板。

让我们为partial-home.html页面添些内容，以便我们可以确切地看到内容。

{% highlight html %}
<!-- partial-home.html -->
<div class="jumbotron text-center">
    <h1>The Homey Page</h1>
    <p>This page demonstrates <span class="text-danger">nested</span> views.</p>
</div>
{% endhighlight %}

现在我们就拥有自己的网站了！它不能实现很多，但是我们已经有了一个。
(demo效果图略)

在这些常规的东西完成之后，让我们看看为什么说UI-Router有一些很酷的特性吧。

嵌套视图（Home Page）

让我们看看如何嵌套视图。我们要添加两个按钮到home页，并且，在这个页面我们要根据我们点击的按钮显示不同的内容。

我们将添加按钮到partial-home.html文件中，然后打开Angular文件，查看我们如何改变它添加嵌套视图。

{% highlight html %}

<!-- partial-home.html -->

<div class="jumbotron text-center">
    <h1>The Homey Page</h1>
    <p>This page demonstrates <span class="text-danger">nested</span> views.</p>

    <a ui-sref=".list" class="btn btn-primary">List</a>
    <a ui-sref=".paragraph" class="btn btn-danger">Paragraph</a>
</div>

<div ui-view></div>

当我们要链接到一个嵌套视图的时候，要使用点标记，如：ui-sref=".list" 和ui-sref=".pargraph"。这些点标记将在Angular文件中定义，一旦我们在这里设置了它，我们将注入新的<div ui-view></div>。
{% endhighlight %}

在app.js文件中，让我们创建这些嵌套的状态。


{% highlight html %}

// app.js
...

$stateProvider

  // HOME STATES AND NESTED VIEWS ========================================
    .state('home', {
        url: '/home',
        templateUrl: 'partial-home.html'
    })

  // nested list with custom controller
  .state('home.list', {
        url: '/list',
        templateUrl: 'partial-home-list.html',
        controller: function($scope) {
            $scope.dogs = ['Bernese', 'Husky', 'Goldendoodle'];
        }
    })

  // nested list with just some random string data
    .state('home.paragraph', {
        url: '/paragraph',
        template: 'I could sure use a drink right now.'
    })

...
{% endhighlight %}

现在，我们在home.html文件中定义的ui-sref被连接到一个实际的状态。通过创建home.list和home.paragraph，这些链接将得到提供的模板并将它注入到ui-view中。

我们需要为home页做的最后一件事是定义partial-home-list.html文件。We have also passed in a controller with a list of dogs that we will use in the template file.

{% highlight html %}

<!-- partial-home-list.html -->

<ul>
    <li ng-repeat="dog in dogs">{{ dog }}</li>
</ul>
{% endhighlight %}


现在，当我们点击list按钮时，它会将我们的dogs列表注入到模板中。或者，如果我们单击Paragraph按钮的时候，它会将我们给定的字符串注入到模板中。

你可以看到，根据state是多么容易改变应用程序的不同部分。我们不必用ngInclude、ngShow、ngHide、或者ngIf做任何形式的工作。这样可以保持我们的视图文件的简洁，因为所有的工作都是在app.js中完成的。

让我们继续，看我们如何拥有多视图。

多视图 (About Page)

在你的应用中拥有多视图是非常强大的。也许在你的网站里有一个边栏，里边有一些内容，像Popular Posts、Recent Posts、Users、或者其他任何内容。这些内容也可以被分离，注入到我们的模板中。每一个都拥有自己的controller和模板文件，所以我们的app保持简洁。

我们的应用像这样模块化也可以让我们在不同的模板中重用数据。

对于About页面，我们做两列并且每列都有自己的数据。我们首先要处理视图，然后再看我们用UI-Router如何实现this。

{% highlight html %}

<!-- partial-about.html -->

<div class="jumbotron text-center">
    <h1>The About Page</h1>
    <p>This page demonstrates <span class="text-danger">multiple</span> and <span class="text-danger">named</span> views.</p>
</div>

<div class="row">

    <!-- COLUMN ONE NAMED VIEW -->
    <div class="col-sm-6">
        <div ui-view="columnOne"></div>
    </div>

    <!-- COLUMN TWO NAMED VIEW -->
    <div class="col-sm-6">
        <div ui-view="columnTwo"></div>
    </div>

</div>
{% endhighlight %}

这个文件中有两个视图，一个是columnOne，另一个是columnTwo。

为什么有人愿意用这种方式呢？这是一个很好的问题。我们创建一个很模块化的应用，这困惑吗？官方UI-Router文档里提到，有一个例子讲为什么你会有多个命名视图。在他们的例子中，展示应用的不同部分。每一部分都有它自己的数据，所以每一部分都有自己的controller和模板文件使得很容易创建像这样的东西。

到现在，我们所有的视图都被创建了，接下来让我们看看我们如何将模板文件和控制器应用到每一个视图。让我们回到app.js文件。


{% highlight html %}

// app.js

...

    .state('about', {
        url: '/about',
        views: {

            // the main template will be placed here (relatively named)
            '': { templateUrl: 'partial-about.html' },

            // the child views will be defined here (absolutely named)
            'columnOne@about': { template: 'Look I am a column!' },

            // for column two, we'll define a separate controller
            'columnTwo@about': {
                templateUrl: 'table-data.html',
                controller: 'scotchController'
            }
        }

    });

}); // closes $routerApp.config()


// let's define the scotch controller that we call up in the about state
routerApp.controller('scotchController', function($scope) {

    $scope.message = 'test';

    $scope.scotches = [
        {
            name: 'Macallan 12',
            price: 50
        },
        {
            name: 'Chivas Regal Royal Salute',
            price: 10000
        },
        {
            name: 'Glenfiddich 1937',
            price: 20000
        }
    ];

});

...

{% endhighlight %}

像这样，我们的About页面就已经准备好了。现在也许还是很困惑，我们如何为about state在视图中嵌套每件事情。为什么没有为主页定义一个templateUrl，然后在一个嵌套视图对象中定义columns？这个原因就是给我们的真正伟大的工具。

相对命名和绝对命名

UI-Router分配给每一个视图一个绝对的命名。绝对命名的结构是viewName@stateName。因为我们主要的ui-view在about state里，我们就给它一个空白的名字。另外两个视图是columnOne@about和columnTwo@about。

Having the naming scheme this way let’s us define multiple views inside a single state. The docs explain this concept very well and I’d encourage taking a look at their examples. Extremely powerful tools there.

总结

这是一篇关于强大工具UI-Router的概述。你能用它做的事情是令人难以置信的，当你看见你的应用程序作为states而不是ngRoute的时候，Angular应用可以很容易的被创建为模块化的和可扩展的。




<a href="http://scotch.io/tutorials/javascript/angular-routing-using-ui-router">http://scotch.io/tutorials/javascript/angular-routing-using-ui-router</a>









