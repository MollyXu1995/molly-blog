---
title: "Bootstrap的使用"
date: 2022-08-29T15:50:47+08:00
tags: ['Frontend Framework']
series: ['前端学习之旅']
---

## 简介
BootStrap框架，快速开发响应式网页。

BootStrap是由Twitter公司开发维护的`前端UI框架`，它提供了大量`编写好的css样式`，允许开发者结合一定`html结构和javescript`，快速编写功能完善的网页及常见交互效果。中文官网：[https://www.bootcss.com](https://www.bootcss.com)

### 下载
地址：[https://www.bootcss.com](https://www.bootcss.com)  

首页——BootStrap3文档——下载BootStrap（生产环境的）——解压bootstrap-3.4.1-dist.zip压缩包——将bootstrap-3.4.1-dist文件夹放到项目中

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220825/image.39zy7rbwpz60.webp)

- 生产环境的BootStrap，项目用的
- 源码，日后自己学习用的

### 使用
1、link引入：BootStrap提供的css代码  
2、调用类名：使用BootStrap提供的样式  
- container:响应式布局版心类

```html
<head>
    <!-- 只能引入css里的 bootstrap.min.css 或者 bootstrap.css-->
    <!-- 建议引入min.css是格式化压缩后的，体积更小 -->
    <link rel="stylesheet" href="./bootstrap-3.4.1-dist/css/bootstrap.min.css">
</head>

<body>
    <div class="container"> </div>
</body>
```
3、BootStrap手册使用  
- BootStrap预定义了大量`类`来美化页面，`掌握手册查找`方法是学习全局样式的重点
- 网站首页——BootStrap3中文文档——全局css样式——按分类导航查找目标类


## 栅格系统
1、原理  
- 使用BootStrap栅格系统，布局响应式网页  
- BootStrap3默认把网页宽度等分成12份，每个内容占12份当中的份数

![5dda3d256c4b247c3e32c4dd2b4f564](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220825/5dda3d256c4b247c3e32c4dd2b4f564.3s0xczbwuhk0.webp)

2、代码
```html
<head>
    <link rel="stylesheet" href="./bootstrap-3.4.1-dist/css/bootstrap.min.css">

    <style>
        .container div{
            height:50px;
            background-color:pink;
        }
    </style>
</head>

<body>
    <!-- 需求：大屏：一行排列4个内容；中屏：一行排列2个内容-->
    <div class="container">
        <div class="col-lg-3 col-md-6">1</div>
        <div class="col-lg-3 col-md-6">2</div>
        <div class="col-lg-3 col-md-6">3</div>
        <div class="col-lg-3 col-md-6">4</div>
    </div>
</body>
```

3、其他类名

|类名|说明|
|:--|:--|
|`.container` |默认已被指定宽度且居中，自带间距15px|
|.container-fluid |宽度均为100%|
|`.row` |定义栅格布局的行，自带间距-15px（可抵消container类的15px内边距）|
|.col| 定义栅格布局的列|

## 样式
Bootstrap 将设置全局的 CSS 样式。HTML 的基本元素均可以通过 class 设置样式并得到增强效果。还有先进的栅格系统。表格、表单、按钮、图片等
- HTML页面link标签，引入Bootstrap样式表
- 给HTML标签，添加Bootstrap的class类

## 组件
Bootstrap 自带了大量可复用的组件，包括字体图标、下拉菜单、导航、警告框、弹出框等更多功能。
- 引入Bootstrap样式表
- 复制结构，修改内容

1、字体图标
Glyphicons 字体图标使用步骤：
- 引入Bootstrap样式表
- 空标签调用类名（2个类名）
    - glyphicon
    - 图标类

## 插件
jQuery 插件为 Bootstrap 的组件赋予了“生命”。可以简单地一次性引入所有插件，或者逐个引入到你的页面中。下拉菜单、轮播图 Carousel等
- 引入Bootstrap样式表
- 引入js文件：jQuery.js+Bootstrap.min.js
- 复制HTML结构，并适当调整结构内容

```html
<body>

      <!-- 必须先引jquery，再引js -->
    <script src="./js/jquery.js"></script>
    <script src="./bootstrap-3.4.1-dist/js/bootstrap.min.js"></script>
</body>
```

## 参考
{{< card "https://www.bootcss.com/" >}}       