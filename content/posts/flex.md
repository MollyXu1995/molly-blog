---
title: "常见布局的Flex写法"
date: 2022-09-05T09:48:42+08:00
tags: ['Issue']
---

## Flex知识
- 是CSS3的一种新的浏览器提倡的布局模式；灵活控制块级项目的布局方式，避免浮动布局脱标的问题   
- CSS3弹性盒是一种当页面需要适应不同的屏幕大小以及设备类型时确保元素拥有恰当的行为的布局方式；  
- 引入弹性布局模型的目的是提供一种更加有效的方式来`对一个容器中的子元素进行排列、对齐和分配空白空间`
- IE6-9版本不支持Flex布局，关于浏览器是否兼容可查询：[caniuse](https://caniuse.com/)


#### 基本概念
- 由弹性容器（Flex container）、弹性子元素/项目(Flex item)、主轴、侧轴（交叉轴）组成  （方向可改变） 
- 通过设置`display:flex`将其定义为弹性容器，容器内包含了一个或多个项目（弹性子元素  ）

`主轴默认是水平方向`，侧轴默认是垂直方向：
![c609167878e2e2d5fe55e5785c9aea6](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220825/c609167878e2e2d5fe55e5785c9aea6.6dk02ago08g0.webp)

- 任何一个容器都可以指定为 Flex 布局

```css
.box{
  display: flex;
}

/* 行内元素也可以使用 Flex 布局 */
.box{
  display: inline-flex;
}
```

#### 容器的属性（亲父元素）
- 给亲父元素先必须添加`display:flex;`开启弹性布局。容器里子项目会横向摆放（块级变成行内 ）
- 项目是沿着主轴进行排列的。   

- 以下6个属性设置在容器上
    |属性|  说明|
    |:--|:--|
    |display:flex|开启弹性布局|
    |justify-content|项目在主轴上的排列对齐方式|
    |align-items|项目在交叉轴上的排列对齐方式|
    |flex-direction|修改主轴方向|
    |flex-wrap|项目换行|
    |flex-flow|flex-direction和flex-wrap属性的简写形式。默认值为row nowrap|
    |align-content|定义了换行后多根轴线的对齐方式|

1、`justify-content`  
- 定义了项目在主轴上的排列分布对齐方式。(项目和空白)

    |属性值|作用|
    |:--|:--|
    |flex-start|默认值，起点开始依次排列（左对齐）|
    |flex-end|终点开始依次排列（右对齐）|
    |`center`|居中|
    |space-between|两端对齐，项目之间的间隔都相等。|
    |space-around|每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。|
    |space-evenly|项目与容器、容器与容器，间距都相等|

    ![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220902/image.st1evmf8dzk.webp)

2、`align-items`
- 定义项目在交叉轴上的排列对齐方式 

    |属性值|作用|
    |:--|:--|
    |flex-start|默认值，起点开始依次排列|
    |flex-end|终点开始依次排列|
    |`center`|沿侧轴居中排列|
    |baseline|项目的第一行文字的基线对齐|
    |stretch|默认值，如果项目未设置高度或设为auto，将占满整个容器的高度|

    ![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220902/image.2fh6v177807w.webp)

3、`flex-direction`
- 决定主轴的方向（即项目的排列方向）。
- 修改主轴方向，主轴若竖着，侧轴就自动默认横着。

    |属性值|作用|
    |:--|:--|
    |row|水平（默认值）从左到右|
    |`column`|垂直，从上到下|
    |row-reverse|水平，从右向左|
    |column-reverse|垂直，从下向上|

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220902/image.rc5wnog5l6o.webp)

4、`flex-wrap`
- Flex布局，默认沿着主轴排不换行，父级宽度不够，子级就自动挤压来适应父级宽度
- 实现一条轴线排不下，项目进行换行，多行排列效果

    |属性值|作用|
    |:--|:--|
    |nowrap|默认值，不换行|
    |`wrap`|换行，第一行在上方|
    |wrap-reverse|换行，第一行在下方|

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220902/image.1rno17iwa0hs.webp)

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220902/image.3t5e8ffg2k40.webp)

5、`flex-flow`
- flex-flow属性是flex-direction属性和flex-wrap属性的简写形式
- 默认值为row nowrap。

6、`align-content`
- 定义了换行后多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。

    |属性值|作用|
    |:--|:--|
    |flex-start|默认值，起点开始依次排列|
    |flex-end|终点开始依次排列|
    |`center`|居中排列|
    |space-between|与交叉轴两端对齐，轴线之间的间隔平均分布|
    |space-around|每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍|
    |stretch|（默认值）轴线占满整个交叉轴|

    ![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220902/image.5mhekyijw000.webp)


#### 项目的属性（亲儿子元素）

- 以下6个属性设置在项目上
    |属性|  说明|
    |:--|:--|
    |align-self|控制某个子级项目在侧轴的对齐方式|
    |flex|复合属性。`flex:取值整数`，占用父级剩余尺寸的份数|
    |order|定义项目的排列顺序。数值越小，排列越靠前，默认为0。一般设置负数，使其靠前|
    |flex-grow|定义项目的放大比例。默认为0不放大|
    |flex-shrink|定义了项目的缩小比例。默认为1，即空间不足，都将等比例缩小|
    |flex-basis|定义了在分配多余空间之前，项目占据的主轴空间。默认值为auto，即项目的本来大小|

1、`align-self`  
- 控制某一个子级项目在侧轴的对齐方式（给子元素添加） 
- 可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。
- 可能取6个值，除了auto，其他都与align-items属性完全一致

|属性值|作用|
|:--|:--|
|flex-start|默认值，起点开始依次排列|
|flex-end|终点开始依次排列|
|`center`|沿侧轴居中排列|
|stretch|默认值，项目沿着主轴线被拉伸至铺满容器|
|baseline|项目的第一行文字的基线对齐|


2、`flex`  
- flex-grow, flex-shrink 和 flex-basis的简写，`默认值为0 1 auto`。后两个属性可选。
- 弹性伸缩比，使用flex属性修改项目子元素的宽度尺寸。`flex:取值整数`，占用父级剩余尺寸的份数。
- 该属性有两个快捷值：auto (即1 1 auto) 和 none (即0 0 auto)。
- 建议优先使用这个属性，而不是单独写三个分离的属性，因为浏览器会推算相关值。

比如：给外层容器`container`增加弹性容器的设置，就可以刚好的管理里面的这三个子项目`box1、box2、box3`，纵向摆放变成了横向摆放。
```html
<head>
    <style>
        .container{
             width: 500px;
             height: 500px;
            background-color: grey;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }
        .box1{
            width: 100px;
            height: 100px;
            background-color: red;
            flex: 2;
        }
        .box2{
            width: 100px;
            height: 100px;
            background-color: green;
            flex: 2;
        }
        .box3{
            width: 100px;
            height: 100px;
            background-color:blue;
            flex: 1;
        }
    </style>
</head>
<body>
    <div>
        <div class="container">
            <div class="box1"></div>
            <div class="box2"></div>
            <div class="box3"></div>
        </div>
    </div>
</body>
```

3、`order`  
- 定义项目的排列顺序。数值越小，排列越靠前，默认为0。一般设置负数，使其靠前。

4、`flex-grow`   
- 定义项目的放大比例。默认为0，即如果存在剩余空间，也不放大。  
- 如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。

5、`flex-shrink`  
- 定义了项目的缩小比例。默认为1，即如果空间不足，各项目都将等比例缩小。
- 如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小。
- 负值对该属性无效。

6、`flex-basis`  
- 定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。
- 它可以设为跟width或height属性一样的值（比如350px），则项目将占据固定空间。或百分比写法。
    
> 提示：  
>①默认弹性容器里内容横向摆放  
>②弹性容器外、弹性子元素内是正常渲染的。只定义了弹性子元素如何在弹性容器内布局


#### 关于Flex布局中使用 gap 属性
- flex布局可以使用`gap`属性，来定义间距    
- 但还处于草案阶段 [2021/6/3] ，如果需要在生产环境使用，可能需要进行考量，虽说主流浏览器全部都已经支持了。
- 详细 <https://yogwang.site/2021/CSS-use-gap-in-flex-layout/>

```css
#flex-box {
  display: flex;
  flex-wrap: wrap;
  gap: 20px 20px;
  justify-content: space-between;
}
```
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221031/image.l64ln18p1cg.webp)


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
