---
title: "html头部链接+css清除默认样式"
date: 2022-09-01T10:53:28+08:00
tags: ['Issue']
---


## html头部链接

```html
<html lang="zh-CN"> 
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

        
    <meta name="description" content="小兔鲜儿官网，致力于打造全球最大的食品购物平台。">
    <meta name="keywords" content="小兔鲜儿,食品,生鲜,服装,家电,电商,购物">
    
    <title>小兔鲜儿-新鲜、惠民、快捷！</title>
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">

    <link rel="stylesheet" href="./font/iconfont.css">

    <link rel="stylesheet" href="./css/base.css">
    <link rel="stylesheet" href="./css/common.css">
    <link rel="stylesheet" href="./css/index.css">
</head>

<body>

    <script src="my.js"></script>
    <script src="./js/jquery.min.js"></script>
    <script src="./js/slider.js"></script>
</body>
```

## css清除默认样式

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

body {
  font: 16px/1.5 "Helvetica Neue", Helvetica, Arial, "Microsoft Yahei",
    "Hiragino Sans GB", "Heiti SC", "WenQuanYi Micro Hei", sans-serif;
  color: #333;
}

ul,
ol {
  list-style: none;
}

em,
i {
  font-style: normal;
}

a {
  text-decoration: none;
  color: #333;
}

img {
  vertical-align: middle;
}

input {
  border: none;
  outline: none;
  color: #333;
}

.fl {
  float: left;
}

.fr {
  float: right;
}

.clearfix::before,
.clearfix::after {
  content: "";
  display: table;
}
.clearfix::after {
  clear: both;
}
```

## 项目结构创建目录

文件：
- `index.html` 
- `favicon.ico` 网页标题图

文件夹：
- `html`
- `css`
- `js`
- `images` 一般是png格式：logo图、精灵图等
- `uploads` 商品产品图:jpg格式、png格式等
- `less`
- `lib`下载解压的字体图标、别人的代码等等

