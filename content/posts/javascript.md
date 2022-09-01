---
title: "Javascript知识总结"
date: 2022-08-24T15:25:36+08:00
tags: ['Language']
series: ['前端学习之旅']
---

## 简介
### 计算机基础  

1、什么是编程语言？  
- 用来控制计算机的一系列指令，它有固定的格式和词汇（不同编程语言词汇不一样），必须遵守。
- 编程语言两种形式
    - 汇编语言：对硬件直接操作，英文缩写标识符
    - 高级语言：c语言、c++、javascript、PHP、java等

2、编程语言和标记语言的不同？
- 编程语言：    
    - `有很强的逻辑和行为能力，是主动的`
    - if else、for、while……

- 标记语言（html）：
    - 不向计算机发出指令，常用于格式化和链接，被读取，是被动的

3、常见的数据存储单位及其换算关系  
- bit<byte<KB<MB<GB<TB……
- 位（bit）：1bit可以保存一个0或1（最小的存储单位）
- 字节（byte）:1B=8b
- 千字节（KB）：1KB-1024B
- 兆字节（MB）：1MB=1024KB
- 吉字节（GB）：1GB=1024MB
- 太字节（TB）：1TB=1024GB
- ……

4、内存的主要作用以及特点
- 硬盘——内存——CPU
- CPU运行快，若从硬盘中读数据，会浪费CPU性能，所以才使用速度更快的内存来保存运行时的数据（内存是电，硬盘是机械）
- 从硬盘中把程序的代码加载到内存中，CPU执行内存中的代码

### 初识javascript（简称js）
1、javascript是什么？  
一种`运行在客户端`的`脚本语言`（script是脚本的意思）
- 脚本语言：不需要编译，由js解释器（js引擎）逐行进行解释并执行
- 现在也可以基于Node.js技术进行服务器端编程
- 注意javascript和java没任何关系

2、javascript的作用
- 表单动态校验、密码强度检测（js产生的最初目的）
- 网页特效
- 服务端开发（Node.js）
- 桌面程序（Electron）
- APP（Cordova）
- 控制硬件——物联网（Ruff）
- 游戏开发（cocos2d-js）

3、html/css/js的关系
- html标记语言，决定网页结构和内容（决定看到什么）
- css描述类语言，决定网页呈现给用户的模样（决定好不好看）
- js编程语言，实现业务逻辑和页面控制（决定功能）

4、浏览器执行javascript的原理  
浏览器分成两部分：渲染引擎、JS引擎
- 渲染引擎
    - 用来解析html/css，俗称内核。比如chrome浏览器的blink，老版本的webkit

- JS引擎
    - 也称为JS解释器，用来读取网页中的javascript代码，对其处理后运行。比如，chrome浏览器的V8
    - JS引擎逐行解释每一句JS源码，转换为机器语言（只有0 1），所以JS归为脚本语言，会逐行解释执行。


5、javascript由三部分组成  
- ECMAScript（javascript语法）：
    - 规定了JS的编程语法和基本核心知识，是所有浏览器厂商共同遵守的一套JS语法工业标准

- DOM（文档对象模型）
    - 全称：Document Object Model
    - 是W3C组织推荐的处理可扩展标记语言的标准编程接口
    - 通过DOM提供的接口可以对页面上的各种元素进行操作（大小、位置、颜色等）

- BOM（浏览器对象模型）
    - 全称：Browser Object Model
    - 通过BOM可以操作浏览器窗口（弹出框、控制浏览器跳转、获取分辨率等）

6、javascript的3种书写位置
- 行内式
- 内嵌式
- 外部

```html
<head>
      <!--内嵌式  -->
    <script>
        alert('你好世界');
    </script>
        
      <!-- 外部引入js文件； 注意：script标签中间不可以写代码 -->
    <script src="my.js"></script>
</head>
<body>
      <!-- 行内式  直接写到元素的内部 -->
    <input type="button" value="唐伯虎" onclick="alert('秋香')">

</body>
```
>注意：  
html中推荐使用双引号  
js中推荐使用单引号

7、javascript的注释
- 单行注释：`// 注释内容`  
快捷键：ctrl+/
- 多行注释：`/*注释内容*/`   
快捷键：ctrl+shift+/      （自己修改过的）


8、javascript三个常用输入输出语句

|方法| 说明 |归属|
|:--|:--|:--|
|alert(msg) | 浏览器弹出警示框（输出的，展示给用户看的）  | 浏览器|
|console.log('msg') | 浏览器控制台打印输出信息（控制台输出，给程序员看的） | 浏览器|
|prompt('info') |浏览器弹出输入框，用户可以输入 | 浏览器|

```html
<head>
      <!--内嵌式  -->
    <script>
        prompt('请输入您的年龄')
        alert('结果是');
        console.log('我是程序员能看到的')
    </script>

</head>
```

## 语法
### 变量
1、变量概念  
- 变量是用于存放数据的`容器`(盒子)，我们通过变量名获取数据、修改数据
- 本质上，变量就是程序在内存中申请的一块用来存放数据的空间

2、变量使用（变量的初始化）  
- 声明一个变量并赋值

    `var` myname = '卡卡';   
    //声明一个名称为myname的变量。var是一个JS关键字，声明变量后计算机会自动为变量分配一个内存空间。把卡卡赋值给myname

```html
<script>
//案例1
    var myname = '旗木卡卡西';
    var address = '火影村';
    var age = 30;             //数字不用加引号
    var email = 'kakaxi@itcast.cn';
    var gz = 2000;
    console.log(myname);  //显示信息
    console.log(address);
    console.log(age);
    console.log(email);
    console.log(gz);

   /*  var myname = '旗木卡卡西',
           address = '火影村',
           age = 30,             
           email = 'kakaxi@itcast.cn',
           gz = 2000;   */

//案例2
     //用户输入姓名，存储到一个myname的变量里面
    var myname = prompt('请输入你的名字')；
     //输出这个用户名
    alert(myname)
</script>
```

3、变量语法扩展
- 一个变量被重新赋值后，原有的值就会被覆盖，`变量值将以最后一次赋值为准`
- 同时声明多个变量时，`可只需写一个var`，多个变量名之间使用英文逗号隔开，最后以分号结尾。
- 特殊情况

|情况| 说明 |结果|
|:--|:--|:--|
|var age;console.log(age); |只声明 不赋值 | undefined|
|console.log(age) |不声明 不赋值 直接使用 |报错|
|age=10;console.log(age);| 不声明 只赋值| 10|

4、变量命名规则
- 由`字母（A-Z a-z）、数字（0-9）、下划线（_）、美元符号（$）`组成。
- 严格区分大小写。var app、var APP是两个变量
- 不能以数字开头。var 18age 是错误的
- 不能是关键字。比如var、for、while
- 变量名必须有意义，尽量以英文单词
- 遵守驼峰命名法，首字母小写，后面单词首字母大写。如myFirstName

5、变量交换案例
```html
<script>
//案例 交换2个变量的值
    var temp;    //声明一个临时变量为空
    var apple1 = '青苹果';
    var apple2 = '红苹果';             
    temp=apple1;
    apple1=apple2;
    apple2=temp;
    console.log(apple1);  //显示信息。此时apple1空间是红苹果、apple2是青苹果
    console.log(apple2);

</script>
```

### 数据类型
一、简介
- 数据类型简单讲，就是数据的类别型号
- 不同数据所需占用的存储空间是不同的，为充分利用存储空间，于是定义了不同的数据类型
- `变量的数据类型`是只有在程序运行过程中，根据等号右边的值来确定  
- js是动态语言，变量的数据类型是可以变化的
```html
<script>
    var num = 10;   //num是数字型
    var str = '朗朗';  //str是字符串型
</script>
```
二、分类  
js把数据类型分为两类：  
1、简单数据类型（Number、String、Boolean、Undefined、Null）

|简单数据类型 | 说明| 默认值|
|:--|:--|:--|
|Number | 数字型，包含整型值、浮点型值。如66、3.14|0|
|Boolean| 布尔值类型， 如true、false，等价于1和0 |false|
|String |字符串类型，如'张三'、'menglisa'。注意字符串都带引号 | ''|
|Undefined |var a;声明变量但没赋值，此时a=undefined  |undefined|
|Null |var a=null;声明了变量a为空值|null|

数字型
- 数字进制：  
    - 二进制（0 1）、八进制（0-7）、十进制（0-9）、十六进制（0-9 A-F）
    - 数字前面加0，是八进制。如010
    - 数字前面加0x，是十六进制。如0xA
- 数字范围
    - 最大值 Number.MAX_VALUE;  //值为1.79769……+308
    - 最小值 Number.MIN_VALUE; //值为5e-32
    - 无穷大 lnfinity
    - 无穷小 -lnfinity
    - NaN 代表一个非数值 not a number的意思
- 判断变量是否为非数字的类型：`isNaN(x)`
    - x是数字，返回false
    - x不是数字，返回true

字符串型
- 字符串型可以是引号中的任意文本。'北京'、'123'、'apple'




2、复杂数据类型(Object)










    运算符
    循环
    关键字
    数组
    函数
    作用域


    表格
    表单
    节点操作



## 对象
    内建对象
    Web APIs
    HTML DOM 对象
    HTML BOM 对象



## 扩展
    


## 参考
{{< card "https://www.liaoxuefeng.com/wiki/1022910821149312" >}}             
{{< card "https://www.runoob.com/css/css-tutorial.html" >}}      
{{< card "https://humble-blog.vercel.app/html" >}}  


