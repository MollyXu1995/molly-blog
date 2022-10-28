---
title: "JQuery知识总结"
date: 2022-10-26T14:07:45+08:00
tags: ['Frontend Framework']
series: ['前端学习之旅']
---

## 简介与使用
### 概述

一、JavaScript 库
- JavaScript库：即 library，是一个封装好的特定的集合（方法和函数）。
- 简单理解： 就是一个JS 文件，里面对我们原生js代码进行了封装，存放到里面。这样我们可以快速高效的使用这些封装好的功能了。
- 比如 jQuery，就是为了快速方便的操作DOM，里面基本都是函数（方法）。
- 常见的JavaScript 库
    - jQuery
    - Prototype
    - YUI
    - Dojo
    - Ext JS
    - 移动端的zepto

二、jQuery 的概念
- jQuery 是一个快速、简洁的 JavaScript 库
- j 就是 JavaScript；   Query 查询； 意思就是查询js，把js中的DOM操作做了封装。
- 学习jQuery本质： 就是学习调用这些函数（方法）。

三、jQuery 的优点

- 轻量级。核心文件才几十kb，不会影响页面加载速度
- 跨浏览器兼容。基本兼容了现在主流的浏览器
- 链式编程、隐式迭代
- 对事件、样式、动画支持，大大简化了DOM操作
- 支持插件扩展开发。有着丰富的第三方的插件，例如：树形菜单、日期控件、轮播图等
- 免费、开源

### jQuery 的下载与使用
一、下载  

1、官网地址： <https://jquery.com/>

2、版本：
- 1x ：兼容 IE 678 等低版本浏览器， 官网不再更新  
- 2x ：不兼容 IE 678 等低版本浏览器， 官网不再更新  
- 3x ：不兼容 IE 678 等低版本浏览器， 是官方主要更新维护的版本

各个版本的下载：<https://code.jquery.com/>

二、使用步骤

1.  引入 jQuery 文件
2.  使用即可

### jQuery 的入口函数

一、入口函数

```html
<head>
    <script src="jquery.min.js"></script>
    <style>
        div {
            width: 200px;
            height: 200px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <script>
        // $('div').hide();
        // 1. 等着页面DOM加载完毕再去执行js 代码
        // $(document).ready(function() {
        //     $('div').hide();
        // })
        // 2.  等着页面DOM加载完毕再去执行js 代码
        $(function() {
            $('div').hide(); // 隐藏div

        });
    </script>
    <div></div>

</body>
```

二、jQuery 的顶级对象 $

```html
<head>
    <script src="jquery.min.js"></script>
    <style>
        div {
            width: 200px;
            height: 200px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div></div>
    <script>
        // 1. $ 是jQuery的别称（另外的名字）。在代码中可以使用 jQuery 代替 $，但一般为了方便，通常都直接使用 $ 。

        // $(function() {
        //     alert(11)
        // });
        jQuery(function() {
            // alert(11)
            // $('div').hide();
            jQuery('div').hide();
        });
        // 2. $同时也是jQuery的 顶级对象
    </script>
</body>
```

### jQuery 对象和 DOM 对象
一、jQuery 对象和 DOM 对象 

```html
<head>
    <script src="jquery.min.js"></script>
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div></div>
    <span></span>
    <script>
        // 1. DOM 对象：  用原生js获取过来的对象就是DOM对象
        var myDiv = document.querySelector('div'); // myDiv 是DOM对象
        var mySpan = document.querySelector('span'); // mySpan 是DOM对象
        console.dir(myDiv);
        // 2. jQuery对象： 用jquery方式获取过来的对象是jQuery对象。 本质：通过$把DOM元素进行了包装
        $('div'); // $('div')是一个jQuery 对象
        $('span'); // $('span')是一个jQuery 对象
        console.dir($('div'));
        // 3. jQuery 对象只能使用 jQuery 方法，DOM 对象则使用原生的 JavaScirpt 属性和方法
        // myDiv.style.display = 'none';
        // myDiv.hide(); myDiv是一个dom对象不能使用 jquery里面的hide方法
        // $('div').style.display = 'none'; 这个$('div')是一个jQuery对象不能使用原生js 的属性和方法
    </script>
</body>
```

二、 jQuery 对象和 DOM 对象相互转换

```html
<head>
    <script src="jquery.min.js"></script>
</head>

<body>
    <video src="mov.mp4" muted></video>
    <script>
        // 1. DOM对象转换为 jQuery对象
        // (1) 我们直接获取视频，得到就是jQuery对象
        // $('video');
        // (2) 我们已经使用原生js 获取过来 DOM对象
        var myvideo = document.querySelector('video');
        // $(myvideo).play();  jquery里面没有play 这个方法

        // 2.  jQuery对象转换为DOM对象
        // myvideo.play();
        // 方式一：
        $('video')[0].play()  // 0 是索引号index           
        // 方式二：
        $('video').get(0).play()  // 0 是索引号index
    </script>
</body>
```

## jQuery 常用API 
### 选择器
#### 基础和层级选择器
- 原生 JS 获取元素方式很多，很杂，而且兼容性情况不一致，因此 jQuery 给我们做了封装，使获取元素统一标准。
- `$("选择器") ` 里面选择器直接写 CSS 选择器即可，但是要加引号      

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221016/image.72bld0npda00.webp)

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221016/image.cfqczc28a5s.webp)

```html
<head>
    <script src="jquery.min.js"></script>
</head>

<body>
    <div>我是div</div>
    <div class="nav">我是nav div</div>
    <p>我是p</p>
    <ol>
        <li>我是ol 的</li>
        <li>我是ol 的</li>
        <li>我是ol 的</li>
        <li>我是ol 的</li>
    </ol>
    <ul>
        <li>我是ul 的</li>
        <li>我是ul 的</li>
        <li>我是ul 的</li>
        <li>我是ul 的</li>
    </ul>
    <script>
        $(function() {
            console.log($(".nav"));
            console.log($("ul li"));
        })
    </script>
</body>
```

#### 隐式迭代（重要）
- 遍历内部 DOM 元素（伪数组形式存储）的过程就叫做隐式迭代。
- 简单理解：给匹配到的所有元素进行循环遍历，执行相应的方法，而不用我们再进行循环，简化我们的操作，方便我们调用。

```html
<head>
    <script src="jquery.min.js"></script>
</head>

<body>
    <div>惊喜不，意外不</div>
    <div>惊喜不，意外不</div>
    <div>惊喜不，意外不</div>
    <div>惊喜不，意外不</div>
    <ul>
        <li>相同的操作</li>
        <li>相同的操作</li>
        <li>相同的操作</li>
    </ul>
    <script>
        // 1. 获取四个div元素 
        console.log($("div"));

        // jQuery 设置样式:    $('div').css('属性', '值')      
        // 2. 给四个div设置背景颜色为粉色，四个li设置为红色字
        // jquery对象不能使用style
        $("div").css("background", "pink");
        $("ul li").css("color", "red");

        // 3. 隐式迭代就是把匹配的所有元素内部进行遍历循环，给每一个元素添加css这个方法
    </script>
</body>
```

#### 筛选选择器

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221016/image.4g3erbjiw0s0.webp)

```html
<head>
    <script src="jquery.min.js"></script>
</head>

<body>
    <ul>
        <li>多个里面筛选几个</li>
        <li>多个里面筛选几个</li>
        <li>多个里面筛选几个</li>
        <li>多个里面筛选几个</li>
        <li>多个里面筛选几个</li>
        <li>多个里面筛选几个</li>
    </ul>
    <ol>
        <li>多个里面筛选几个</li>
        <li>多个里面筛选几个</li>
        <li>多个里面筛选几个</li>
        <li>多个里面筛选几个</li>
        <li>多个里面筛选几个</li>
        <li>多个里面筛选几个</li>
    </ol>
    <script>
        $(function() {
            $("ul li:first").css("color", "red");
            $("ul li:eq(2)").css("color", "blue");
            $("ol li:odd").css("color", "skyblue");
            $("ol li:even").css("color", "pink");
        })
    </script>
</body>
```

#### 筛选方法（重点）
- 重点记住：`parent()  children()  find()  siblings()  eq()`

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221016/image.m9pklc9r6i8.webp)

```html
<head>
    <script src="jquery.min.js"></script>
</head>

<body>
    <div class="yeye">
        <div class="father">
            <div class="son">儿子</div>
        </div>
    </div>

    <div class="nav">
        <p>我是屁</p>
        <div>
            <p>我是p</p>
        </div>
    </div>
    <script>
        // 注意一下都是方法 带括号
        $(function() {
            // 1. 父  parent()  返回的是 最近一级的父级元素 亲爸爸
            console.log($(".son").parent()); // father

            // 2. 子
            // (1) 亲儿子 children()  类似子代选择器  ul>li
            $(".nav").children("p").css("color", "red"); // 我是屁

            // (2) 可以选里面所有的孩子 包括儿子和孙子  find() 类似于后代选择器
            $(".nav").find("p").css("color", "red"); // 我是屁 我是p
        });
    </script>
</body>
```

```html
<head>
    <script src="jquery.min.js"></script>
</head>

<body>
    <ol>
        <li>我是ol 的li</li>
        <li>我是ol 的li</li>
        <li class="item">我是ol 的li</li>
        <li>我是ol 的li</li>
        <li>我是ol 的li</li>
        <li>我是ol 的li</li>
    </ol>
    <ul>
        <li>我是ol 的li</li>
        <li>我是ol 的li</li>
        <li>我是ol 的li</li>
        <li>我是ol 的li</li>
        <li>我是ol 的li</li>
        <li>我是ol 的li</li>
    </ul>
    <div class="current">俺有current</div>
    <div>俺木有current</div>
    <script>
        // 注意一下都是方法 带括号
        $(function() {
            // 1. 兄弟元素siblings 除了自身元素之外的所有亲兄弟
            $("ol .item").siblings("li").css("color", "red");

            // 2. 第n个元素
            var index = 2;
            // (1) 我们可以利用选择器的方式选择
            $("ul li:eq(2)").css("color", "blue");
            // $("ul li:eq("+index+")").css("color", "blue");

            // (2) 我们可以利用选择方法的方式选择  更推荐这种写法
            $("ul li").eq(2).css("color", "blue");
            // $("ul li").eq(index).css("color", "blue");

            // 3. 判断是否有某个类名
            console.log($("div:first").hasClass("current")); // true 
            console.log($("div:last").hasClass("current")); // false

        });
    </script>
</body>
```

案例：新浪下拉菜单
```html
<head>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        li {
            list-style-type: none;
        }
        
        a {
            text-decoration: none;
            font-size: 14px;
        }
        
        .nav {
            margin: 100px;
        }
        
        .nav>li {
            position: relative;
            float: left;
            width: 80px;
            height: 41px;
            text-align: center;
        }
        
        .nav li a {
            display: block;
            width: 100%;
            height: 100%;
            line-height: 41px;
            color: #333;
        }
        
        .nav>li>a:hover {
            background-color: #eee;
        }
        
        .nav ul {
            display: none;
            position: absolute;
            top: 41px;
            left: 0;
            width: 100%;
            border-left: 1px solid #FECC5B;
            border-right: 1px solid #FECC5B;
        }
        
        .nav ul li {
            border-bottom: 1px solid #FECC5B;
        }
        
        .nav ul li a:hover {
            background-color: #FFF5DA;
        }
    </style>
    <script src="jquery.min.js"></script>
</head>

<body>
    <ul class="nav">
        <li>
            <a href="#">微博</a>
            <ul>
                <li>
                    <a href="">私信</a>
                </li>
                <li>
                    <a href="">评论</a>
                </li>
                <li>
                    <a href="">@我</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul>
                <li>
                    <a href="">私信</a>
                </li>
                <li>
                    <a href="">评论</a>
                </li>
                <li>
                    <a href="">@我</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul>
                <li>
                    <a href="">私信</a>
                </li>
                <li>
                    <a href="">评论</a>
                </li>
                <li>
                    <a href="">@我</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul>
                <li>
                    <a href="">私信</a>
                </li>
                <li>
                    <a href="">评论</a>
                </li>
                <li>
                    <a href="">@我</a>
                </li>
            </ul>
        </li>
    </ul>
    <script>
        $(function() {
            // 鼠标经过
            $(".nav>li").mouseover(function() {
                // $(this) jQuery 当前元素  this不要加引号
                // show() 显示元素  hide() 隐藏元素
                $(this).children("ul").show();
            });
            // 鼠标离开
            $(".nav>li").mouseout(function() {
                $(this).children("ul").hide();
            })
        })
    </script>
</body>
```

#### 里面的排他思想
- 想要多选一的效果，排他思想：当前元素设置样式，其余的兄弟元素清除样式。
- `$(this).css("color","red");`    
`$(this).siblings(). css("color","");`  

```html
<head>
    <script src="jquery.min.js"></script>
</head>

<body>
    <button>快速</button>
    <button>快速</button>
    <button>快速</button>
    <button>快速</button>
    <button>快速</button>
    <button>快速</button>
    <button>快速</button>
    <script>
        $(function() {
            // 1. 隐式迭代 给所有的按钮都绑定了点击事件
            $("button").click(function() {
                // 2. 当前的元素变化背景颜色
                $(this).css("background", "pink");
                // 3. 其余的兄弟去掉背景颜色 隐式迭代
                $(this).siblings("button").css("background", "");
            });
        })
    </script>
</body>
```

案例：淘宝服饰精品案例  
核心原理：  
1、鼠标经过左侧盒子某个小li，就让内容区盒子相对应图片显示，其余的图片隐藏。  
2、需要得到当前小li 的索引号，就可以显示对应索引号的图片  
3、jQuery 得到当前元素索引号 $(this).index()    
4、中间对应的图片，可以通过  eq(index) 方法去选择   
5、显示元素 show()   隐藏元素 hide()  

```html
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style type="text/css">
        * {
            margin: 0;
            padding: 0;
            font-size: 12px;
        }
        
        ul {
            list-style: none;
        }
        
        a {
            text-decoration: none;
        }
        
        .wrapper {
            width: 250px;
            height: 248px;
            margin: 100px auto 0;
            border: 1px solid pink;
            border-right: 0;
            overflow: hidden;
        }
        
        #left,
        #content {
            float: left;
        }
        
        #left li {
            background: url(images/lili.jpg) repeat-x;
        }
        
        #left li a {
            display: block;
            width: 48px;
            height: 27px;
            border-bottom: 1px solid pink;
            line-height: 27px;
            text-align: center;
            color: black;
        }
        
        #left li a:hover {
            background-image: url(images/abg.gif);
        }
        
        #content {
            border-left: 1px solid pink;
            border-right: 1px solid pink;
        }
    </style>
    <script src="jquery.min.js"></script>
    <script>
        $(function() {
            // 1. 鼠标经过左侧的小li 
            $("#left li").mouseover(function() {
                // 2. 得到当前小li 的索引号
                var index = $(this).index();
                console.log(index);
                // 3. 让我们右侧的盒子相应索引号的图片显示出来就好了
                // $("#content div").eq(index).show();
                // 4. 让其余的图片（就是其他的兄弟）隐藏起来
                // $("#content div").eq(index).siblings().hide();
                // 链式编程
                $("#content div").eq(index).show().siblings().hide();

            })
        })
    </script>
</head>

<body>
    <div class="wrapper">
        <ul id="left">
            <li><a href="#">女靴</a></li>
            <li><a href="#">雪地靴</a></li>
            <li><a href="#">冬裙</a></li>
            <li><a href="#">呢大衣</a></li>
            <li><a href="#">毛衣</a></li>
            <li><a href="#">棉服</a></li>
            <li><a href="#">女裤</a></li>
            <li><a href="#">羽绒服</a></li>
            <li><a href="#">牛仔裤</a></li>
        </ul>
        <div id="content">
            <div>
                <a href="#"><img src="images/女靴.jpg" width="200" height="250" /></a>
            </div>
            <div>
                <a href="#"><img src="images/雪地靴.jpg" width="200" height="250" /></a>
            </div>
            <div>
                <a href="#"><img src="images/冬裙.jpg" width="200" height="250" /></a>
            </div>
            <div>
                <a href="#"><img src="images/呢大衣.jpg" width="200" height="250" /></a>
            </div>
            <div>
                <a href="#"><img src="images/毛衣.jpg" width="200" height="250" /></a>
            </div>
            <div>
                <a href="#"><img src="images/棉服.jpg" width="200" height="250" /></a>
            </div>
            <div>
                <a href="#"><img src="images/女裤.jpg" width="200" height="250" /></a>
            </div>
            <div>
                <a href="#"><img src="images/羽绒服.jpg" width="200" height="250" /></a>
            </div>
            <div>
                <a href="#"><img src="images/牛仔裤.jpg" width="200" height="250" /></a>
            </div>

        </div>

    </div>
</body>
```

#### 链式编程
- 链式编程是为了节省代码量，看起来更优雅。
- 使用链式编程一定注意是哪个对象执行样式.
- `$(this).css('color', 'red').sibling().css('color', ''); `

```html
<head>
    <script src="jquery.min.js"></script>
</head>

<body>
    woshi body 的文字
    <button>快速</button>
    <button>快速</button>
    <button>快速</button>
    <button>快速</button>
    <button>快速</button>
    <button>快速</button>
    <button>快速</button>
    <script>
        $(function() {
            // 1. 隐式迭代 给所有的按钮都绑定了点击事件
            $("button").click(function() {
                // 2. 让当前元素颜色变为红色
                // $(this).css("color", "red");
                // 3. 让其余的姐妹元素不变色 
                // $(this).siblings().css("color", "");
                // 链式编程
                // $(this).css("color", "red").siblings().css("color", "");
                // 我的颜色为红色, 我的兄弟的颜色为空
                // $(this).siblings().css('color', 'red');
                // 我的兄弟变为红色  ,我本身不变颜色
                $(this).siblings().parent().css('color', 'blue');
                // 最后是给我的兄弟的爸爸 body 变化颜色 

            });
        })
    </script>
</body>
```

### 样式操作
#### 操作 css 方法

jQuery 可以使用 css 方法来修改简单元素样式； 也可以操作类，修改多个样式。

1、参数只写属性名，则是返回属性值
- `$(this).css("color");`

2、参数是属性名，属性值，逗号分隔，是设置一组样式，属性必须加引号，值如果是数字可以不用跟单位和引号
- `$(this).css("color","red");`

3、参数可以是对象形式，方便设置多组样式。属性名和属性值用冒号隔开， 属性可以不用加引号，值是数字可以不用跟单位和引号。值不是数字，则需要加引号
- `$(this).css({ color:"white",font-size:20});`

```html
<head>
    <script src="jquery.min.js"></script>
    <style>
        div {
            width: 200px;
            height: 200px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div></div>
    <script>
        // 操作样式之css方法
        $(function() {
            console.log($("div").css("width"));
            // $("div").css("width", "300px");  // 属性名一定要加引号
            // $("div").css("width", 300);  // 值是数字可以不用跟单位和引号
            $("div").css({
                width: 400,
                height: 400,
                backgroundColor: "red"
                    // 如果是复合属性则必须采取驼峰命名法，如果值不是数字，则需要加引号
            })
        })
    </script>
</body>
```

#### 设置类样式方法
- 作用等同于以前的 classList，可以操作类样式， 注意操作类里面的参数不要加点。

1、添加类
-  `$("div").addClass("current");`

2、移除类
- `$("div").removeClass("current");`

3、切换类
- `$("div").toggleClass("current");`

```html
<head>
    <style>
        div {
            width: 150px;
            height: 150px;
            background-color: pink;
            margin: 100px auto;
            transition: all 0.5s;
        }
        
        .current {
            background-color: red;
            transform: rotate(360deg);
        }
    </style>
    <script src="jquery.min.js"></script>
</head>

<body>
    <div class="current"></div>
    <script>
        $(function() {
            // 1. 添加类 addClass()
            // $("div").click(function() {
            //     // $(this).addClass("current");
            // });
            // 2. 删除类 removeClass()
            // $("div").click(function() {
            //     $(this).removeClass("current");
            // });
            // 3. 切换类 toggleClass()
            $("div").click(function() {
                $(this).toggleClass("current");
            });
        })
    </script>
</body>
```

案例：tab 栏切换  
分析：  
1、点击上部的li，当前li 添加current类，其余兄弟移除类。  
2、点击的同时，得到当前li 的索引号  
3、让下部里面相应索引号的item显示，其余的item隐藏  

```html
<head>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        li {
            list-style-type: none;
        }
        
        .tab {
            width: 978px;
            margin: 100px auto;
        }
        
        .tab_list {
            height: 39px;
            border: 1px solid #ccc;
            background-color: #f1f1f1;
        }
        
        .tab_list li {
            float: left;
            height: 39px;
            line-height: 39px;
            padding: 0 20px;
            text-align: center;
            cursor: pointer;
        }
        
        .tab_list .current {
            background-color: #c81623;
            color: #fff;
        }
        
        .item_info {
            padding: 20px 0 0 20px;
        }
        
        .item {
            display: none;
        }
    </style>
    <script src="jquery.min.js"></script>
</head>

<body>
    <div class="tab">
        <div class="tab_list">
            <ul>
                <li class="current">商品介绍</li>
                <li>规格与包装</li>
                <li>售后保障</li>
                <li>商品评价（50000）</li>
                <li>手机社区</li>
            </ul>
        </div>
        <div class="tab_con">
            <div class="item" style="display: block;">
                商品介绍模块内容
            </div>
            <div class="item">
                规格与包装模块内容
            </div>
            <div class="item">
                售后保障模块内容
            </div>
            <div class="item">
                商品评价（50000）模块内容
            </div>
            <div class="item">
                手机社区模块内容
            </div>

        </div>
    </div>
    <script>
        $(function() {
            // 1.点击上部的li，当前li 添加current类，其余兄弟移除类
            $(".tab_list li").click(function() {
                // 链式编程操作
                $(this).addClass("current").siblings().removeClass("current");
                // 2.点击的同时，得到当前li 的索引号
                var index = $(this).index();
                console.log(index);
                // 3.让下部里面相应索引号的item显示，其余的item隐藏
                $(".tab_con .item").eq(index).show().siblings().hide();
            });
        })
    </script>
</body>
```

#### 类操作与className区别
- 原生 JS 中 className 会覆盖元素原先里面的类名。
- jQuery 里面类操作只是对指定类进行操作，不影响原先的类名。

```html
<head>
    <style>
        .one {
            width: 200px;
            height: 200px;
            background-color: pink;
            transition: all .3s;
        }
        
        .two {
            transform: rotate(720deg);
        }
    </style>
    <script src="jquery.min.js"></script>
</head>

<body>
    <div class="one two"></div>
    <script>
        // var one = document.querySelector(".one");
        // one.className = "two";
        // $(".one").addClass("two");  这个addClass相当于追加类名 不影响以前的类名
        $(".one").removeClass("two"); // 清除 two类名，不影响 one类名
    </script>
</body>
```

### 效果
jQuery 给我们封装了很多动画效果，最为常见的如下：  
1. 显示隐藏： `show()` `hide()` `toggle()`
2. 滑动：`slideDown()` `slideUp()` `slideToggle()`
3. 淡入淡出：`fadeIn()` `fadeOut()` `fadeToggle()` `fadeTo()`
4. 自定义动画：`animate()`

#### 显示隐藏切换效果
1、显示语法：`show([speed,[easing],[fn]])`   
2、隐藏语法：`toggle([speed,[easing],[fn]])`  
3、显示与隐藏切换语法：`toggle([speed,[easing],[fn]])`  

参数：  
（1）参数都可以省略， 无动画直接显示。  
（2）speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。  
（3）easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。  
（4）fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。 建议：平时一般不带参数，直接显示隐藏即可。
  
```html
<head>
    <style>
        div {
            width: 150px;
            height: 300px;
            background-color: pink;
        }
    </style>
    <script src="jquery.min.js"></script>
</head>

<body>
    <button>显示</button>
    <button>隐藏</button>
    <button>切换</button>
    <div></div>
    <script>
        $(function() {
            $("button").eq(0).click(function() {
                $("div").show(1000, function() {
                    alert(1);
                });
            })
            $("button").eq(1).click(function() {
                $("div").hide(1000, function() {
                    alert(1);
                });
            })
            $("button").eq(2).click(function() {
                    $("div").toggle(1000);
                })
                // 一般情况下，我们都不加参数直接 显示隐藏 就可以了
        });
    </script>
</body>
```

#### 滑动效果
1、下滑效果语法规范：`slideDown([speed,[easing],[fn]])`  
2、上滑效果语法规范: `slideUp([speed,[easing],[fn]])`  
3、上滑下滑切换效果语法规范: `slideToggle([speed,[easing],[fn]])`  

参数：  
（1）参数都可以省略。  
（2）speed:三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。  
（3）easing:(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。  
（4）fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。  

```html
<head>
    <style>
        div {
            width: 150px;
            height: 300px;
            background-color: pink;
            display: none;
        }
    </style>
    <script src="jquery.min.js"></script>
</head>

<body>
    <button>下拉滑动</button>
    <button>上拉滑动</button>
    <button>切换滑动</button>
    <div></div>
    <script>
        $(function() {
            $("button").eq(0).click(function() {
                // 下滑动 slideDown()
                $("div").slideDown();
            })

            $("button").eq(1).click(function() {
                // 上滑动 slideUp()
                $("div").slideUp(500);
            })

            $("button").eq(2).click(function() {
                // 滑动切换 slideToggle()
                $("div").slideToggle(500);
            });

        });
    </script>
</body>
```

#### 事件切换
- `hover([over,]out)`

参数：   
（1）over:鼠标移到元素上要触发的函数（相当于mouseenter）  
（2）out:鼠标移出元素要触发的函数（相当于mouseleave）  
（3）如果只写一个函数，则鼠标经过和离开都会触发它  

案例：简洁版滑动下拉菜单
```html
<head>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        li {
            list-style-type: none;
        }
        
        a {
            text-decoration: none;
            font-size: 14px;
        }
        
        .nav {
            margin: 100px;
        }
        
        .nav>li {
            position: relative;
            float: left;
            width: 80px;
            height: 41px;
            text-align: center;
        }
        
        .nav li a {
            display: block;
            width: 100%;
            height: 100%;
            line-height: 41px;
            color: #333;
        }
        
        .nav>li>a:hover {
            background-color: #eee;
        }
        
        .nav ul {
            display: none;
            position: absolute;
            top: 41px;
            left: 0;
            width: 100%;
            border-left: 1px solid #FECC5B;
            border-right: 1px solid #FECC5B;
        }
        
        .nav ul li {
            border-bottom: 1px solid #FECC5B;
        }
        
        .nav ul li a:hover {
            background-color: #FFF5DA;
        }
    </style>
    <script src="jquery.min.js"></script>
</head>

<body>
    <ul class="nav">
        <li>
            <a href="#">微博</a>
            <ul>
                <li>
                    <a href="">私信</a>
                </li>
                <li>
                    <a href="">评论</a>
                </li>
                <li>
                    <a href="">@我</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul>
                <li>
                    <a href="">私信</a>
                </li>
                <li>
                    <a href="">评论</a>
                </li>
                <li>
                    <a href="">@我</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul>
                <li>
                    <a href="">私信</a>
                </li>
                <li>
                    <a href="">评论</a>
                </li>
                <li>
                    <a href="">@我</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul>
                <li>
                    <a href="">私信</a>
                </li>
                <li>
                    <a href="">评论</a>
                </li>
                <li>
                    <a href="">@我</a>
                </li>
            </ul>
        </li>
    </ul>
    <script>
        $(function() {
            // 鼠标经过
            // $(".nav>li").mouseover(function() {
            //     // $(this) jQuery 当前元素  this不要加引号
            //     // show() 显示元素  hide() 隐藏元素
            //     $(this).children("ul").slideDown(200);
            // });
            // // 鼠标离开
            // $(".nav>li").mouseout(function() {
            //     $(this).children("ul").slideUp(200);
            // });
            // 1. 事件切换 hover 就是鼠标经过和离开的复合写法
            // $(".nav>li").hover(function() {
            //     $(this).children("ul").slideDown(200);
            // }, function() {
            //     $(this).children("ul").slideUp(200);
            // });
            // 2. 事件切换 hover  如果只写一个函数，那么鼠标经过和鼠标离开都会触发这个函数
            $(".nav>li").hover(function() {
                $(this).children("ul").slideToggle();
            });
        })
    </script>
</body>
```

#### 动画队列及其停止排队方法  
1、动画或效果队列  
- 动画或者效果一旦触发就会执行，如果多次触发，就造成多个动画或者效果排队执行。  

2、停止排队
- `stop()`  
参数：  
(1）stop() 方法用于停止动画或效果。  
(2)  注意： stop() 写到动画或者效果的前面， 相当于停止结束上一次的动画。

```js
$(function() {

            // 事件切换 hover  如果只写一个函数，那么鼠标经过和鼠标离开都会触发这个函数
            $(".nav>li").hover(function() {
                // stop 方法必须写到动画的前面
                $(this).children("ul").stop().slideToggle();
            });
        })
```

#### 淡入淡出效果
1、淡入效果语法规范：`fadeIn([speed,[easing],[fn]])`  
2、淡出效果语法规范：`fadeOut([speed,[easing],[fn]])`  
3、淡入淡出切换效果语法规范：`fadeToggle([speed,[easing],[fn]])`  
4、渐进方式调整到指定的不透明度：`fadeTo([[speed],opacity,[easing],[fn]])`
- opacity 透明度必须写，取值 0~1 之间。  
- speed：`必须写`  

参数：  
（1）参数都可以省略。  
（2）speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。  
（3）easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。  
（4）fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。  

```html
<head>
    <style>
        div {
            width: 150px;
            height: 300px;
            background-color: pink;
            display: none;
        }
    </style>
    <script src="jquery.min.js"></script>
</head>

<body>
    <button>淡入效果</button>
    <button>淡出效果</button>
    <button>淡入淡出切换</button>
    <button>修改透明度</button>
    <div></div>
    <script>
        $(function() {
            $("button").eq(0).click(function() {
                // 淡入 fadeIn()
                $("div").fadeIn(1000);
            })
            $("button").eq(1).click(function() {
                // 淡出 fadeOut()
                $("div").fadeOut(1000);

            })
            $("button").eq(2).click(function() {
                // 淡入淡出切换 fadeToggle()
                $("div").fadeToggle(1000);

            });
            $("button").eq(3).click(function() {
                //  修改透明度 fadeTo() 这个速度和透明度要必须写
                $("div").fadeTo(1000, 0.5);

            });

        });
    </script>
</body>
```

案例：突出显示
```html
<head lang="en">
    <title></title>
    <style type="text/css">
        * {
            margin: 0;
            padding: 0;
        }
        
        ul {
            list-style: none;
        }
        
        body {
            background: #000;
        }
        
        .wrap {
            margin: 100px auto 0;
            width: 630px;
            height: 394px;
            padding: 10px 0 0 10px;
            background: #000;
            overflow: hidden;
            border: 1px solid #fff;
        }
        
        .wrap li {
            float: left;
            margin: 0 10px 10px 0;
        }
        
        .wrap img {
            display: block;
            border: 0;
        }
    </style>
    <script src="jquery.min.js"></script>
    <script>
        $(function() {
            //鼠标进入的时候,其他的li标签透明度：0.5
            $(".wrap li").hover(function() {
                $(this).siblings().stop().fadeTo(400, 0.5);
            }, function() {
                // 鼠标离开，其他li 透明度改为 1
                $(this).siblings().stop().fadeTo(400, 1);
            })

        });
    </script>
</head>

<body>
    <div class="wrap">
        <ul>
            <li>
                <a href="#"><img src="images/01.jpg" alt="" /></a>
            </li>
            <li>
                <a href="#"><img src="images/02.jpg" alt="" /></a>
            </li>
            <li>
                <a href="#"><img src="images/03.jpg" alt="" /></a>
            </li>
            <li>
                <a href="#"><img src="images/04.jpg" alt="" /></a>
            </li>
            <li>
                <a href="#"><img src="images/05.jpg" alt="" /></a>
            </li>
            <li>
                <a href="#"><img src="images/06.jpg" alt="" /></a>
            </li>
        </ul>
    </div>
</body>
```

#### 自定义动画 animate
- 语法：`animate(params,[speed],[easing],[fn])`
- 参数：  
（1）params: 想要更改的样式属性，以对象形式传递，`必须写`。 属性名可以不用带引号， 如果是复合属性则需要采取驼峰命名法 borderLeft。其余参数都可以省略。  
（2）speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。  
（3）easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。  
（4）fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。  

```html
<head>
    <script src="jquery.min.js"></script>
    <style>
        div {
            position: absolute;
            width: 200px;
            height: 200px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <button>动起来</button>
    <div></div>
    <script>
        $(function() {
            $("button").click(function() {
                $("div").animate({
                    left: 500,
                    top: 300,
                    opacity: .4,
                    width: 500
                }, 500);
            })
        })
    </script>
</body>
```

案例：王者荣耀手风琴效果  
分析：      
1、鼠标经过某个小li 有两步操作：  
2、当前小li 宽度变为 224px， 同时里面的小图片淡出，大图片淡入  
3、其余兄弟小li宽度变为69px， 小图片淡入， 大图片淡出  

```html
<head>
    <title>手风琴案例</title>

    <style type="text/css">
        * {
            margin: 0;
            padding: 0;
        }
        
        img {
            display: block;
        }
        
        ul {
            list-style: none;
        }
        
        .king {
            width: 852px;
            margin: 100px auto;
            background: url(images/bg.png) no-repeat;
            overflow: hidden;
            padding: 10px;
        }
        
        .king ul {
            overflow: hidden;
        }
        
        .king li {
            position: relative;
            float: left;
            width: 69px;
            height: 69px;
            margin-right: 10px;
        }
        
        .king li.current {
            width: 224px;
        }
        
        .king li.current .big {
            display: block;
        }
        
        .king li.current .small {
            display: none;
        }
        
        .big {
            width: 224px;
            display: none;
        }
        
        .small {
            position: absolute;
            top: 0;
            left: 0;
            width: 69px;
            height: 69px;
            border-radius: 5px;
        }
    </style>

</head>

<body>
    <script src="js/jquery.min.js"></script>
    <script type="text/javascript">
        $(function() {
            // 鼠标经过某个小li 有两步操作：
            $(".king li").mouseenter(function() {
                // 1.当前小li 宽度变为 224px， 同时里面的小图片淡出，大图片淡入
                $(this).stop().animate({
                    width: 224
                }).find(".small").stop().fadeOut().siblings(".big").stop().fadeIn();
                // 2.其余兄弟小li宽度变为69px， 小图片淡入， 大图片淡出
                $(this).siblings("li").stop().animate({
                    width: 69
                }).find(".small").stop().fadeIn().siblings(".big").stop().fadeOut();
            })
        });
    </script>

    <div class="king">
        <ul>
            <li class="current">
                <a href="#">
                    <img src="images/m1.jpg" alt="" class="small">
                    <img src="images/m.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="images/l1.jpg" alt="" class="small">
                    <img src="images/l.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="images/c1.jpg" alt="" class="small">
                    <img src="images/c.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="images/w1.jpg" alt="" class="small">
                    <img src="images/w.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="images/z1.jpg" alt="" class="small">
                    <img src="images/z.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="images/h1.jpg" alt="" class="small">
                    <img src="images/h.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="images/t1.jpg" alt="" class="small">
                    <img src="images/t.png" alt="" class="big">
                </a>
            </li>
        </ul>
    </div>
</body>
```

### 属性操作
#### 设置或获取元素固有属性值 prop()  
所谓元素固有属性就是元素本身自带的属性，比如` <a>` 元素里面的 href ，比如 `<input> `元素里面的 type。 

- 获取属性语法：`prop("属性")`
- 设置属性语法：`prop("属性", "属性值")`

#### 设置或获取元素自定义属性值 attr()   
用户自己给元素添加的属性，我们称为自定义属性。 比如给 `<div>` 添加 index =“1”。   
改方法也可以获取 H5 自定义属性

- 获取属性语法：`attr("属性")  ` // 类似原生 getAttribute()
- 设置属性语法：`attr("属性", "属性值") ` // 类似原生 setAttribute()

#### 数据缓存 data()  
data() 方法可以在指定的元素上存取数据，并不会修改 DOM 元素结构。一旦页面刷新，之前存放的数据都将被移除。   
同时，还可以读取 HTML5 自定义属性  data-index ，得到的是数字型

- 附加数据语法：`data("name","value") ` // 向被选元素附加数据  
- 获取数据语法：`date("name") ` //   向被选元素获取数据  

```html
<head>
    <script src="jquery.min.js"></script>
</head>

<body>
    <a href="http://www.itcast.cn" title="都挺好">都挺好</a>
    <input type="checkbox" name="" id="" checked>
    <div index="1" data-index="2">我是div</div>
    <span>123</span>
    <script>
        $(function() {
            //1. element.prop("属性名") 获取元素固有的属性值
            console.log($("a").prop("href"));
            $("a").prop("title", "我们都挺好");
            $("input").change(function() {
                console.log($(this).prop("checked"));
            });
            // console.log($("div").prop("index"));

            // 2. 元素的自定义属性 我们通过 attr()
            console.log($("div").attr("index")); // 1
            $("div").attr("index", 4);
            console.log($("div").attr("data-index")); // 2

            // 3. 数据缓存 data() 这个里面的数据是存放在元素的内存里面
            $("span").data("uname", "andy");
            console.log($("span").data("uname")); // andy
            // 这个方法获取data-index h5自定义属性 第一个 不用写data-  而且返回的是数字型
            console.log($("div").data("index")); // 2
        })
    </script>
</body>
```

案例：购物车案例模块-全选    《代码参见文件》  
思路：  
1、里面3个小的复选框按钮（j-checkbox）选中状态（checked）跟着全选按钮（checkall）走。  
2、因为checked 是复选框的固有属性，此时我们需要利用prop()方法获取和设置该属性。  
3、把全选按钮状态赋值给3小复选框就可以了。   
4、当我们每次点击小的复选框按钮，就来判断：    
5、如果小复选框被选中的个数等于3 就应该把全选按钮选上，否则全选按钮不选。  
6、:checked 选择器      :checked 查找被选中的表单元素。  


### 内容文本属性值  
主要针对 元素的内容 还有 表单的值 操作。

1、普通元素内容 html() ，相当于原生inner HTML  
- `html()  `   // 获取元素的内容  
- `html("内容") `  // 设置元素的内容

2、普通元素文本内容 text() ，相当与原生 innerText
- `text()  `  // 获取元素的文本内容
- `text("文本内容") ` // 设置元素的文本内容

3、表单的值 val()，相当于原生value
- `val()  `   // 获取表单的值
- `val("内容") `  // 设置表单的值


案例：购物车案例模块-增减商品数量  《代码参见文件》    
核心思路：  
- 首先声明一个变量，当我们点击+号（increment），就让这个值++，然后赋值给文本框。    
- 注意1： 只能增加本商品的数量， 就是当前+号的兄弟文本框（itxt）的值。   
- 修改表单的值是val() 方法  
- 注意2： 这个变量初始值应该是这个文本框的值，在这个值的基础上++。要获取表单的值  
- 减号（decrement）思路同理，但是如果文本框的值是1，就不能再减了。  


案例：购物车案例模块-修改商品小计  《代码参见文件》   
核心思路：    
- 每次点击+号或者-号，根据文本框的值 乘以 当前商品的价格  就是 商品的小计  
- 注意1： 只能增加本商品的小计， 就是当前商品的小计模块（p-sum）    
- 修改普通元素的内容是text() 方法  
- 注意2： 当前商品的价格，要把￥符号去掉再相乘 截取字符串 substr(1)  
- parents(‘选择器’) 可以返回指定祖先元素    
- 最后计算的结果如果想要保留2位小数 通过 toFixed(2)  方法  
- 用户也可以直接修改表单里面的值，同样要计算小计。 用表单change事件  
- 用最新的表单内的值 乘以 单价即可  但是还是当前商品小计  

```html
<head>
    <script src="jquery.min.js"></script>
</head>

<body>
    <div>
        <span>我是内容</span>
    </div>
    <input type="text" value="请输入内容">
    <script>
        // 1. 获取设置元素内容 html()
        console.log($("div").html());
        // $("div").html("123");
        // 2. 获取设置元素文本内容 text()
        console.log($("div").text());
        $("div").text("123");

        // 3. 获取设置表单值 val()
        console.log($("input").val());
        $("input").val("123");
    </script>
</body>
```

### 元素操作  
主要是遍历、创建、添加、删除元素操作。

#### 遍历元素  
jQuery 隐式迭代是对同一类元素做了同样的操作。 如果想要给同一类元素做不同操作，就需要用到遍历。

1、语法一：`$("div").each(function (index, domEle) { xxx; })  `       
- each() 方法遍历匹配的每一个元素。主要用DOM处理。 each 每一个
- 里面的回调函数有2个参数：  index 是每个元素的索引号;  demEle 是每个DOM元素对象，不是jquery对象
- 所以要想使用jquery方法，需要给这个dom元素转换为jquery对象  $(domEle)

2、语法二：`$.each(object，function (index, element) { xxx; })`    
- $.each()方法可用于遍历任何对象。主要用于数据处理，比如数组，对象
- 里面的函数有2个参数：  index 是每个元素的索引号;  element  遍历内容

```html
<head>
    <style>

    </style>
    <script src="jquery.min.js"></script>
</head>

<body>
    <div>1</div>
    <div>2</div>
    <div>3</div>
    <script>
        $(function() {
            // $("div").css("color", "red");
            // 如果针对于同一类元素做不同操作，需要用到遍历元素（类似for，但是比for强大）
            var sum = 0;
            
            // 1. each() 方法遍历元素 
            var arr = ["red", "green", "blue"];
            $("div").each(function(i, domEle) {
                // 回调函数第一个参数一定是索引号  可以自己指定索引号号名称
                // console.log(index);
                // console.log(i);
                // 回调函数第二个参数一定是 dom元素对象 也是自己命名
                // console.log(domEle);
                // domEle.css("color"); dom对象没有css方法
                $(domEle).css("color", arr[i]);
                sum += parseInt($(domEle).text());
            })
            console.log(sum);

            // 2. $.each() 方法遍历元素 主要用于遍历数据，处理数据
            // $.each($("div"), function(i, ele) {
            //     console.log(i);
            //     console.log(ele);
            // });
            // $.each(arr, function(i, ele) {
            //     console.log(i);
            //     console.log(ele);
            // })

            $.each({
                name: "andy",
                age: 18
            }, function(i, ele) {
                console.log(i); // 输出的是 name age 属性名
                console.log(ele); // 输出的是 andy  18 属性值
            })
        })
    </script>
</body>
```

案例：购物车案例模块-计算总计和总额  《代码参见文件》  
核心思路：
- 把所有文本框里面的值相加就是总计数量。总额同理
- 文本框里面的值不相同，如果想要相加需要用到each遍历。声明一个变量，相加即可
- 点击+号-号，会改变总计和总额，如果用户修改了文本框里面的值同样会改变总计和总额
- 因此可以封装一个函数求总计和总额的， 以上2个操作调用这个函数即可。
- 注意1： 总计是文本框里面的值相加用 val()     总额是普通元素的内容用text()  
- 要注意普通元素里面的内容要去掉￥并且转换为数字型才能相加

#### 创建元素
- 语法：`$("<li></li>");`   
- 动态的创建了一个 li  

#### 添加元素

一、内部添加  

内部添加元素，生成之后，它们是父子关系。

1、`element.append("内容")  `  
- 把内容放入匹配元素内部最后面，类似原生 appendChild。

2、`element.prepend("内容")  `
- 把内容放入匹配元素内部最前面。

二、外部添加  

外部添加元素，生成之后，他们是兄弟关系。

1、`element.after("内容") ` 
- 把内容放入目标元素后面  

2、`element.before("内容")` 
- 把内容放入目标元素前面

#### 删除元素

1、`element.remove() ` 
- 删除匹配的元素（本身），即删除元素本身。

2、`element.empty()`
- 删除匹配的元素集合中所有的子节点

3、`element.html("") `
- 清空匹配的元素内容
- empt() 和  html("") 作用等价，都可以删除元素里面的内容，只不过 html 还可以设置内容。

```html
<head>
    <script src="jquery.min.js"></script>
</head>

<body>
    <ul>
        <li>原先的li</li>
    </ul>
    <div class="test">我是原先的div</div>
    <script>
        $(function() {
            // 1. 创建元素
            var li = $("<li>我是后来创建的li</li>");

            // 2. 添加元素
            // (1) 内部添加
            // $("ul").append(li);  内部添加并且放到内容的最后面 
            $("ul").prepend(li); // 内部添加并且放到内容的最前面

            // (2) 外部添加
            var div = $("<div>我是后妈生的</div>");
            // $(".test").after(div);
            $(".test").before(div);

            // 3. 删除元素
            // $("ul").remove(); 可以删除匹配的元素 自杀
            // $("ul").empty(); // 可以删除匹配的元素里面的子节点 孩子
            $("ul").html(""); // 可以删除匹配的元素里面的子节点 孩子
        })
    </script>
</body>
```

案例：购物车案例模块-删除商品模块  《代码参见文件》  
核心思路：  
1、把商品remove() 删除元素即可  
2、有三个地方需要删除：商品后面的删除按钮、删除选中的商品、清理购物车  
3、商品后面的删除按钮： 一定是删除当前的商品，所以从 $(this) 出发  
4、删除选中的商品： 先判断小的复选框按钮是否选中状态，如果是选中，则删除对应的商品  
5、清理购物车： 则是把所有的商品全部删掉  

案例：购物车案例模块-选中商品添加背景  《代码参见文件》  
核心思路：  
1、选中的商品添加背景，不选中移除背景即可  
2、全选按钮点击：如果全选是选中的，则所有的商品添加背景，否则移除背景  
3、小的复选框点击： 如果是选中状态，则当前商品添加背景，否则移除背景  
4、这个背景，可以通过类名修改，添加类和删除类  


### 尺寸、位置操作
#### 尺寸操作

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221016/image.1z3s9j1vgd34.webp)

- 以上参数为空，则是获取相应值，返回的是数字型。
- 如果参数为数字，则是修改相应值。
- 参数可以不必写单位。

```html
<head>
    <style>
        div {
            width: 200px;
            height: 200px;
            background-color: pink;
            padding: 10px;
            border: 15px solid red;
            margin: 20px;
        }
    </style>
    <script src="jquery.min.js"></script>
</head>

<body>
    <div></div>
    <script>
        $(function() {
            // 1. width() / height() 获取设置元素 width和height大小 
            console.log($("div").width());
            // $("div").width(300);

            // 2. innerWidth() / innerHeight()  获取设置元素 width和height + padding 大小 
            console.log($("div").innerWidth());

            // 3. outerWidth()  / outerHeight()  获取设置元素 width和height + padding + border 大小 
            console.log($("div").outerWidth());

            // 4. outerWidth(true) / outerHeight(true) 获取设置 width和height + padding + border + margin
            console.log($("div").outerWidth(true));
        })
    </script>
</body>
```

#### 位置操作  
位置主要有三个： `offset()、position()、scrollTop()/scrollLeft()`

1、`offset()`设置或获取元素偏移

- offset() 方法设置或返回被选元素相对于`文档`的偏移坐标，跟父级没有关系。
- 该方法有2个属性 left、top
- offset().top  用于获取距离文档顶部的距离，offset().left 用于获取距离文档左侧的距离。
- 可以设置元素的偏移：offset({ top: 10, left: 30 });

2、`position() `获取元素偏移

- position() 方法用于返回被选元素相对于`带有定位的父级`偏移坐标，如果父级都没有定位，则以文档为准。
- 该方法有2个属性 left、top
- position().top 用于获取距离定位父级顶部的距离，position().left 用于获取距离定位父级左侧的距离。
- 该方法只能获取。

3. scrollTop()/scrollLeft() 设置或获取元素被卷去的头部和左侧

- scrollTop() 方法设置或返回被选元素被卷去的头部。
- 不跟参数是获取，参数为不带单位的数字则是设置被卷去的头部。


```html
<head>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        .father {
            width: 400px;
            height: 400px;
            background-color: pink;
            margin: 100px;
            overflow: hidden;
            position: relative;
        }
        
        .son {
            width: 150px;
            height: 150px;
            background-color: purple;
            position: absolute;
            left: 10px;
            top: 10px;
        }
    </style>
    <script src="jquery.min.js"></script>
</head>

<body>
    <div class="father">
        <div class="son"></div>
    </div>
    <script>
        $(function() {
            // 1. 获取设置距离文档的位置（偏移） offset
            console.log($(".son").offset());
            console.log($(".son").offset().top);
            // $(".son").offset({
            //     top: 200,
            //     left: 200
            // });
            // 2. 获取距离带有定位父级位置（偏移） position   如果没有带有定位的父级，则以文档为准
            // 这个方法只能获取不能设置偏移
            console.log($(".son").position());
            // $(".son").position({
            //     top: 200,
            //     left: 200
            // });
        })
    </script>
</body>
```

```html
<head>
    <style>
        body {
            height: 2000px;
        }
        
        .back {
            position: fixed;
            width: 50px;
            height: 50px;
            background-color: pink;
            right: 30px;
            bottom: 100px;
            display: none;
        }
        
        .container {
            width: 900px;
            height: 500px;
            background-color: skyblue;
            margin: 400px auto;
        }
    </style>
    <script src="jquery.min.js"></script>
</head>

<body>
    <div class="back">返回顶部</div>
    <div class="container">
    </div>
    <script>
        $(function() {
            $(document).scrollTop(100);
            // 被卷去的头部 scrollTop()  / 被卷去的左侧 scrollLeft()
            // 页面滚动事件
            var boxTop = $(".container").offset().top;
            $(window).scroll(function() {
                // console.log(11);
                console.log($(document).scrollTop());
                if ($(document).scrollTop() >= boxTop) {
                    $(".back").fadeIn();
                } else {
                    $(".back").fadeOut();
                }
            });
            // 返回顶部
            $(".back").click(function() {
                // $(document).scrollTop(0);
                $("body, html").stop().animate({
                    scrollTop: 0
                });
                // $(document).stop().animate({
                //     scrollTop: 0
                // }); 不能是文档而是 html和body元素做动画
            })
        })
    </script>
</body>
```






案例：带有动画的返回顶部  《代码参见文件》  
核心原理：   
- 使用animate动画返回顶部。
- animate动画函数里面有个scrollTop 属性，可以设置位置
- 但是是元素做动画，因此 $(“body,html”).animate({scrollTop: 0})

案例： 品优购电梯导航   《代码参见文件》  
当我们滚动到 今日推荐 模块，就让电梯导航显示出来。点击电梯导航页面可以滚动到相应内容区域    
- 核心算法：  
因为电梯导航模块和内容区模块一一对应的
当我们点击电梯导航某个小模块，就可以拿到当前小模块的索引号
就可以把animate要移动的距离求出来：当前索引号内容区模块它的offset().top
然后执行动画即可

- 当我们点击电梯导航某个小li， 当前小li 添加current类，兄弟移除类名
- 当我们页面滚动到内容区域某个模块， 左侧电梯导航，相对应的小li模块，也会添加current类， 兄弟移除current类。
- 触发的事件是页面滚动，因此这个功能要写到页面滚动事件里面。
- 需要用到each，遍历内容区域大模块。 each里面能拿到内容区域每一个模块元素和索引号
- 判断的条件：  被卷去的头部 大于等于 内容区域里面每个模块的offset().top
- 就利用这个索引号找到相应的电梯导航小li添加类。


## jQuery 事件
### 事件注册  
1、单个事件注册  

语法： 
- `element.事件(function(){}) `       
- `$(“div”).click(function(){  事件处理程序 }) `      
 
2、其他事件和原生基本一致    

比如：`mouseover、mouseout、blur、focus、change、keydown、keyup、resize、scroll` 等

```html
<head>
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: pink;
        }
        
        .current {
            background-color: purple;
        }
    </style>
    <script src="jquery.min.js"></script>
</head>

<body>
    <div></div>
    <ul>
        <li>我们都是好孩子</li>
        <li>我们都是好孩子</li>
        <li>我们都是好孩子</li>
        <li>我们都是好孩子</li>
        <li>我们都是好孩子</li>
    </ul>
    <ol>

    </ol>
    <script>
        $(function() {
            // 1. 单个事件注册
            // $("div").click(function() {
            //     $(this).css("background", "purple");
            // });

            // $("div").mouseenter(function() {
            //     $(this).css("background", "skyblue");
            // });
        })
    </script>
</body>
```

### 事件处理
#### on() 绑定事件

1、on() 方法，在匹配元素上绑定一个或多个事件的事件处理函数  
- 语法：`element.on(events,[selector],fn) `      
- 参数：  
    - events:一个或多个用空格分隔的事件类型，如"click"或"keydown"  
    - selector: 元素的子元素选择器 。  
    - fn:回调函数 即绑定在元素身上的侦听函数。   

2、on() 方法的优势  
- 可以绑定多个事件，多个处理事件处理程序。 
- 可以事件委派操作 。事件委派的定义就是，把原来加给子元素身上的事件绑定在父元素身上，就是把事件委派给父元素。
- 动态创建的元素，click() 没有办法绑定事件， on() 可以给动态生成的元素绑定事件 

```html
<head>
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: pink;
        }
        
        .current {
            background-color: purple;
        }
    </style>
    <script src="jquery.min.js"></script>
</head>

<body>
    <div></div>
    <ul>
        <li>我们都是好孩子</li>
        <li>我们都是好孩子</li>
        <li>我们都是好孩子</li>
        <li>我们都是好孩子</li>
        <li>我们都是好孩子</li>
    </ul>
    <ol>

    </ol>
    <script>
        $(function() {
            // 2. 事件处理on

            // (1) on可以绑定1个或者多个事件处理程序
            // $("div").on({
            //     mouseenter: function() {
            //         $(this).css("background", "skyblue");
            //     },
            //     click: function() {
            //         $(this).css("background", "purple");
            //     },
            //     mouseleave: function() {
            //         $(this).css("background", "blue");
            //     }
            // });
            // 如果事件处理程序相同 可这样写 
            $("div").on("mouseenter mouseleave", function() {
                $(this).toggleClass("current");
            });

            // (2) on可以实现事件委托（委派）
            // $("ul li").click();
            $("ul").on("click", "li", function() {
                alert(11);
            });
            // click 是绑定在ul 身上的，但是 触发的对象是 ul 里面的小li
            // 在此之前有bind(), live() delegate()等方法来处理事件绑定或者事件委派，最新版本的请用on替代他们。

            // (3) on可以给未来动态创建的元素绑定事件
            // $("ol li").click(function() {
            //     alert(11);
            // })
            $("ol").on("click", "li", function() {
                alert(11);
            })
            var li = $("<li>我是后来创建的</li>");
            $("ol").append(li);
        })
    </script>
</body>
```

案例：微博发布效果
```html
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        * {
            margin: 0;
            padding: 0
        }
        
        ul {
            list-style: none
        }
        
        .box {
            width: 600px;
            margin: 100px auto;
            border: 1px solid #000;
            padding: 20px;
        }
        
        textarea {
            width: 450px;
            height: 160px;
            outline: none;
            resize: none;
        }
        
        ul {
            width: 450px;
            padding-left: 80px;
        }
        
        ul li {
            line-height: 25px;
            border-bottom: 1px dashed #cccccc;
            display: none;
        }
        
        input {
            float: right;
        }
        
        ul li a {
            float: right;
        }
    </style>
    <script src="jquery.min.js"></script>
    <script>
        $(function() {
            // 1.点击发布按钮， 动态创建一个小li，放入文本框的内容和删除按钮， 并且添加到ul 中
            $(".btn").on("click", function() {
                var li = $("<li></li>");
                li.html($(".txt").val() + "<a href='javascript:;'> 删除</a>");
                $("ul").prepend(li);
                li.slideDown();
                $(".txt").val("");
            })

            // 2.点击的删除按钮，可以删除当前的微博留言li
            // $("ul a").click(function() {  // 此时的click不能给动态创建的a添加事件
            //     alert(11);
            // })
            // on可以给动态创建的元素绑定事件
            $("ul").on("click", "a", function() {
                $(this).parent().slideUp(function() {
                    $(this).remove();
                });
            })

        })
    </script>
</head>

<body>
    <div class="box" id="weibo">
        <span>微博发布</span>
        <textarea name="" class="txt" cols="30" rows="10"></textarea>
        <button class="btn">发布</button>
        <ul>
        </ul>
    </div>
</body>
```

#### off() 解绑事件
- off() 方法可以移除通过 on() 方法添加的事件处理程序。

```html
<head>
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: pink;
        }
    </style>
    <script src="jquery.min.js"></script>
    <script>
        $(function() {
            $("div").on({
                click: function() {
                    console.log("我点击了");
                },
                mouseover: function() {
                    console.log('我鼠标经过了');
                }
            });
            $("ul").on("click", "li", function() {
                alert(11);
            });
            // 1. 事件解绑 off 
            // $("div").off();  // 这个是解除了div身上的所有事件
            $("div").off("click"); // 这个是解除了div身上的点击事件
            $("ul").off("click", "li"); // 解绑事件委托
            
            // 2. one() 但是它只能触发事件一次
            $("p").one("click", function() {
                alert(11);
            })
        })
    </script>
</head>

<body>
    <div></div>
    <ul>
        <li>我们都是好孩子</li>
        <li>我们都是好孩子</li>
        <li>我们都是好孩子</li>
    </ul>
    <p>我是屁</p>
</body>
```

#### 自动触发事件 trigger()     
有些事件希望自动触发, 比如轮播图自动播放功能跟点击右侧按钮一致。可以利用定时器自动触发右侧按钮点击事件，不必鼠标点击触发。

```html
<head>
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: pink;
        }
    </style>
    <script src="jquery.min.js"></script>
    <script>
        $(function() {
            $("div").on("click", function() {
                alert(11);
            });

            // 自动触发事件
            // 1. 元素.事件()
            // $("div").click();会触发元素的默认行为
            // $("input").click("focus");

            // 2. 元素.trigger("事件")
            // $("div").trigger("click"); // 会触发元素的默认行为
            $("input").trigger("focus");

            // 3. 元素.triggerHandler("事件") 就是不会触发元素的默认行为
            $("div").triggerHandler("click");
            $("input").on("focus", function() {
                $(this).val("你好吗");
            });
            $("input").triggerHandler("focus");

        });
    </script>
</head>

<body>
    <div></div>
    <input type="text">
</body>
```

### 事件对象  
事件被触发，就会有事件对象的产生。
- `element.on(events,[selector],function(event) {}) `
- 阻止默认行为：event.preventDefault()   或者 return  false 
- 阻止冒泡： event.stopPropagation()      

```html
<head>
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: pink;
        }
    </style>
    <script src="jquery.min.js"></script>
    <script>
        $(function() {
            $(document).on("click", function() {
                console.log("点击了document");

            })
            $("div").on("click", function(event) {
                // console.log(event);
                console.log("点击了div");
                event.stopPropagation(); // 阻止冒泡
            })
        })
    </script>
</head>

<body>
    <div></div>
</body>
```

## jQuery 其他方法
### 拷贝对象  
如果想要把某个对象拷贝（合并） 给另外一个对象使用，此时可以使用 $.extend() 方法

一、语法：`$.extend([deep], target, object1, [objectN]) `  

二、参数:
1. deep: 如果设为true 为深拷贝， 默认为false  浅拷贝 
2. target: 要拷贝的目标对象
3. object1:待拷贝到第一个对象的对象。
4. objectN:待拷贝到第N个对象的对象。
5. 浅拷贝，是把被拷贝的对象复杂数据类型中的地址拷贝给目标对象，修改目标对象`会影响`被拷贝对象。
6. 深拷贝，前面加true， 完全克隆(拷贝的对象,而不是地址)，修改目标对象`不会影响`被拷贝对象。


```html
<head>
    <script src="jquery.min.js"></script>
    <script>
        $(function() {
            // var targetObj = {};
            // var obj = {
            //     id: 1,
            //     name: "andy"
            // };
            // // $.extend(target, obj);
            // $.extend(targetObj, obj);
            // console.log(targetObj);
            // var targetObj = {
            //     id: 0
            // };
            // var obj = {
            //     id: 1,
            //     name: "andy"
            // };
            // // $.extend(target, obj);
            // $.extend(targetObj, obj);
            // console.log(targetObj); // 会覆盖targetObj 里面原来的数据
            var targetObj = {
                id: 0,
                msg: {
                    sex: '男'
                }
            };
            var obj = {
                id: 1,
                name: "andy",
                msg: {
                    age: 18
                }
            };
            // // $.extend(target, obj);
            // $.extend(targetObj, obj);
            // console.log(targetObj); // 会覆盖targetObj 里面原来的数据

            // // 1. 浅拷贝把原来对象里面的复杂数据类型地址拷贝给目标对象
            // targetObj.msg.age = 20;
            // console.log(targetObj);
            // console.log(obj);

            // 2. 深拷贝把里面的数据完全复制一份给目标对象 如果里面有不冲突的属性,会合并到一起 
            $.extend(true, targetObj, obj);
            // console.log(targetObj); // 会覆盖targetObj 里面原来的数据
            targetObj.msg.age = 20;
            console.log(targetObj); // msg :{sex: "男", age: 20}
            console.log(obj);

        })
    </script>
</head>

<body>

</body>
```

### 多库共存

一、问题概述：

- jQuery使用`$`作为标示符，随着jQuery的流行,其他 js 库也会用这`$`作为标识符， 这样一起使用会引起冲突。

二、客观需求：

- 需要一个解决方案，让jQuery 和其他的js库不存在冲突，可以同时存在，这就叫做多库共存。

三、jQuery 解决方案：

1. 把里面的 $ 符号 统一改为 jQuery。 比如 jQuery("div")
2.  jQuery 变量规定新的名称：`$.noConflict()`  ` var xx = $.noConflict();`

```html
<head>
    <script src="jquery.min.js"></script>
    <script>
        $(function() {
            function $(ele) {
                return document.querySelector(ele);
            }
            console.log($("div"));
            // 1. 如果$ 符号冲突 我们就使用 jQuery
            jQuery.each();
            // 2. 让jquery 释放对$ 控制权 让用自己决定
            var suibian = jQuery.noConflict();
            console.log(suibian("span"));
            suibian.each();
        })
    </script>
</head>

<body>
    <div></div>
    <span></span>
</body>
```

### jQuery 插件

jQuery 功能比较有限，想要更复杂的特效效果，可以借助于 jQuery 插件完成。 
注意: 这些插件也是依赖于jQuery来完成的，所以必须要先引入jQuery文件，因此也称为 jQuery 插件。

一、jQuery 插件常用的网站：
1.  jQuery 插件库  <http://www.jq22.com/>     
2.  jQuery 之家   <http://www.htmleaf.com/>  

二、jQuery 插件使用步骤：
1.  引入相关文件。（jQuery 文件 和 插件文件）    
2.  复制相关html、css、js (调用插件)。

三、jQuery 插件演示：
1. 瀑布流
2. 图片懒加载（图片使用延迟加载在可提高网页下载速度。它也能帮助减轻服务器负载）  
    - 当我们页面滑动到可视区域，再显示图片。  
    - 我们使用jquery 插件库  EasyLazyload。 注意，此时的js引入文件和js调用必须写到 DOM元素（图片）最后面  
3. 全屏滚动（fullpage.js）
    - gitHub： <https://github.com/alvarotrigo/fullPage.js>
    - 中文翻译网站： <http://www.dowebok.com/demo/2014/77/>

四、bootstrap JS 插件：
- bootstrap 框架也是依赖于 jQuery 开发的，因此里面的 js插件使用 ，也必须引入jQuery 文件。


案例：toDoList 
- 文本框里面输入内容，按下回车，就可以生成待办事项。
- 点击待办事项复选框，就可以把当前数据添加到已完成事项里面。
- 点击已完成事项复选框，就可以把当前数据添加到待办事项里面。
- 但是本页面内容刷新页面不会丢失。

```html
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
    <title>ToDoList—最简单的待办事项列表</title>
    <link rel="stylesheet" href="css/index.css">
    <script src="js/jquery.min.js"></script>
    <script src="js/todolist.js"></script>
</head>

<body>
    <header>
        <section>
            <label for="title">ToDoList</label>
            <input type="text" id="title" name="title" placeholder="添加ToDo" required="required" autocomplete="off" />
        </section>
    </header>
    <section>
        <h2>正在进行 <span id="todocount"></span></h2>
        <ol id="todolist" class="demo-box">

        </ol>
        <h2>已经完成 <span id="donecount"></span></h2>
        <ul id="donelist">

        </ul>
    </section>
    <footer>
        Copyright &copy; 2014 todolist.cn
    </footer>

</body>
```

分析：  
1、刷新页面不会丢失数据，因此需要用到本地存储 localStorage
核心思路：   
- 不管按下回车，还是点击复选框，都是把本地存储的数据加载到页面中，这样保证刷新关闭页面不会丢失数据
- 存储的数据格式：var todolist =  [{ title : ‘xxx’, done: false}]
- 注意点1： 本地存储 localStorage 里面只能存储字符串格式 ，因此需要把对象转换为字符串 JSON.stringify(data)。
- 注意点2： 获取本地存储数据，需要把里面的字符串转换为对象格式JSON.parse() 我们才能使用里面的数据。

2、toDoList 按下回车把新数据添加到本地存储里面   
切记： 页面中的数据，都要从本地存储里面获取，这样刷新页面不会丢失数据，所以先要把数据保存到本地存储里面。  
- 利用事件对象.keyCode判断用户按下回车键（13）。
- 声明一个数组，保存数据。
- 先要读取本地存储原来的数据（声明函数 getData()），放到这个数组里面。
- 之后把最新从表单获取过来的数据，追加到数组里面。
- 最后把数组存储给本地存储 (声明函数 savaDate())


3、案例：toDoList 本地存储数据渲染加载到页面
- 因为后面也会经常渲染加载操作，所以声明一个函数 load，方便后面调用
- 先要读取本地存储数据。（数据不要忘记转换为对象格式）
- 之后遍历这个数据（$.each()），有几条数据，就生成几个小li 添加到 ol 里面。
- 每次渲染之前，先把原先里面 ol 的内容清空，然后渲染加载最新的数据。

4、案例：toDoList 删除操作

- 点击里面的a链接，不是删除的li，而是删除本地存储对应的数据。
- 核心原理：先获取本地存储数据，删除对应的数据，保存给本地存储，重新渲染列表li
- 我们可以给链接自定义属性记录当前的索引号
- 根据这个索引号删除相关的数据----数组的splice(i, 1)方法
- 存储修改后的数据，然后存储给本地存储
- 重新渲染加载数据列表
- 因为a是动态创建的，我们使用on方法绑定事件

5、案例：toDoList  正在进行和已完成选项操作

- 当我们点击了小的复选框，修改本地存储数据，再重新渲染数据列表。
- 点击之后，获取本地存储数据。
- 修改对应数据属性 done 为当前复选框的checked状态。
- 之后保存数据到本地存储
- 重新渲染加载数据列表
- load 加载函数里面，新增一个条件,如果当前数据的done为true 就是已经完成的，就把列- 表渲染加载到 ul 里面
- 如果当前数据的done 为false， 则是待办事项，就把列表渲染加载到 ol 里面


6、案例：toDoList 统计正在进行个数和已经完成个数

- 在我们load 函数里面操作
- 声明2个变量 ：todoCount 待办个数  doneCount 已完成个数   
- 当进行遍历本地存储数据的时候， 如果 数据done为 false， 则 todoCount++, 否则 doneCount++
- 最后修改相应的元素 text() 


## 扩展

## 参考

