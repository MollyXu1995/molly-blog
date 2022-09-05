---
title: "常见布局的Flex写法"
date: 2022-09-05T09:48:42+08:00
tags: ['Issue']
---

## 骰子的布局
- 骰子的一面，最多可以放置9个点。

```css
/* -----------1个点 */
.first-face {
    display: flex;
    justify-content: center;
    /* 在主轴上，居中分布 */
    align-items: center;
    /* 在侧轴上，居中分布 */
}

/* -----------2个点 */
.second-face {
    display: flex;
    justify-content: space-between;
    /* 在主轴上，两端对齐 项目之间的间隔都相等 */
}

.second-face .pip:nth-child(2) {
    align-self: flex-end;
    /* 在侧轴上，终点对齐 */
}

/* -----------3个点 */
.third-face {
    display: flex;
}

.third-face .pip:nth-child(2) {
    /* 在侧轴上，居中 */
    align-self: center;
}

.third-face .pip:nth-child(3) {
    /* 在侧轴上，终点对齐 */
    align-self: flex-end;
}

/* -----------4(6)个点 */
.fourth-face {
    display: flex;
    justify-content: space-between;
}

.fourth-face .column {
    display: flex;
    flex-direction: column;
    /* 主轴为垂直方向，从上到下 */
    justify-content: space-between;
}

/* -----------5(7)个点 */
.fifth-face,
.seventh1-face {
    display: flex;
}

.fifth-face .column,
.seventh1-face .column {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

.fifth-face .column:nth-child(2),
.seventh1-face .column:nth-child(2) {
    justify-content: center;
}

/* -----------6个点 */
.sixth-face {
    display: flex;
    justify-content: space-between;
}

.sixth-face .column {
    display: flex;
    flex-direction: column;
    /* justify-content: space-between; */
}

/* -----------8个点 */
.eighth1-face{
    display: flex;
}
.eighth1-face .column {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

/* -----------9个点 */
.nineth-face{
    display: flex;
}
.nineth-face .column{
    display: flex;
    flex-wrap: wrap;
}
```


## 网格布局
1、基本网格布局
- 最简单的网格布局，就是平均分布。在容器里面平均分配空间，跟上面的骰子布局很像，但是需要设置项目的自动缩放。

```css
.Grid {
  display: flex;
}

.Grid-cell {
  flex: 1;
}
```

2、百分比布局
- 某个网格的宽度为固定的百分比，其余网格平均分配剩余的空间。

```css
.Grid {
  display: flex;
}

.Grid-cell.u-1of1 {
  flex: 0 0 50%;
}

.Grid-cell.u-1of2 {
  flex: 0 0 25%;
}

.Grid-cell.u-1of3 {
  flex: 0 0 25%;
}
```

## 圣杯布局
- 圣杯布局（Holy Grail Layout）指的是一种最常见的网站布局。页面从上到下，分成三个部分：头部（header），躯干（body），尾部（footer）。其中躯干又水平分成三栏，从左到右为：导航、主栏、副栏。

    ![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220902/image.56ff62w9am00.webp)

```css
.HolyGrail {
  display: flex;
  min-height: 100vh;
  flex-direction: column;
}

header,
footer,
.HolyGrail-body {
  flex: 1;     /* 平均等分 */
}

.HolyGrail-body {
  display: flex;
}

.HolyGrail-content {
  flex: 1;
}

.HolyGrail-nav, .HolyGrail-ads {
  /* 两个边栏的宽度设为12em */
  flex: 0 0 12em;
}

.HolyGrail-nav {
  /* 导航放到最左边 */
  order: -1;
}
```

## 输入框的布局
- 我们常常需要在输入框的前方添加提示，后方添加按钮。
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220902/image.7faichvs65o0.webp)

```css
.InputAddOn {
  display: flex;
}

.InputAddOn-field {   /* input输入框 */
  flex: 1;
}
```

## 悬挂式布局
- 有时，主栏的左侧或右侧，需要添加一个图片栏。
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220902/image.58faswlkfi00.webp)

```css
.Media {
  display: flex;
  align-items: flex-start;
}

.Media-figure {       /* 图片 */
  margin-right: 1em;
}

.Media-body {       /* 文字 */
  flex: 1;
}
```

## 固定的底栏
- 有时，页面内容太少，无法占满一屏的高度，底栏就会抬高到页面的中间。这时可以采用Flex布局，让底栏总是出现在页面的底部。
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220902/image.48t3nygd2zm0.webp)

```css
.Site {
  display: flex;
  min-height: 100vh;
  flex-direction: column;
}

.Site-content {   /* 中间main内容 */
  flex: 1;
}
```

## 流式布局
- 每行的项目数固定，会自动分行。
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220902/image.1ml0lv9vfu68.webp)

```css
.parent {
  width: 200px;
  height: 150px;
  background-color: black;

  display: flex;
  flex-flow: row wrap;
  align-content: flex-start;
}

.child {
  box-sizing: border-box;
  background-color: white;

  flex: 0 0 25%;
  height: 50px;

  border: 1px solid red;
}
```

## 参考
{{< card "https://www.ruanyifeng.com/blog/2015/07/flex-examples.html" >}}        
