---
title: "css关于导航栏中间竖线的方法"
date: 2022-10-31T17:57:30+08:00
tags: ['Issue']
---

参考：<https://juejin.cn/post/6850418113675001863>

### 直接用键盘上的字符来做
因为这种做法常常用来做头部的导航栏，所以起个类名nav的盒子，下面是html结构ul+li 里面放a链接，a链接后面直接加竖线。  

```html
 <div class="nav"> 
     <ul>     
       <li><a href="##">热门</a>|</li> 
       <li><a href="##">大家电</a>|</li>            
       <li><a href="##">生活电器</a>|</li>            
       <li><a href="##">厨房电器</a>|</li>            
       <li><a href="##">个护健康</a>|</li>            
       <li><a href="##">应季电器</a>|</li>        
     </ul>    
</div>
```
下面是css样式，给nav加宽度和高度，文字垂直居中，加个背景颜色，然后让 li 浮动，给 li 里面的a加左右padding，把a转换为行内块，这样就会增加a的范围，用来增加用户体验，这个做的好处就是简单，如果某一个竖线不要，直接在html中去掉就行了。

```css
* {            
   margin: 0;            
   padding: 0;            
   box-sizing: border-box;        
}                
.nav {            
   width: 700px;           
   height: 30px;            
   line-height: 30px;            
   margin: 200px auto;            
   background-color: #eeeeee;        
}                
.nav ul li {            
   float: left;         
   list-style: none;        
}                
.nav ul li a { 
   display: inline-block;  
   /* 让竖线和文字对齐 */  
   vertical-align: middle;   
   padding: 0 20px;  
   text-decoration: none;  
   color: #333333;       
 }             
.nav ul li a:hover {            
   color: red        
}
```

### 插入标签
插入标签来做把插入的标签width设为1px，height自行调整，当然插入的标签得是行内块，或者转换为行内块，因为我们做导航栏都是用 ul 和 li 做的，所以最简单的就是把竖线用 li来做，用结构伪类选择器，选择奇数或者偶数的 li，把width设为1px，再给这个li设置margin-top和左右的margin值就行了。

```css
* {           
   margin: 0;            
   padding: 0;            
   box-sizing: border-box;    
}               
 .nav {          
   width: 700px;         
   height: 30px;        
   line-height: 30px;        
   margin: 200px auto;       
   background-color: #eeeeee;    
 }             
  .nav ul li {          
   float: left;         
   list-style: none;       
 }                
  .nav ul li a {         
   text-decoration: none;         
   color: #333333;      
 } 
 /* 选择偶数的li*/              
  .nav ul li:nth-child(2n) {          
   width: 1px;           
   height: 12px;           
   background-color: #333333;         
   margin: 10px 20px;      
  }    
```

### 用 li 的左或者右边框
给 li 左右的padding 然后来个右边框就好了

```css
.nav ul li {     
    float: left;        
    list-style: none;      
    margin-top: 10px;        
    padding: 0 20px;    
    height: 13px;     
    line-height: 13px;     
    border-right: 1px solid #333333;        }
  /*去掉最后一个 li 的边框 */
.nav ul li:last-child{
    border:0
}       
```

### 用 伪元素做
其实伪元素来做和插入标签的原理是一样的，就是细节上有点差别，而且好处是不会增加html的结构，毕竟结构越简单越好。

```css
.nav ul li::after {      
   content: '';       
   display: inline-block;    
   width: 1px;         
   height: 13px;       
   margin: 0 20px;     
   background-color: #333;  
 }     
   /* 同理，去掉最后一个竖线，这里先结构伪类选择器，再伪元素，顺序不要错了 */  
          
.nav ul li:last-child::after {     
    width: 0;    
 }
```