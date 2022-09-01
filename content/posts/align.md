---
title: "css水平垂直居中设置"
date: 2022-09-01T10:57:58+08:00
tags: ['Issue']
---

## 水平居中
### 行内元素水平居中
- 这里行内元素是指文本text、图像img、按钮button、超链接a等
- 只需给`父元素设置text-align:center;`即可实现。

```css
.father{
    text-align:center;
}
```

### 块级元素水平居中
#### 定宽块级元素水平居中  
`有width`宽度值的块状元素，只需给`需要居中的块级元素加margin:0 auto;`
```css
  .center{
      margin:0 auto;
      width:200px;
  }
```

#### 不定宽块级元素水平居中  
`没有width`宽度值的块状元素，即块级元素宽度不固定

- 方法1：设置table

给`要居中显示的元素`，设置`display:table;` 与`margin:0 auto;`来实现

```css
  .center{
      display:table;
      margin:0 auto;
  }
```

- 方法2：设置inline-block（多个块状元素）  
`子元素设置display:inline-block;` 同时`父元素设置text-align:center;`
```css
  .father{
      text-align:center;
  }
  .son{
      display:inline-block;
  }
```

- 方法3：设置flex布局  
`给要居中的块状元素的父元素`，添加`display:flex;`与`justify-content:center;`

```css
  .father{
      display:flex;
      justify-content:center;
  }
```
- 方法4：position + 负margin；
- 方法5：position + margin：auto；
- 方法6：position + transform；

注：这里方法4、5、6同下面垂直居中一样的道理，只不过需要把top/bottom改为left/right，在垂直居中部分会详细讲述。


## 垂直居中
### 单行文本垂直居中  
设置`padding-top=padding-bottom`；或`line-height=height`；

```css
.center{
      line-height=40px;    /* height=40px */
  }
```

### 多行文本垂直居中  
给`父元素设置display:table;` `子元素display:table-cell和vertical-align:middle;`

```css
  .father{
      display:table;
  }
  .son{
      display:table-cell;
      vertical-align:middle;
  }
```
### 块级元素垂直居中
- 方法1：flex布局  
在需要垂直居中的`父元素`上，设置`display:flex;和align-items:center;`
要求：`父元素必须显示设置height值`

```css
.father{
      height:300px;
      display:flex;
      align-items:center;
  }
```

- 方法2：利用position和top和负margin（需知宽高）  
1、设置元素为absolute/relative/fixed  (子绝父相)  
2、top/bottom  
3、margin-top/bottom=负高度的一半

```css
.parent{
    position: relative;
    width: 200px;
    height: 200px;
    background-color: pink;
}
.child{
    position: absolute;
    top: 50%; 
    margin-top: -50px;

    width: 150px;
    height: 100px;
    line-height: 100px;
    background-color: red;
}
```
- 方法3：利用position和top/bottom和margin:auto （需知宽高）   
1、position：absolute/relative/fixed  
2、top=bottom：0  
3、margin：auto   （注意不是margin:0 auto）


```css
.parent{
    position: relative;
    width: 200px;
    height: 200px;
    background-color: pink;
}
.child{
    position: absolute;
    top:0;
    bottom: 0;
    margin: auto;

    width: 150px;
    height: 100px;
    line-height: 100px;
    background-color: blanchedalmond;
}
```

- 方法4：利用position和top和transform  
1、transform中translate偏移的百分比就是相对于元素自身的尺寸而言的。  
2、transform方法，可用于未知元素大小的居中

```css
.parent{
    position: relative;
    width: 200px;
    height: 200px;
    background-color: pink;
}
.child{
    position: absolute;
    top:50%;
    transform: translate(0,-50%);

    background-color: blanchedalmond;
}
```

## 水平垂直居中
- 方法1：绝对定位+margin:auto
```css
.both-father {
    position: relative;

    width: 200px;
    height: 200px;
    background: green;
}
.both {
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    right: 0;
    margin: auto;

    width: 150px;
    height: 100px;
    background-color: red;
    line-height: 100px;
    text-align: center;
}
```

- 方法2：绝对定位+负margin

```css
    div{
        width:200px;
        height: 200px;
        background:green;
        
        position: absolute;
        left:50%;
        top:50%;
        margin-left:-100px;
        margin-top:-100px;
    }
```

- 方法3：绝对定位+transform

```css
    div{
        width: 200px;
        height: 200px;
        background: green;
        
        position:absolute;
        left:50%;    /* 定位父级的50% */
        top:50%;
        transform: translate(-50%,-50%); /*自己的50% */
    }
```
 
- 方法4：flex布局  
只要三句话就可以实现不定宽高水平垂直居中。
```css
.box{
        height:600px;  
        
        display:flex;
        justify-content:center;  /*子元素水平居中*/
        align-items:center;      /*子元素垂直居中 */
}

.box>div{
    background: green;
    width: 200px;
    height: 200px;
}
```

- 方法5：table-cell实现居中

设置
display:table-cell;  
text-align:center;  
vertical-align: middle;  