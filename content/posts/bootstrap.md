---
title: "Bootstrap的使用"
date: 2022-08-29T15:50:47+08:00
tags: ['Support']
series: ['前端学习之旅']
---

## 简介
### 概念
BootStrap框架，`快速开发 响应式网页`。

`响应式设计`：Bootstrap 可以根据不同平台（手机、平板电脑和台式机）进行调整。

BootStrap是由Twitter公司开发维护的`前端UI框架`，它提供了大量`编写好的css样式`，允许开发者结合一定`html结构和javescript`，快速编写功能完善的网页及常见交互效果。中文官网：<https://www.bootcss.com>

### 关于版本
Bootstrap5 与 Bootstrap 3 & 4：

- Bootstrap5 是 Bootstrap 的最新版本，使用了新组件、更快的样式表以及拥有更快的响应能力。

- Bootstrap5 支持所有主要的最新稳定版本浏览器，但不支持 Internet Explorer 11 及以下版本。

- Bootstrap5 和 Bootstrap 3 & 4 的主要区别在于 Bootstrap5 不再依赖 jQuery，使用了原生的 JavaScript，当然我们如果要想用也可以引入 jQuery。

- Bootstrap5 IE11 以下版本的浏览器，Bootstrap4 放弃了对 IE8 以及 iOS 6 的支持。如果需要对旧版本浏览器兼容，那么请使用 Bootstrap3。

## 下载
1、中文官网：<https://www.bootcss.com>   
2、其他下载方式: <https://www.runoob.com/bootstrap5/bootstrap5-install.html> 

中文官网下载：  
- 首页——BootStrap5文档——下载BootStrap（生产文件）——解压bootstrap-5.1.3-dist.zip压缩包——将bootstrap-5.1.3-dist文件夹放到项目中

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220825/image.39zy7rbwpz60.webp)

- 生产环境的BootStrap，项目用的
- 源码，日后自己学习用的

## 使用
### 引入文件
1、`link引入`：BootStrap提供的css、js代码  

2、Bootstrap 5 需要一个`容器元素来包裹内容`。

3、`使用手册 调用类名`：使用BootStrap提供的类样式、组件  

下载BootStrap 本地引入
```html
<head>

    <!-- 建议引入 .min文件 是格式化压缩后的，体积更小 -->
    <!-- 新 Bootstrap5 核心 CSS 文件 -->
    <link rel="stylesheet" href="./bootstrap-5.3.1-dist/css/bootstrap.min.css">
    <!-- 最新的 Bootstrap5 核心 JavaScript 文件 -->
    <script src="./bootstrap-5.3.1-dist/js/bootstrap.bundle.min.js"></script>

</head>

<body>
    <div class="container"> 
        <!-- 调用类名 编写代码-->
    </div>
</body>
```

### 手册使用  
手册地址：<https://v5.bootcss.com/docs/5.1/getting-started/introduction/>

- BootStrap预定义了大量`类`来美化页面，`掌握手册查找`方法是学习全局样式的重点
- 网站首页——BootStrap5中文文档——文档

#### 容器类   

Bootstrap 5 需要一个容器元素来包裹网站的内容。

- 可使用以下两个容器类：
    - `.container` 用于创建固定宽度的响应式页面。宽度 (max-width) 会根据屏幕宽度同比例放大或缩小。

    - `.container-fluid` 用于创建一个全屏幕尺寸的容器，占据全部视口（viewport）。容器始终跨越整个屏幕宽度（width 始终为 100%）：

```html
<!--1、容器内边距 ------>
    <!-- 默认情况下，容器都有填充左右内边距，顶部和底部没有填充内边距。 Bootstrap 提供了一些间距类用于填充边距。 比如 .pt-5 就是用于填充顶部内边距 -->

<!-- 2、容器的边框和颜色------>
    <!-- 边框（border）和颜色（bg-dark、bg-primary等）类用于设置容器的样式 -->

<!--3、响应式容器------>
    <!-- 可以使用 .container-sm|md|lg|xl 类来创建响应式容器。 -->
```


其他类名


样式  
Bootstrap 将设置全局的 CSS 样式。HTML 的基本元素均可以通过 class 设置样式并得到增强效果。还有先进的栅格系统。表格、表单、按钮、图片等
- HTML页面link标签，引入Bootstrap样式表
- 给HTML标签，添加Bootstrap的class类

组件  
Bootstrap 自带了大量可复用的组件，包括字体图标、下拉菜单、导航、警告框、弹出框等更多功能。
- 引入Bootstrap样式表
- 复制结构，修改内容

字体图标  
Glyphicons 字体图标使用步骤：
- 引入Bootstrap样式表
- 空标签调用类名（2个类名）
    - glyphicon
    - 图标类


## 参考   
{{< card "https://www.runoob.com/bootstrap5/bootstrap5-tutorial.html" >}}   
