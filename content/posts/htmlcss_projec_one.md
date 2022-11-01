---
title: "html+css 入门项目 结构搭建"
date: 2022-08-12T14:43:41+08:00
tags: ['Essay']
---

## 学成在线项目
### 一、根目录
根目录：网站的第一级文件夹（以项目名命名）
1. 根据项目需求创建根目录
2. 将所有关项目的资料文件放到这个文件夹里
    - 图片文件夹：images
    - 样式文件夹：css
    - 首页：index.html
3. 打开Vscode，打开项目文件夹，创建`index.html`文件
4. css样式文件夹下，创建`index.css`文件，用来美化首页


> 注意：   
1、所有的文件夹、文件，都用小写字母命名，因为服务器不支持中文！      
2、服务器：配置很高的电脑（CPU、内存、网速等）  
3、所有的网站的首页，都得叫index.html，因为服务器找首页都是找index.html      
4、方便编写代码，可以使用分屏，左边html，右边css


### 二、代码编写
1. `!`快捷键，补充html文档骨架
2. 修改网站标题`<title>`
3. 使用`<link>`把index.css联接到index.html文件
```html
<link rel="stylesheet" href="./css/index.css">
```

---
## 小兔鲜项目

## 1
### 文件和目录准备

pc：电脑端  
client：客户

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220816/image.6w4ys788nk00.webp)


### 完成后的目录及文件结构

文件：都带后缀   
文件夹：没有后缀

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220816/image.33ps12hrzeq0.webp)

### css文件联接到html
把所有css样式文件，联接到html文件里 

因为外部样式表中，在同一元素不同样式，谁在下 谁生效  

所以，必须按照下面顺序引入：
```html
<link rel="stylesheet" href="./css/base.css">
<link rel="stylesheet" href="./css/common.css">
<link rel="stylesheet" href="./css/index.css">
```

## 2 

### base基础公共样式

场景：一般项目开始前，首先会 去除掉浏览器默认样式，设置为 当前项目需要的初始化样式

作用：防止不同浏览器中标签默认样式不同的影响，统一不同浏览器的默认显示效果，方便后续项目开发

在 `base.css` 中完成的基础公共样式代码如下：

```css
/* 去除常见标签默认的 margin 和 padding */
body,
h1,
h2,
h3,
h4,
h5,
h6,
p,
ul,
ol,
li,
dl,
dt,
dd,
input {
  margin: 0;
  padding: 0;
}

/* 内减模式 */
/* 所有标签加padding、bored，都不会撑大盒子*/
* {
    box-sizing: border-box;
  }

/* 设置网页统一的字体大小、行高、字体系列相关属性 */
/* 所有的 16px字（1.5行高）、333的颜色，都不用写代码，这些直接属于默认样式 */
body {
  font: 16px/1.5 "Helvetica Neue", Helvetica, Arial, "Microsoft Yahei",
    "Hiragino Sans GB", "Heiti SC", "WenQuanYi Micro Hei", sans-serif;
  color: #333;
}

/* 去除列表默认样式 */
ul,
ol {
  list-style: none;
}

/* 去除默认的倾斜效果 */
em,
i {
  font-style: normal;
}

/* 去除a标签默认下划线，并设置默认文字颜色 */
a {
  text-decoration: none;
  color: #333;
}

/* 设置img的垂直对齐方式为居中对齐，去除img默认下间隙 */
img {
  vertical-align: middle;
}

/* 去除input默认样式 */
input {
  border: none;
  outline: none;
  color: #333;
}

/* 左浮动 */
.fl {
  float: left;
}

/* 右浮动 */
.fr {
  float: right;
}

/* 双伪元素清除法 */
.clearfix::before,
.clearfix::after {
  content: "";
  display: table;
}
.clearfix::after {
  clear: both;
}
```

### 一、index 页面骨架

在 `index.html` 完成页面骨架搭建，其中包括：

   ```html
   <html lang="zh-CN">          <!-- 网页语言 -->
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
   
        <!-- 优化SEO -->

        <!-- 网站标题 -->
    <title>小兔鲜儿-新鲜、惠民、快捷！</title>
        <!-- 网站描述信息 -->
    <meta name="description" content="小兔鲜儿官网，致力于打造全球最大的食品、生鲜电商购物平台。">
        <!-- 网站关键字 -->
    <meta name="keywords" content="小兔鲜儿,食品,生鲜,服装,家电,电商,购物">
        <!-- 网站标题图 -->
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">


        <!-- 按顺序引入：外链式样式表后写的生效 -->
    <link rel="stylesheet" href="./css/base.css">
    <link rel="stylesheet" href="./css/common.css">
    <link rel="stylesheet" href="./css/index.css">
   ```

## 注意，实际代码编写，和以下描述不太一样！！！

### 二、网页头部 header 部分开发
> 网页最前面两个部分属于网页的头部，为了凸显网页头部的语义，使用header标签包裹内部的 `xtx-shortcut` 和 `xtx-main-nav`

#### 1. 快捷菜单：xtx-shortcut

注意点：

1. 最开始就说明，因为待会内部是导航，为了凸显对应的语义，需要使用语义标签进行包裹，所以版心的盒子就使用nav标签表示
2. 导航中的每一个之间以竖线分隔，直接写 `|` ，小米、淘宝都是这样写的，只不过他们用span包裹着的
3. 手机精灵图大小，可以直接从psd文件中获取到，然后只需要在精灵图中获取坐标即可
4. 手机精灵图使用给a设置伪元素完成，需要把伪元素转换成行内块元素
5. 但是行内块元素和文本之间存在垂直对齐方式问题，可以给行内块元素设置 `vertical-align:middle` ，但是此时行内块元素过小，还是存在误差，此时可以给行内块元素设置margin-top为负值往上偏移调整即可

#### 2. 主导航：xtx-main-nav

##### logo

注意点：

1. 直接一开始就说，中间是主要导航，使用nav标签表示包裹即可
2. logo本体直接用h1标签表示
3. h1标签中写a标签，a标签转换成行内块元素之后，只设置高度即可，让用户可以点击logo部分调整
4. a标签中需要写入文字方便搜索引擎的爬虫收录，但是用户不需要看到，因此设置 `font-size:0` 即可
5. 给nav浮动，然后设置nav的左margin40，给每一个li设置右margin48，
6. 当a标签hover之后，改变文字颜色，和增加下边框，以及内容与边框的距离设置 `padding-bottom:7px` （自己看：之前讲行内元素如a标签设置垂直方向的margin和padding对于布局是无效的，但是对于自己盒子本身是存在的效果的，布局指的是当前盒子的位置以及与其他盒子的相互位置）

##### search

注意点：

1. 给search设置margin-left，记得减去之前的48px（82-48==34）
2. 给search设置margin-top，自己下去顺带着让内部的input一起下去（自己看：为了之后精灵图相对于search定位的时候，不会top定位到最上面）
3. 设置input:search，搜索框有默认的自动内减的效果，直接设置完大小后，直接设置边框
4. 给search内部设置伪元素，注意input标签是单标签，不能在内部设置内容
5. search中的伪元素需要和input标签层叠在一起，需要设置定位，设置绝对定位后脱标，变得可以设置宽高了

##### cart

注意点：

1. 直接将cart当做精灵图设置即可


### 三、网页底部 footer 部分开发

> 网页最地下三个部分属于网页的头部，为了凸显网页底部的语义，使用footer标签包裹内部的 `xtx-contact` 、 `xtx-service` 、 `xtx-copyright`
>
> 其中带着做 `xtx-service` 、 `xtx-copyright` 两个部分，话术为：对于footer的内容来说 咱们目前先完成service和copyright部分，contact部分最后同学们有兴趣可以试着自己完成看看，课上咱们footer以service和copyright为主。

#### 1. 宣传服务：xtx-service

注意点：

1. 三个部分使用a标签，分别浮动之后，设置宽度33.33% ，高度100%
2. 设置a中的文本，设置水平垂直居中
3. 设置a内部的伪元素，伪元素转换成行内块元素，这样可以被父元素a标签水平垂直居中控制，只需要量取并设置精灵图与右侧文字的间距即可

#### 2. 版权信息：copyright

### 四、网站入口 xtx-entry 部分开发

### 五、新鲜好物面板 xtx-new-goods 部分开发

### 六、生鲜商品面板 xtx-fresh-goods 部分开发

