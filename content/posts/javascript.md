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
JS组成
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221016/image.1ihf3hyz9pb4.webp)

- Web API 是浏览器提供的一套操作`浏览器功能(BOM)`和`页面元素(DOM)`的API，针对浏览器做交互效果
- Web API 一般有输入和输出（函数的传参和返回值），很多都是方法（函数）
- API 是应用程序编程接口。是给程序员提供的一种接口工具，以更轻松的实现功能
- Web API很多，所以将这个阶段称为Web APIs

详细API：<https://developer.mozilla.org/en-US/docs/Web/API>

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
|alert('msg') | 浏览器弹出警示框（输出的，展示给用户看的）  | 浏览器|
|console.log('msg') | 浏览器控制台打印输出信息（控制台输出，给程序员看的） | 浏览器|
|prompt('info') |浏览器弹出输入框，用户可以输入 | 浏览器|

```html
<head>
      <!--内嵌式  -->
    <script>
        prompt('请输入您的年龄')
        alert('结果是');
        // 快捷键：log 回车
        console.log('我是程序员能看到的')
    </script>

</head>
```

### js规范

1、标识符命名规范

- 变量、函数的命名必须要有意义
- 变量的名称一般用名词
- 函数的名称一般用动词

2、书写规范
```js
// 小括号的左右两侧保留一个空格
// 运算符左右两侧保留一个空格
for (var i = 1; i <= 1000; i++ ) {   

}

// 单行注释的符号与文字之间保留一个空格
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

#### 分类  
js把数据类型分为两类：简单数据类型、复杂数据类型

一、简单数据类型（Number、String、Boolean、Undefined、Null）
- 又叫做基本数据类型、值类型
- 储存的是值本身

|简单数据类型 | 说明| 默认值|
|:--|:--|:--|
|String |字符串类型，如'张三'、'menglisa'。注意字符串都带引号 | ''|
|Number | 数字型，包含整型值、浮点型值。如66、3.14|0|
|Boolean| 布尔值类型， 如true、false，等价于1和0 |false|
|Undefined |var a;声明变量但没赋值，此时a=undefined  |undefined|
|Null |var a=null;声明了变量a为空值|null|

1、数字型
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

2、字符串型  

字符串型可以是`引号中的任意文本`。'北京'、'123'、'apple'都叫字符串

- 字符串引号嵌套：`外单内双`或 外双内单。'我是一名"漂亮"的女生'
- 字符串转义符：字符串中也有特殊字符，我们称为转义符。`转义符都是\开头的`要写到字符串引号里面

    |转义符 |解释说明|
    |:--|:--|
    |\n |换行，n是newline的意思|
    |`\\ `|斜杠`\`|
    |`\'` |'单引号|
    |`\"` |"双引号|
    |\t |tab缩进|
    |\b |空格，b是blank的意思|

- 字符串长度：字符的数量就是字符串的长度。通过`length`属性可以检测获取整个字符串的长度
```js
var str = 'my name is andy';  
console.log(str.length);    //打印字符串的长度，显示15
```
- 字符串的拼接：多个字符串之间可以使用`+`进行拼接。
    - `字符串型+任何类型`，`最终的结果是字符串类型`。
    - `字符串和变量拼接`：变量不要写到字符串引号里面，是通过和字符串相连+的方式实现的

```js
//口诀：数值相加，字符相连
console.log('沙漠'+'骆驼');   //结果是：'沙漠骆驼'
console.log('小兰花'+18);   //结果是：'小兰花18'
console.log('meng'+lisa);   //结果是：'menglisa'
console.log('12'+12);   //结果是：'1212'
console.log(12+12);   //结果是：24

// 变量可以很方便地修改里面的值
//口诀：变量两侧都有字符串拼接，"引引加加"，变量写加中间
var age = 19;
console.log('小兰花' + age + '岁');   //结果是：小兰花19岁
```

```js
//案例:js简单交互——显示用户输入的年龄

//弹出一个输入框（prompt），让用户输入年龄（用户输入）
//把用户输入的值用变量保存起来，把刚才输入的年龄与所要输出的字符串拼接（程序内部处理）
//使用alert语句弹出警示框（输出结果）
var age = prompt("请输入您的年龄");
var str = '您今年已经'+age+'岁了';
alert(str);
```

3、布尔型Boolean、未定义型Undefined、空类型Null
- 布尔类型有两个值:true和false，其中true表示真（对），而false表示假（错）。布尔型和数字型一起参与运算相加的时候，true当作1看，false当作0看。
- 如果一个变量声明未赋值，就是Undefined未定义数据类型
- Null空数据类型。空值。

```js
console.log(true + 1);   //结果为2
console.log(false + 1);  //结果为1


var str;
console.log(str);  //结果就是Undefined

// undefined和数字相加 结果是NaN
var variable = undefined;
console.log(variable + 'pink');  //结果为 variablepink
console.log(variable + 1);  //结果为 NaN

var space = null;
console.log(space + 'pink');  //结果为 nullpink
console.log(space + 1);  //结果为 1
```

二、复杂数据类型(Object、Array、Date……)
- 又叫引用数据类型
- 存储的仅仅是地址

#### typeof 获取检测变量的数据类型
```js
var num=18;
console.log(typeof num);   //结果为 number

var str = 'pink';
console.log(typeof str);  //结果就是 string

var flag = true;
console.log(typeof flag);  //结果为 Boolean

var vari = undefined;
console.log(typeof vari);  //结果为 undefined

var timer = null;
console.log(typeof null);  //结果为 Object

// 使用表单、 prompt获取过来的值是 字符串类型的
var age = prompt('请输入您的年龄')；
console.log(age);
console.log(typeof age);
```
>1、chrome调试工作台中，各类型的字体颜色不同：    
    数字型，蓝色  
    字符型，黑色  
    布尔型，深蓝色  
    undefined、null，浅灰色
>
>2、使用表单、 prompt获取过来的值是 字符串类型的

#### 数据类型转换
概念：把一种数据类型的变量转换成另外一种数据类型。

一、转换为字符串类型

|方式 |说明| 案例|备注|
|:--|:--|:--|:--|
|变量.toString() | 转成字符串 |var num = 1; alert(num.toString());|
|String(变量) | 强制转换成字符串 | var num = 1; alert(String(num));|
|`加号拼接字符串` | 和字符串拼接的结果都是字符串| var num = 1; alert(num+'我是字符串');|常用|

```js
//把数字型转换为字符串类型 
var num = 10;

//方法1：变量.toString();
var str = num.toString();
console.log(str); 
console.log(typeof str); 

// 方法2：String(变量)
console.log(String(num)); 

// 方法3：利用 + 拼接字符串  
//这种方法最常用，也称为隐式转换
console.log(num + '');  
```

二、转换为数字型

|方式 |说明| 案例|备注|
|:--|:--|:--|:--|
|`parseInt(变量)` | 将string类型转换为整数数值型 |parselnt('78');|常用|
|`parseFloat(变量)` | 将string类型转换为浮点数数值型 | parseFloat('78.23');|常用|
|Number(变量) | 强制转换,将string类型转换为数值型|Number('12');|
|js隐式转换|（减- 乘* 除/）利用算术运算隐式转换为数值型|'12'-0|

```js
//把字符串类型转换为数字类型 
var age = prompt("请输入您的年龄");

//方法1：parseInt(变量)  可以把 字符型转换为数字型 且取整数
console.log(parseInt('3.64'));  //结果是 3
console.log(parseInt('120px'));  //结果是 120 会去掉单位
console.log(parseInt('ab120px'));  //结果是 NaN

// 方法2：parseFloat(变量)  可以把 字符型转换为数字型  得到的是小数
console.log(parseFloat('3.64'));   //结果是 3.64
console.log(parseFloat('120px'));  //结果是 120 会去掉单位
console.log(parseFloat('ab120px'));  //结果是 NaN

// 方法3：Number(变量)
console.log(Number('123'));  

// 方法4：利用算术运算  （减- 乘* 除/）
console.log('12'-0);  //结果是 数字型 12
console.log('123'-'120');  //结果是 数字型 3
```

```js
//案例1：输入出生年份计算年龄
var year = prompt('请输入您的出生年份')；
var age = 2018 - year;  // year取过来的是字符串型  但这里用了减法隐式转换 变成了数字型
alert('您今年已经' + age + '岁了');

//案例2：简单加法器
var num1 = prompt('请您输入第一个值')；
var num2 = prompt('请您输入第二个值')；
var result = parseFloat(num1) + parseFloat(num1)； //这里注意：数据类型的转换
alert('您的结果是:' + result);
```

三、转换为布尔型

|方式 |说明|
|:--|:--|
|Boolean(变量) | 其他类型转换成布尔值 |

- 代表`空、否定的值`会被转换为false，如''、0、NaN、null、underfined
- 其余值会被转换为true

```js
console.log(Boolean(''));   //结果是 false
console.log(Boolean('12'));   //结果是 true
```
>概念拓展：  
解释性语言(javascript)、编译型语言(java)的区别，在于翻译的时间点不同：      
>1、解释性语言：运行时进行及时解释，并立即执行（边解释边执行）  
>2、编译型语言：代码执行之前进行编译，生成中间代码文件，再解释执行  
>
>标识（zhi）符: 指开发人员为变量、属性、函数、参数取的名字。标识符不能是关键字或保留字  
关键字: js本身已经使用的字，不能再用来当变量名、方法名  
保留字: 预留的“关键字”，未来可能会使用

#### 内存分配
（js中没有堆栈的概念，只是利用堆栈概念来理解下代码的执行方式）

一、简单数据类型的内存分配
- 简单数据类型是，存放在栈里面，是直接开辟一个空间 存放的是值
- 简单数据类型 null 返回的是一个空对象 
```js
// 如果有个变量想打算存储为对象，但暂时没想好放啥，这时候就可先给 null
var timer = null;
console.log(typeof timer); // object
```

二、复杂数据类型的内存分配
- 首先在栈里面存放地址，十六进制表示，然后这个地址指向堆里面的数据

#### 传参
一、简单数据类型的传参
```js
// 函数的形参也可以看作一个变量，当把一个值类型变量作为参数传递给函数的形参时，其实是把变量在栈空间里的值复制了一份给形参，那么在方法内部对形参做任何修改，都不会影响到外部变量

function fn(a) {
    a++;
    console.log(a); //11
}
var x = 10;
fn(x);
console.log(x); // 10
```

二、复杂数据类型的传参
```js
function Person(name) {
    this.name = name;
}
function f1(x) {
    console.log(x.name); // 2、刘德华 
    x.name = '张学友';
    console.log(x.name); // 3、张学友  
}
var p = new Person('刘德华');
console.log(p.name);   // 1、刘德华  
f1(p);
console.log(p.name); // 4、张学友  

// 结果 ：刘德华 刘德华 张学友 张学友
```

### 运算符
运算符（operator）也被称为操作符，是用来实现赋值、比较、执行算数运算功能的符号。
#### 算数运算符
概念：算数运算使用的符号，用于执行两个变量或值的算术运算；

|运算符 |描述|实例|
|:--|:--|:--|
|+ | 加 |10+20=30|
|- | 减 |10-20=-10|
|* | 乘 |10*20=200|
|/ | 除 |10/20=0.5|
|% | 取余数（取模） |返回除法的余数 9%2=1|

```js
console.log(1 + 2);   //3
console.log(5 * 3);   //15
//取余数 判断一个数能否被整除
console.log(4 % 2);   //0
//先乘除后加减，有括号先算括号里面的
console.log(1 + 2 * 3);   //7

//浮点数 在算数运算中会有问题
//浮点数的最高精度是17位小数，但在算术运算时精度远远不如整数
//所以，两个浮点数，不要直接算术运算、不要判断是否相等
console.log(0.1 + 0.2); //0.3000000…4
console.log(0.7 * 10);  //7.000000…1

//表达式和返回值
//由数字、运算符、变量组成的式子 我们称为表达式  1+2
console.log(1 + 2); //3就是返回值
//程序里面，把右边表达式计算完毕 返回值给左边
var num = 1 + 1;
```

#### 递增和递减运算符
- 需要反复给数字变量添加或减去1，可以使用递增（++）和递减（--）运算符来完成
- 递增（++）和递减（--）运算符必须和变量配合使用

1、前置递增（递减）运算符  
`++num`；递增（++）和递减（--）放在变量前面。

```js
var age = 10;
++age;  //类似于age=age+1
console.log(age);  //11

//先自加1，再返回值
var p = 10;
console.log(++p + 10);  //21
```

2、后置递增（递减）运算符  
`num++`；递增（++）和递减（--）放在变量后面。

```js
//前置递增和后置递增单独使用 效果是一样的
var age = 10;
age++;  //类似于age=age+1
console.log(age);  //11

//先返回原值，后自加1
var p = 10;
console.log(p++ + 10);  //20
console.log(p);  //11
```

3、总结
- 前置、后置递增单独使用，结果是一样的
- 与其他代码联用时，结果不一样
- 后置：先原值计算，后自加
- 前置：先自加，后计算
- 开发时，`大多使用后置`,并且代码独占一行，如num++;

```js
var a = 10; 
++a;  // ++a=11  a=11
var b = ++a + 2;  //  ++a=12 
console.log(b);  //14

var c = 10;
c++;  // c++=11  c=11
var d = c++ + 2;  //c++=11
console.log(d);   //13

var e = 10;
var f = e++ + ++e;   // e++=10  e=11 ;  ++e=12 
console.log(f);   //22
```

#### 比较运算符
- 两个数据进行比较时使用的运算符；
- 比较运算后，会返回一个布尔值（true/false）作为运算的结果。

|比较运算符 |说明| 案例| 结果|
|:--|:--|:--|:--|
|<|小于号|1<2|true|
|>|大于号|1>2|false|
|>=|大于等于号|2>=2|true|
|<=|小于等于号|3<=2|false|
|==|判等号（会转型），值相等即可|37==37|true|
|!=|不等号|37！=37|false|
|===|全等。要求值、数据类型都得一致|37==='37'|false|
|!==|全不等。要求值、数据类型都得不一致|46!=='37'|true|

|符号|作用| 用法|
|:--|:--|:--|
|=|赋值|把右边给左边|
|==|判断|判断两边值是否相等 （注意此时有隐式转换：会把字符串型默认转换为数字型），只要求值相等就可以了|
|===|全等|判断两边的值和数据类型是否完全相同|

```js
console.log(18 == '18');   //true
console.log(18 === '18');   //false
```

#### 逻辑运算符
1、用来进行布尔值运算的运算符，返回值也是布尔值；开发中常用于多个条件的判断

|运算符 |说明| 案例|结果|备注|
|:--|:--|:--|:--|:--|
|&&|“逻辑与”，简称“与” and|ture&&false|false|全为true才为true，否则为false|
|ll|“逻辑或”，简称“或” or|ture ll false|ture|全为false才为false，否则为true|
|！|“逻辑非”，简称“非” not|!true|false|取反|

```js
var res = 2 > 1 && 3 > 1; 
console.log(res);   //true

console.log(3 > 5 && 3 > 2);   //false
console.log(3 < 5 && 3 > 2);   //true

console.log(3 > 5 || 3 > 2);   //true
console.log(3 < 5 || 3 < 2);   //false

console.log(!true);   //false

//案例练习
var num = 7;
var str = "我爱你~中国~";
console.log(num > 5 && str.length >= num);   //true

console.log(!(num < 10));   //false
console.log(!(num < 10 || str.length == num));   //false
```

2、逻辑中断（短路运算）  
当有多个表达式（值）时，左边的表达式值可以确定结果时，就不再继续运算右边的表达式的值。逻辑中断很重要，她会影响我们程序的运行结果。  

- 逻辑与：表达式1 && 表达式2  
表达式1真，则返回表达式2；表达式1假，则返回表达式1

- 逻辑或：表达式1 || 表达式2  
表达式1真，则返回表达式1；表达式1假，则返回表达式2

```js
//如果有空的、否定的都代表是假，其余为真   
//0/空/null/undefined/NaN

console.log(123 && 456);   //456
console.log(0 && 456);   //0

console.log(0 && 1 + 2 && 456 * 56789);   //0
console.log('' && 1 + 2 && 456 * 56789);   //''

console.log(123 || 456 || 789 + 345);   //123
console.log(0 || 456 || 789 + 123);   //456
```

#### 赋值运算符
用来把数据赋值给变量的运算符

|符号|说明|
|:--|:--|
|=|直接赋值|
|+=、-=|加、减一个数 后再赋值|
|*=、/=、%=|乘、除、取模 后再赋值|

```js
var age = 10;
age += 5;  //相当于 age = age + 5;  结果15
age -= 5;  //相当于 age = age - 5;   结果5
age *= 10;  //相当于 age = age * 10;  结果100
```

#### 运算符优先级
从高到低：
|优先级 |运算符|顺序|
|:--|:--|:--|
|1|小括号|（ ）|
|2|一元运算符|++ -- ！|
|3|算数运算符|先* / % 后+ -|
|4|关系运算符|> >= < <=|
|5|相等运算符|== != === !==|
|6|逻辑运算符| 先&& 后ll|
|7|赋值运算符|=|
|8|逗号运算符|，|

- 一元运算符中，逻辑非优先级很高
- 逻辑与 比 逻辑或 优先级高

### 流程控制
通过控制代码的执行顺序来实现我们要完成的功能。

#### 顺序结构
程序按照代码的先后顺序，依次执行。

#### 分支结构
- 由上到下执行代码的过程中，根据不同的条件，执行不同的路径代码（执行代码多选一的过程），从而得到不同的结果。
- 两种分支结构语句：if、switch。  

一、if语句

```js
//满足if语句的条件表达式时，就执行大括号里面的代码；否则执行大括号后面的代码。
if (条件表达式) {
    执行语句；
}

//案例
var age = prompt('请输入您的年龄：')；
if (age >= 18) {
    alert('你可以进入网吧')；
}
```

二、if……else语句
- 2选1

```js
//条件成立时，执行if里面的代码；否则执行else里面的代码。
//if、else，最终只能有一个语句执行
if (条件表达式) {
    执行语句1；
} else {
    执行语句2；
}

// 例子1
var age = prompt('请输入您的年龄：')；
if (age >= 18) {
    alert('你可以进入网吧')；
} else {
    alert('未成年不能进哦')；   
}

// 例子2：判断闰年
//能被4整除且不能整除100的为闰年，或者能够被400整除的就是闰年
//如2004年是闰年，1901年不是闰年
var year = prompt('请输入您的年份：')；
if (year % 4 == 0 && year % 100 != 0 || year % 400 == 0) {
    alert('是闰年')；
} else {
    alert('不是闰年，是平年')；   
}
```

三、if…… else if ……else语句
- 适用于检查多重条件
- 多选1

```js
//满足条件1，就执行语句1，语句1执行完毕后，直接退出整个if语句
//条件1不满足，则判断条件2，满足条件2就执行语句2，完毕直接退出整个，以此类推
//所有条件都不满足，就执行else里面的语句

//多选1，最终只能执行一个语句
//else if个数可以是任意多个。else if中间是有空格的

if (条件表达式1) {
    执行语句1；
} else if (条件表达式2) {
    执行语句2；
} else if (条件表达式3) {
    执行语句3；
    ……
} else {
    上述条件都不满足，执行此代码；
}

//案例 判断成绩等级
var score = prompt('请输入您的分数：')；
if (score >= 90) {
    alert('优秀')；
} else if (score >= 80)  {
    alert('良好')； 
} else if (score >= 70)  {
    alert('中等')；     
} else if (score >= 60)  {
    alert('及格')；   
} else {
    alert('要争取下次进步及格呀')；
}
```

四、switch语句  
- 针对变量设置一系列的`特定值`的选项时，就可以使用switch。
- 多选1

```js
//表达式的值 和 case选项值 进行全等匹配，如果匹配上就执行case语句；
//都没有匹配上，就执行dafault语句
// 注意：表达式的值 和 case选项值 必须全等，即值、数据类型都一致。
switch(表达式) {
    case value1:
        执行语句1;
        break;
    case value2:
        执行语句2;
        break;
    ……
    dafault:
        以上都没有匹配上，就执行此条语句;
}

//案例
var num = 2；
switch(num) {
    case 1:
        console.log('这是1');
        break;
    case 2:
        console.log('这是2');
        break;
    case 3:
        console.log('这是3');
        break;
    dafault:
        console.log('没有匹配结果');
}
```
五、总结  
if… else if …else、switch语句 的区别： 
 
1、switch语句，通常处理`确定值`的情况；if… else if …else语句常用于`范围判断`  
2、switch语句判断后直接执行，效率高；if… else if …else有几种条件就得判断多少次  
3、分支少时，switch语句效率更高  
4、分支多时，if… else if …else结构更清晰


#### 循环结构
- 对于具有规律性的重复操作，`可以重复执行某些代码`实现。
- 3种循环语句：for、while、do……while
- for循环更常用

一、for循环
- 通常和`计数`有关系

```js
for (var声明变量初始化; 条件表达式; 操作表达式) {
        循环体语句;
}

//例1、 执行 1000次 “媳妇我错了”
for (var i = 1; i <= 1000; i++) {
        console.log('媳妇我错了');
}

// 例2： 让用户控制输出的次数
var num = prompt('请输入次数：');
for (var i = 1; i <= num; i++) {
        console.log('真的错了');
}

// 例3： 1-100 所有整数和的平均值
var sum = 0;
var average = 0;
for (var i = 1; i <= 100; i++) {
        sum += i;
        //sum = sum + i;
}
average = sum / 100;
console.log(average);


// 例4： 1-100 所有偶数和、奇数和
var even = 0;
var odd = 0;
for (var i = 1; i <= 100; i++) {
      if (i % 2 == 0) {
        even = even + i;
      } else {
        odd = odd + i;
      }
}
console.log('1~100之间的所有偶数和是' + even);
console.log('1~100之间的所有偶数和是' + odd);


// 例5：求全班级同学的总成绩、平均成绩
var num = prompt('请输入班级总人数：');
var sum = 0;
var average = 0;
for (var i = 1; i <= num; i++) {
    var score = prompt('请输入第' + i + '个学生成绩');
       //从prompt取过来的数是字符串型，需要转换为数字型
       sum = sum + parseFloat(score); 
}
average = sum / num;
alert('全班级同学的总成绩是' + sum);
alert('全班级同学的平均成绩是' + average);


// 例6：打印星星   采取追加字符串的方式
var num = prompt('请输入星星个数');
var str = '';
for (var i = 1; i <= num; i++) {
       str = str + '⭐'; 
}
console.log(str);
```

二、双重for循环
循环嵌套，for循环嵌套for循环。

```js
//外层循环循环一次，里层的循环执行全部

for (外层声明变量初始化; 外层条件表达式; 外层操作表达式) {
    for (里层声明变量初始化; 里层条件表达式; 里层操作表达式) {
        执行语句；
    }
}

// 例1： 打印 五行五列星星  
// 外层循环负责打印五行 
// 内层循环负责一行打印5个星星
var str = '';
for (var i = 1; i <= 5; i++) {
    for (var j = 1; j <= 5; j++) {
        str = str + '⭐'; 
    }
    //打印完一行 换行
    str = str + '\n'; 
}
console.log(str);

// 例2：打印倒直角三角形
var str = '';
for (var i = 1; i <= 10; i++) {
    for (var j = i; j <= 10; j++) {   // j = i
        str = str + '⭐'; 
    }
    str = str + '\n'; 
}
console.log(str);

// 例3：打印九九乘法表
var str = '';
for (var i = 1; i <= 9; i++) {
    for (var j = 1; j <= i; j++) {    // j <= i
        //1 × 2 = 2  
        str += j + '×' + i + '=' + i * j + '\t';   // '\t'空格
    }
    str = str + '\n'; 
}
console.log(str);
```

三、while循环  
- 当……的时候
- 满足条件时，执行循环体语句，直到不满足条件为止，才结束整个循环过程

```js
while (条件表达式) {
    循环体代码;
}

// 例1：打印一个人的从1-100岁
var i = 1;
while (i <= 100) {
    console.log('这个人今年' +  i  + ' 岁了');
    i++;
}

// 例2：1-100所有整数和
var sum = 0;
var j = 1;
while (j <= 100) {
    sum = sum + j;
    j++;
}
console.log(sum);

// 例3：弹出提示框 你爱我吗？ 输入我爱你就提示结束，否则，一直询问
var message = prompt('你爱我吗？');
while (message !== '我爱你') {
    message = prompt('你爱我吗？');
}
alert('我也爱你呀');
```

四、do……while循环
- 先执行一次循环体代码，再执行表达式，满足条件执行循环体，否则退出
- 所以，至少会执行一次循环体代码

```js
do {
    循环体语句;
} while (条件表达式)

// 例1：1-100所有整数和
var sum = 0;
var j = 1;
do {
    sum = sum + j;
    j++;
} while (j <= 100)
console.log(sum);

// 例2：弹出提示框 你爱我吗？ 输入我爱你就提示结束，否则，一直询问
do {
    var message = prompt('你爱我吗？');
} while (message !== '我爱你')
alert('我也爱你呀');
```

#### 三元表达式
- 由三元运算符组成的式子称为三元表达式

```js
//满足条件，则返回表达式1的值，否则返回表达式2的值
条件表达式 ? '表达式1' : '表达式2';

var num = 10;
var result = num > 5 ? '是的' : '不是的';
console.log(result);

//上述写法，就是下列写法的意思：
/* var num = 10;
if (num > 5) {
    result = '是的'；
} else {
    result = '不是的'；
}
 */

//案例  给小于10的数字前面补0
var time = prompt('请输入0~59之间的一个数字：');
var result = time < 10 ? '0' + time : time;
alert(result)；
```
#### 断点调试
- 通过调试代码，更好的解决bug，学习观察程序的运行过程
- chrome浏览器，检查工具，sources中：  
1、程序单步执行  （刷新下界面）
2、watch监视变量值的变化

![f42112917d261d0524b2a5250d9a14b](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220922/f42112917d261d0524b2a5250d9a14b.2fp2fswxkcg0.webp)

### 关键字
一、continue  
- continue关键字，用于立即跳出本次循环，继续执行剩余次数循环。（如for、while）

```js
// 吃5个包子，第3个包子有虫，就扔掉第3个，继续吃第4个第5个
for (var i = 1; i <= 5; i++) {
    if (i == 3) {    
        continue;  //只要遇到 continue就退出本次循环 直接跳到 i++
    }
    console.log(我正在吃第个' + i + '包子);
}

//求1-100之间，除了能被7整除之外的整数和
var sum = 0;
for (var i = 1; i <= 100; i++) {
    if (i % 7 == 0) {    
        continue; 
    }
    sum = sum + i;
}
console.log(sum );
```

二、break
- 立即退出整个循环。 （如for、while）

```js
// 吃5个包子，第3个包子有虫，都扔掉不吃了
for (var i = 1; i <= 5; i++) {
    if (i == 3) {    
        break;  
    }
    console.log(我正在吃第个' + i + '包子);
}
```
三、return
- 函数返回值。不仅可以退出循环，还能够返回return语句中的值，同时结束当前函数体内的代码


### 数组
- 一组数据的集合，其中的每个数据称为元素，在数组中可以存放任意类型的数据。
- 数组是`将一组数据存储在单个变量名下`的方式。

- 使用数组（array）可以把一组相关的数据一起存放，并提供方便的访问（获取）方式。

```js
//普通变量一次只能存储一个值
var num = 10;

//数组一次可以存储多个值
var arr = [1,2,3,4,5];
```

#### 创建数组
js中创建数组有两种方式：
1. 利用`new`创建数组
2. 利用数组`字面量[]`创建数组 （常用）

```js
// 1、用new创建数组 
// 创建一个新的空数组 注意A要大写
var 数组名 = new Array();
var 数组名 = new Array('刘德华');

// 2、用数组字面量创建数组   字面量就是方括号 []
// 创建空的数组
var 数组名 = [];  
//创建带初始值的数组
var 数组名 = ['小黑','大黄', 6, true, 8];
```

#### 获取数组中的元素
- 索引（下标）：用来访问数组元素的序号（从0开始）
- 通过 `数组名[索引号]` 的形式访问获取数组中的这个元素

```js
var arr = ['小黑','大黄', '小兰', '小白'];
// 索引号    0      1       2       3
console.log(arr[0]); // 小黑
console.log(arr[1]); // 大黄
console.log(arr[2]); // 小兰
console.log(arr[3]); // 小白
console.log(arr[4]); // undefined
```

#### 遍历数组
- 把数组的元素从头到尾访问一次
- `数组名[i]` 指索引号为i的元素
- 可以`利用循环`把数组里面的元素全部取出来

```js
// i是计数器 当索引号使用
//索引号是从0开始，所以 i 必须从 0 开始
var arr = ['小黑','大黄', '小兰', '小白'];
for (var i = 0; i < 4; i++){
    console.log(arr[i]); 
    //输出所有数组元素
}
```

一、数组长度
- 数组长度是元素个数 不要与索引号混淆
- `数组名.length`访问数组元素的个数

```js
var arr = ['关羽', '刘备', '张飞', '曹操'];
console.log(arr.length);  // 4
for (var i = 0; i < arr.length; i++){
    console.log(arr[i]); 
}
```

二、计算数组的和以及平均值  

求数组[2,6,1,7,4]里面所有元素的和以及平均值

```js
var arr = [2, 6, 1, 7, 4];
var sum = 0;
var average = 0;
for (var i = 0; i < arr.length; i++) {
    // 计数器 i 当作索引号使用 所以从i=0开始
    // arr[i] 是数组的元素  指索引号为 i的元素
    sum += arr[i];
}
average = sum / arr.length;
console.log(sum, average); 
// 想要输出多个变量，用逗号分隔即可
```

三、求数组中的最大值

求数组[2,6,1,77,52,25,7,99]中的最大值

```js
var arr = [2, 6, 1, 77, 52, 25, 7, 99];
var max = arr[0];
// 把数组第一个元素（索引号为0）先赋值给max  
// 所以 从 i=1开始 进行比较  冒泡法排序
for (var i = 1; i < arr.length; i++) {
    if (arr[i] > max) {
        max = arr[i];
    }
}
console.log('该数组里面的最大值是：' + max);  // 99
```

四、数组转换为字符串

将数组['red','green','blue','pink']转换为字符串，并用符号 | 或其他符号分割

```js
var arr = ['red', 'green', 'blue', 'pink'];
var str = ''; // 定义空的字符串变量
var sep = '*';  // 符号字符变量
for (var i = 0; i < arr.length; i++) {
    str += arr[i] + sep;
}
console.log(str); // red*green*blue*pink*
```

五、 数组中新增元素
- 先，修改数组的length长度
- 再，追加数组新元素

```js
// 数组新增元素：
// 第一，修改数组的length长度
var arr = ['red', 'green', 'blue'];
console.log(arr.length); // 3
arr.length = 5;  // 数组长度修改为5 里面应该有5个元素
// console.log(arr);  // 打印这个数组  ['red', 'green', 'blue', empty × 2]
// console.log(arr[3]);  // 打印索引号为3的元素 undefined
// console.log(arr[4]);  // 打印索引号为4的元素 undefined

// 第二，追加数组元素
arr[3]='pink';   // 追加索引号为3的元素
arr[4]='hotpink'; // 追加索引号为4的元素
arr[0]='yellow';  //这里是替换原来的元素
console.log(arr);


//例子：  新建数组，里面存放10个整数（1~10）

var arr = [];  // 声明一个空数组
// i在循环中是计数器，在数组中也是索引号，所以 i=0 开始更合适 存入的数组元素要加1
for (var i = 0; i < 10; i++) {
    arr[i] = i + 1;
}
console.log(arr);
```

六、筛选数组中的元素

```js
// 将数组[2,0,6,1,77,0,52,0,25,7]中大于等于10的元素选出来，放入新数组

// 方法1：
var arr = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
var newArr = [];  // 声明一个空数组 用来存放新数据
var j = 0;
for (var i = 0; i < arr.length; i++) {
    if (arr[i] >= 10) {
        //新数组索引号从0开始 依次递增
        newArr[j] = arr[i];
        j++;
    }
}
console.log(newArr);  // [77,52,25]

// 方法2:
var arr = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
var newArr = []; 
for (var i = 0; i < arr.length; i++) {
    if (arr[i] >= 10) {
        // 刚开始 newArr.length 的长度就是0
        newArr[newArr.length] = arr[i];
    }
}
console.log(newArr);  // [77,52,25]
```

七、删除指定数组元素

```js
// 将数组 [2,0,6,1,77,0,52,0,25,7]中的0去掉后，形成一个不包含0的新数组

var arr = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
var newArr = [];
for (var i = 0; i < arr.length; i++) {
    if (arr[i] != 0) {
        // 刚开始 newArr.length 的长度就是0
        newArr[newArr.length] = arr[i];
    }
}
console.log(newArr);  // [2, 6, 1, 77, 52, 25, 7]
```

八、翻转数组

```js
// 将数组 ['red','green','blue','pink','purple','hotpink']的内容反过来存放

var arr = ['red', 'green', 'blue', 'pink'];
var newArr = [];
// 采取递减的方式 i--
for (var i = arr.length - 1; i >= 0; i--) {
    newArr[newArr.length] = arr[i];
}
console.log(newArr);

// 交换两个变量
var num1 = 'red';
var num2 = 'pink';
var temp;
temp = num1;
num1 = num2;
num2 = temp;
console.log(num1, num2);  // pink red
```

九、数组冒泡排序  
- 把一系列数据按照顺序（从大到小或从小到大）排列显示
- 重复走访要排序的数列，一次比较两个元素，如果他们的顺序错误就把他们交换过来

![ff6bea9a471719e593fcade19b20498](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220922/ff6bea9a471719e593fcade19b20498.3yapd9m2zpq0.webp)

```js
// 数组 [4,1,2,3,5]按照从小到大排序
var arr = [4, 1, 2, 3, 5];
// 外层循环管 趟数
for (var i = 0; i <= arr.length - 1; i++) { 
    // 里层循环管 每一趟的交换次数
    for (var j = 0; j <= arr.length - i - 1; j++) {
        //内部交换2个变量的值 前一个和后面一个数组元素相比较
        // if (arr[j] < arr[j + 1]) 从大到小排
        if (arr[j] > arr[j + 1]) {
            var temp = arr[j];
            arr[j] = arr[j + 1];
            arr[j + 1] = temp;
        }
    }
}
console.log(arr);  // [1,2,3,4,5]
```

### 函数
- 函数就是封装了一段可以被重复执行调用的代码块 
- 目的：实现大量代码的重复使用

#### 函数的使用
一、分两步：   
1、`声明函数` 2、`调用函数`

```js
// 声明函数
function 函数名(形参1,形参2……){
    //函数体代码;
    return 需要返回的结果；
}
函数名(实参1,实参2……);  // 调用函数

// 注意：function关键字 全小写 
// 函数不调用就不执行  函数名一般是动词 比如getSum
// 调用函数一定要加小括号
```

二、函数的两种声明方式  

```js
// 1、利用函数关键字 自定义命名函数
function getSums(){

}
getSums()

// 2、函数表达式（匿名函数）
var fun = function (aru){
    console.log(aru); 
}
fun('pink老师');
// 这里 fun是变量名 不是函数名
// 函数表达式声明方式 和声明变量差不多，只不过变量里面存的是值 函数表达式里面存的是函数
// 函数表达式也可以进行传递参数
```

#### 函数的参数

- 利用函数的参数实现函数重复不同的代码
- 函数内部值不确定时，可以通过参数在`调用函数时传递`不同的值进去

```js
// 在声明函数的小括号里是 形参  形式上的参数
function 函数名(形参1,形参2……){
    //函数体代码;
}
函数名(实参1,实参2……);  // 在函数调用的小括号里是 实参  实际的参数

// 形参：并不知道是什么
// 实参：实际的参数，实参是要传递给形参的
// js中形参的默认值是undefined


//例子1  利用函数求任意两个数的和
function getSums(num1, num2) {
    console.log(num1 + num2);
}
//尽量让实参个数和形参个数 相匹配
getSums(6, 10);  // 16  实参个数等于形参个数 正常输出结果
getSums(2);  // NaN  实参数小于形参数 输出NaN
getSums(1,2,7);  // 3   实参数大于形参数 取形参个数 即也正常输出结果


//例子2  利用函数求任意两个数之间的和
function getSums(start, end) {
    var sum = 0;
    for (var i = start; i <= end; i++) {
        sum+=i;
    }
    console.log(sum);
}
getSums(1, 10); //50
getSums(1, 100);  //5050
// 先调用 将实参传递给形参 再执行
//形参可以看作是不用声明的变量
```

#### 函数的返回值
- 函数只实现某种功能，最终结果需要返回给函数的调用者，通过return实现
- 函数遇到return，就把结果返回给函数的调用者，即相等于实现 函数名( )=return

```js
function 函数名(){
    return 需要返回的结果；
}
函数名();  


// 例子1  求任意两个数的和
function getSums(num1, num2) {
    return num1 + num2;
    //return [num1 - num2, num1 * num2, num1 / num2]; //返回的是一个数组
}
var re = getSums(6, 10);
console.log(re); // 16

// 例子2  求两个数的最大值
//方法1：
function getMax(num1, num2) {
    if (num1 > num2) {
        return num1;
    } else {
        return num2;
    }
}
console.log(getMax(8, 10)); // 10

//方法2： 用三元表达式
function getMax(num1, num2) {
    return num1 > num2 ? num1 : num2;
}
console.log(getMax(8, 10));  // 10

//例子3  求数组[5,2,99,101,67,77]中的最大值
function getArrMax(arr) {  // arr接收一个数组
    var max = arr[0];
    for (var i = 1; i < arr.length; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    return max;
}
// 在实际开发中，经常用一个变量来接收 函数的返回值
var re = getArrMax([5, 2, 99, 101, 67, 77]);
console.log(re);  // 101
```

```js
// 函数返回值注意事项：
// 1、return终止函数 后面的代码不会被执行
function getSums(num1, num2) {
    return num1 + num2;
    alert('我是不会被执行的哦');  // return 后面的代码不会执行
}
var re = getSums(1, 3); 
console.log(re);  // 4

// 2、return只能返回一个值
function fn(num1, num2) {
    return num1, num2; // 返回的结果是 最后一个值
}
console.log(fn(6, 8));  // 8

// 3、函数有return 则返回return后面的值； 没有return 则返回undefined
function fn1() {
    return 666; 
}
console.log(fn1());  // 666


function fn2() {

}
console.log(fn2());  // undefined
```

#### arguments的使用
- 当我们不知道有多少实参数传递的时候，可以用arguments来获取
- arguments存储了所有传递过来的实参
- 所有函数都内置了一个arguments，只有函数才有arguments对象
- arguments是一个伪数组
    - 具有length属性
    - 按照索引方式储存数据
    - 不具有真正数组的push、pop等方法

```js
// arguments存储了所有传递过来的实参
function fn() {
    console.log(arguments);
    console.log(arguments.length); //3
    console.log(arguments[1]);  //2
}
fn(1, 2, 3);

// 利用函数求任意个数的最大值
function getMax() {
    var max = arguments[0];
    for (var i = 0; i < arguments.length; i++) {
        if (arguments[i + 1] > max) {
            max = arguments[i + 1]
        }
    }
    return max;
}
console.log( getMax(11,4,88,666,20,100));
console.log( getMax(1,2,3,4,5,6));
```

#### 函数小案例

```js
// 案例1、利用函数 翻转数组
function reverse(arr) {
    var newArr = [];
    for (var i = arr.length - 1; i >= 0; i--) {
        newArr[newArr.length] = arr[i];
    }
    return newArr;
}
var arr1 = reverse(['red','blue','pink']); 
console.log(arr1); // ['pink', 'blue', 'red']
var arr2 = reverse([1, 2, 3, 4, 5, 6, 7, 8]);
console.log(arr2); // [8, 7, 6, 5, 4, 3, 2, 1]

// 案例2、利用函数 冒泡排序
function sort(arr) {
    for (var i = 0; i < arr.length - 1; i++) {
        for (var j = 0; j < arr.length - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {  // 从小到大排
                var temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
    return arr;
}
var arr1 = sort([2, 6, 1, 9]);
console.log(arr1);
var arr2 = sort([45, 67, 10, 2, 88]);
console.log(arr2);

// 案例3、利用函数 判断闰年
function isRunYear(year) {
    // 如果是闰年返回true，否则返回false
    var flag = false;
    if (year % 4 == 0 && year % 100 != 0 || year % 400 == 0){
        flag = true;
    }
    return flag;
}
console.log(isRunYear(2000)); // true
console.log(isRunYear(1999)); // false

// 案例4、函数相互调用
function backDay() {
    var year = prompt('请您输入年份：');
    // 调用了上面关于判断闰年的函数
    if (isRunYear(year)) {  
        alert('当前年份是闰年，2月份有29天');
    } else {
        alert('当前年份是平年，2月份有28天');
    }
}
backDay();
```

### 作用域
- js作用域，就是代码名字（变量）在某个范围内起作用和效果，目的是为了提高程序的可靠性，减少命名冲突
- js的作用域（es6）之前，分为：全局作用域、局部作用域
- 块级作用域（es6新增的）

```js
// 全局作用域：整个script标签 或一个单独的js文件
var num = 10;
console.log(num);

// 局部作用域：在函数内部 代码名字只在函数内部起作用和效果
function fn(){
    // 局部作用域
    var num = 20;
    console.log(num);
}
fn();
```

#### 变量的作用域
- 全局变量：
    - 在全局作用域下声明的变量，在任何地方都可以使用
    - 函数内部，没有声明只赋值的变量，属于全局变量
    - 只有浏览器关闭的时候才会销毁，比较占内存资源

- 局部变量：
    - 在局部作用域下声明的变量
    - 在函数内部的变量，其只在函数内部起作用
    - 函数的形参也可以看作是局部变量
    - 当程序执行完毕就会销毁，比较节约内存资源

```js
var num = 10;
console.log(num); // 10
function fn() {
    console.log(num); // 10
}
fn();


function fun() {
    var num1 = 10; // num1局部变量 只能在函数内部使用
    num2 = 20; // num2 只赋值未声明 全局变量  
    // console.log(num1, num2);  // 1o 20
}
fun();
console.log(num1); // 不起作用 报错
console.log(num2); // 20
```

#### 作用域链
- 内部函数访问外部函数的变量，采取的是链式查找的方式来决定取哪个值（就近原则）

```js
// 结果是几？
var a = 1;
function fn1() {
    var a = 2;
    var b = '22';
    fn2();
    function fn2() {
        var a = 3;
        fn3();
        function fn3() {
            var a = 4;
            // 站在目标出发，一层一层的往外查找  就近原则
            console.log(a); // 4
            console.log(b); // 22
        }
    }
}
fn1();
```

#### 预解析（解析器运行js）
一、js引擎运行js分为两步：先预解析，再代码执行  

1、把所有的 var 和function，提升到作用域的最前面  
2、剩下的，再按照代码顺序从上到下执行

二、预解析分为：变量预解析（变量提升）、函数预解析（函数提升）
- 变量提升：把所有的变量声明提升到最前面，不提升赋值
- 函数提升：把所有的函数声明提升到最前面，不调用函数

```js
// 案例
var a = 18;
f1();
function f1() {
    var b = 9;
    console.log(a);
    console.log(b);
    var a = '123';
}
// 相当于 按照下面顺序 来执行以下代码
var a;
function f1() {
    var b;
    var a;
    b = 9
    console.log(a);  // undefined
    console.log(b); // 9
    a = '123';
}
a = 18;
f1();
```

### 对象
javascript对象分为3种：自定义对象、内置对象、浏览器对象
- 自定义对象、内置对象，属于ECMAScript
- 浏览器对象属于js独有的 （DOM、BOM）

#### 自定义对象
- 对象是由`属性`、`方法`组成的。
    - 属性：事物的特征，常用名词
    - 方法：事物的行为，常用动词
- 字符串、数组、数值、函数都可以是对象
- 对象表达结构更清晰，更强大，可以用来保存更多完整的信息

##### 创建对象的三种方式 

一、字面量创建对象 （方式一）
- 对象的字面量，就是花括弧 `{ }`。{ }里面采取`键值对`的形式表示。键是属性名、值是属性值(任意类型值)
- `调用`对象的属性、方法。 小点 理解为 `的`
    - `对象名.属性名`
    - `对象名.方法名()`

```js
var obj = {}; // 创建一个空的对象

// 属性名：属性值   方法名：方法值
// 多个属性、方法之间 用逗号隔开
// 方法冒号后面跟的是一个匿名函数
var obj = {
    uname: '张三丰',
    age: 18,
    sex: '男',
    sayHi: function () {
        console.log('hi~');
    }
}
// 调用对象的属性、方法    ·理解为 的
// 对象名.属性名  或者  对象名['属性名']
console.log(obj.uname);
console.log(obj['age']);
// 对象名.方法名()  
obj.sayHi();
```

二、利用new Object创建对象 （方式二）

```js
// 利用  等号 = 赋值的形式  来添加对象的属性、方法
// 每个属性和方法之间用 分号结束
var obj = new Object();
obj.uname = '张三丰';
obj.age = 18;
obj.sex = '男';
obj.sayHi = function () {
    console.log('hi~');
}
console.log(obj.uname);
console.log(obj['sex']);
obj.sayHi();
```

三、构造函数创建对象 （方式三）

- 字面量、new Object创建对象，一次只能创建一个对象
- 构造函数，就是把对象里面相同的属性和方法抽象出来封装到函数里面

```js
function 构造函数名() {
    this.属性 = 值;
    this.方法 = function () { }
}
new 构造函数名();

// 构造函数名字 首字母要大写  泛指一大类 比如明星
// 调用构造函数 必须使用 new  对象实例 特指一个事物
// 构造函数 不需要return 就可以返回结果
// 属性和方法前面必须添加 this

// 例子：
function Star(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex = sex;
    this.sing = function (sang) {
        console.log(sang);
    }
}
// console.log(typeof ldh);
// 调用函数 返回的是一个对象
var ldh = new Star('刘德华', 18, '男');
console.log(ldh.name);
ldh.sing('笨小孩');

var ny = new Star('那英', 19, '女');
console.log(ny.age);
ny.sing('征服');
```

四、new关键字执行过程  

1、new 构造函数可以在内存中创建了一个新的空对象  
2、this 就会指向刚才创建的空对象  
3、执行构造函数里面的代码 给这个新对象添加属性和方法  
4、返回这个新对象

五、变量、函数、属性、方法的区别  

- 变量和属性
    - 都是用来存储数据的
    - 变量，单独声明并赋值，使用时直接写变量名 单独存在
    - 对象里面的变量称为属性
    - 属性，在对象里面的不需要声明，使用时必须是 对象.属性

- 函数和方法
    - 都是实现某种功能，做某件事
    - 函数，是单独声明的，调用时候， 函数名( )  单独存在
    - 对象里面的函数称为方法
    - 方法，在对象里面，不需要声明，调用的时候， 对象名.方法名( )

##### 遍历对象

```js
for (var 变量名 in 对象名){

}

// 例子
var obj = {
    name: 'pink老师',
    age: 18,
    sex: '男',
    fn: function () {}
}
// console.log(obj.name);
// console.log(obj.age);
// console.log(obj.sex);
// 我们使用 for in 里面的变量 喜欢写 k 或者 key
for (var k in obj) {
    console.log(k); // k变量 输出 得到的是 属性名
    console.log(obj[k]); // obj[k] 输出的是属性值
}
```

#### 内置对象
- js语言自带的一些对象，提供了一些常用的功能（属性和方法）
- 内置对象最大优点是，帮助我们快速开发
- js提供多个内置对象：Math、Date、Array、String 等等

##### 文档查阅指定API
学习一个内置对象的使用，只要学会常用成员的使用即可，我们通过查文档学习，可通过MDN、W3C查询

 MDN：<https://developer.mozilla.org/en-US/>

##### Math 数学对象
- Math数学对象，不是一个构造函数，所以不需要new来调用，直接使用里面的属性和方法即可
- 跟数学相关的运算（求绝对值、取整、最大值等）

```js
 Math.PI   // 圆周率
 Math.floor()  // 向下取整 往最小了取整  1.9取整 结果是1
 Math.ceil()   // 向上取整 往最大了取整  1.1取整 结果是2   
 Math.round()  // 四舍五入 注意.5特殊 往大了取  -3.5结果是-3
 Math.abs()  // 绝对值
 Math.max()  // 最大值 
 Math.min()  // 最小值
 Math.random()  // 返回一个随机的小数  0≤ 小数 <1
 

// 例子
console.log(Math.PI); // 3.141592653589793
console.log( Math.max(1,-3,99)); // 99
console.log(Math.round(-3.7)); // -4

// 案例1：得到两个数之间的随机整数 并且包含这2个整数
function getRandom(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
}
console.log(getRandom(1, 10));

// 案例2：随机点名
function getRandom(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
}
var arr = ['张三', '李四', '王二', '赵五'];
console.log(arr[getRandom(0, arr.length - 1)]);

// 案例3：猜数字游戏
//程序随机生成一个1-10之间的数字，让用户输入一个数字进行猜
function getRandom(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
}
var random = getRandom(1, 10);
while (true) {  // 死循环 后面要加 break
    var num = prompt('你来猜,请输入1-10之间的一个数字');
    if (num > random) {
        alert('你猜大了');
    } else if (num < random) {
        alert('你猜小了')
    } else {
        alert('真棒，你对了')
        break; // 退出整个循环
    }
}
```

##### Date 日期对象
- Date 日期对象，是一个构造函数，需要new来调用，所以实例化后才能使用
- 用来处理日期和时间
- 我们常用总的毫秒数来计算时间，因为它更精确；Date对象是基于1970年1月1日起计算

```js
var arr = new Array(); // 创建一个数组对象
var obj = new Object(); // 创建一个对象实例

getFullYear()  // 获取当年
getMonth() // 获取当月（0-11）
getDate() // 获取当天日期
getDay() // 获取星期几（周日0-周六6）
getHours() // 获取当前小时
getMinutes() // 获取当前分钟
getSeconds() // 获取当前秒钟

// 例子
var date = new Date();
console.log(date); // 输出现在的时钟时间
console.log(date.getFullYear()); // 返回当前年份 2022
console.log(date.getMonth() + 1); // 返回当前月份再小1个月 所以要加1
console.log(date.getDate()); // 返回当前 几号
console.log(date.getDay()); // 周日0 周六6 周一1
console.log(date.getHours()); // 时
console.log(date.getMinutes()); // 分
console.log(date.getSeconds()); // 秒


// 案例： 写一个 2022年 10月 1日 星期六
var year = date.getFullYear();
var month = date.getMonth() + 1;
var dates = date.getDate();
var day = date.getDay();
var arr = ['星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六'];
console.log('今天是' + year + '年' + month + '月' + dates + '日' + arr[day]);


// 案例：封装一个函数返回当前的时分秒 格式 00：00：00
function getTimer() {
    var time = new Date();
    var h = time.getHours();
    h = h < 10 ? '0' + h : h;  // 个位数 前面补0
    var m = time.getMinutes();
    m = m < 10 ? '0' + m : m;
    var s = time.getSeconds();
    s = s < 10 ? '0' + s : s;
    return h + ':' + m + ':' + s;
}
console.log(getTimer());
```
```js
// 时间戳: 获得Date总的毫秒数 不是当前时间的毫秒数 而是距离1970年1月1日 一共过了多少毫秒

// 方法一：通过 valueOf() 或 getTime()
var date = new Date();
console.log(date.valueOf()); // 距离1970年 总的毫秒数
// console.log(date.getTime());

// 方法二：常用方法
var date = +new Date();
console.log(date);

// 方法三：H5新增的
console.log(Date.now());


// 案例：倒计时效果 （用时间戳 来做）
// 思路 用户输入的总毫秒数 减去 现在时间总的毫秒数 得到剩余总毫秒数 再转化为 天 时 分 秒
// 转换公式：
d = parselnt(总秒数 / 60 / 60 / 24); // 计算天数 
h = parselnt(总秒数 / 60 / 60 & 24); // 计算小时
m = parselnt(总秒数 / 60 % 60); // 计算分数 
s = parselnt(总秒数 % 60); // 计算当前秒数

function countDown(time) {
    var nowTime = +new Date(); // 当前时间总毫秒数
    var inputTime = +new Date(time); // 用户输入时间的总毫秒数
    var times = (inputTime - nowTime) / 1000; // 剩余时间总的毫秒数
    var d = parseInt(times / 60 / 60 / 24);  // 天
    d = d < 10 ? '0' + d : d;

    var h = parseInt(times / 60 / 60 & 24); // 时
    h = h < 10 ? '0' + h : h;

    var m = parseInt(times / 60 % 60); // 分
    m = m < 10 ? '0' + m : m;

    var s = parseInt(times % 60); // 秒
    s = s < 10 ? '0' + s : s;

    return d + '天' + h + '时' + m + '分' + s + '秒';
}
console.log(countDown('2022-10-16 08:00:00'));
// var date = new Date();
// console.log(date); // 现在的北京时钟时间
```

##### Array 数组对象
创建数组的方式：
- 利用数组字面量 [ ]
- 利用new Array( )

```js
// 1、 创建数组 
// 方法一 利用数组字面量 []
var arr = [1, 2, 3];
console.log(arr[0]);
// 方法二 利用new Array()
var arr = new Array(); // 创建一个空数组
var arr = new Array(2); // 数组的长度为2 即数组里面有2个空的数组元素
var arr = new Array(2,3); // 等价于[2,3] 里面数组元素有2和3
console.log(arr);

// 2、检测是否为数组
// 方法一: instanceof 运算符
var arr = []; // 空数组
var obj = {}; // 空对象
console.log(arr instanceof Array); // 是数组 返回 true
console.log(obj instanceof Array); // 不是数组 返回 false

// 方法二：Array.isArray(参数)  H5新增的方法 ie9以上版本才可用
console.log(Array.isArray(arr)); // 是数组 返回 true
console.log(Array.isArray(obj)); // 不是数组 返回 false

// 3、翻转数组
function reverse(arr) {
    // if(arr instanceof Array){
    if (Array.isArray(arr)) {  // 先检测是否为数组
        var newArr = [];
        for (var i = arr.length - 1; i >= 0; i--) {
            newArr[newArr.length] = arr[i];

        }
        return newArr;

    } else {
        return 'error 这个参数要求格式必须是数组格式 如[1,2,3]'
    }
}
console.log(reverse([1, 2, 3])); // [3,2,1]
console.log(reverse(1, 2, 3)); // error 这个参数……
```

添加、删除数组元素
```js
// 添加数组元素的方法
// 1、 push() 在数组末尾 添加多个元素
var arr = [1, 2, 3];
arr.push(4,'pink');  
console.log(arr);  // [1,2,3,4,'pink']
// console.log(arr.push(4,'pink')); // 返回的是新数组的长度 5

// 2、 unshift() 在数组开头 添加多个元素
var arr = [1, 2, 3];
arr.unshift(66,88);  
console.log(arr);  // [66,88,1,2,3]
// 返回的是新数组的长度


// 删除数组元素的方法
// 3、 pop() 删除数组的最后一个元素 一次只能删除一个元素
var arr = [1, 2, 3];
arr.pop();  
console.log(arr);  // [1,2]
// 返回结果是 删除的那个元素

// 4、 shift() 删除数组的第一个元素 一次只能删除一个元素
var arr = [1, 2, 3];
arr.shift();  
console.log(arr);  // [2,3]
// 返回结果是 删除的那个元素
```

筛选数组、数组排序
```js
// 1、 筛选数组：把超过等于2000的删除 剩下数据放到新数组里面
var arr = [1500, 1200, 2000, 2100, 2800];
var newArr = [];
for (var i = 0; i < arr.length; i++) {
    if (arr[i] < 2000) {
        // newArr[newArr.length] = arr[i];
        newArr.push(arr[i]);
    }   
}
console.log(newArr); // [1500, 1200]

// 数组排序
// 2、 翻转数组
var arr = ['red','blue','green'];
arr.reverse();
console.log(arr); //  ['green', 'blue', 'red']

// 3、 冒泡排序
var arr=[13,4,77,1,7];
arr.sort(function(a,b){
    // return a-b; // 升序排序 从小到大
    return b-a; // 降序排序 从大到小
});
console.log(arr); // [77,13,7,4,1]
```

获取数组元素索引号、数组去重、数组转换为字符串
```js
// 1、 indexOf(数组元素) 
// 从前面开始查找 返回该数组元素的索引号
// 他只返回第一个满足条件的索引号
// 数组里面找不到元素 返回-1
var arr = ['red', 'blue', 'green', 'pink', 'blue'];
console.log(arr.indexOf('blue')); // 1
console.log(arr.indexOf('yellow')); // -1

// 2、 lastIndexOf(数组元素) 
// 从后面开始查找 返回该数组元素的索引号
// 他只返回第一个满足条件的索引号
// 数组里面找不到元素 返回-1
var arr = ['red', 'blue', 'green', 'pink', 'blue'];
console.log(arr.lastIndexOf('blue')); // 4
console.log(arr.lastIndexOf('yellow')); // -1


// 重要案例：数组去重
// 封装一个去重的函数 unique 独一无二的
function unique(arr) {
    var newArr = [];
    for (var i = 0; i < arr.length; i++) {
        if (newArr.indexOf(arr[i]) === -1) {
            newArr.push(arr[i]);
        }
    }
    return newArr;
}
var demo = unique(['c', 'a', 'c', 'a', 'x', 'a', 'x', 'c', 'b']);
console.log(demo); // ['c','a','x','b']


// 3、 toString()  数组转换为字符串
var arr=[1,2,3]
console.log(arr.toString()); // 1,2,3

// 4、 join('分隔符')
var arr=['red','blue','pink'];
console.log(arr.join()); // red,blue,pink  默认逗号
console.log(arr.join('*')); // red*blue*pink
console.log(arr.join('-')); // red-blue-pink

// 5、  concat()  连接两个或多个数组 不影响原数组
// 返回一个新的数组

// 6、 slice()   数组截取 slice(begin,end)
// 返回被截取项目的新数组

// 7、 splice() 数组截取splice(第几个开始，要删除个数)
// 返回被删除项目的新数组 会影响原数组
```

##### String 字符串对象
- 字符串的不可变性：重新给字符赋值，虽然内容变了，但其实是地址变了，又开辟了一个空间，之前被修改的内容仍然占有内存，所以不要大量拼接字符，会存在效率低问题

根据字符返回位置 
```js
// 根据字符返回位置 
// 1、 str.indesOf('要查找的字符',[起始的位置])
// 找不到 返回-1
var str = '改革春风吹满地，春天来了';
console.log(str.indexOf('春')); // 2
console.log(str.indexOf('春', 3)); // 从索引号是 3的位置开始往后查找  8

// 2、 lastIndexOf('要查找的字符')
// 从后往前查找，只找第一个匹配的
var str = '改革春风吹满地，春天来了';
console.log(str.lastIndexOf('春'));  // 8

// 案例：返回字符位置
// 查找字符'abcoefoxyozzopp'中所有o出现的位置以及次数
var str = 'abcoefoxyozzopp';
var index = str.indexOf('o');
var num = 0;
while (index !== -1) {
    console.log(index); // 3 6 9 12
    num++;
    index = str.indexOf('o', index + 1);
}
console.log('o出现的次数是:' + num); // 4
```

根据位置返回字符
```js
// 1、 charAt(index) 根据位置返回字符
var str = 'andy';
console.log(str.charAt(3)); //输出索引号为3的元素 y
// 遍历所有的字符
for (var i = 0; i < str.length; i++) {
    console.log(str.charAt(i));  // a n d y
}

//  2、 charCodeArt(index) 返回相应索引号的字符ASCII值 为了判断用户按下了那个键
console.log(str.charCodeAt(0)); // 索引号为0的元素的 ASCII值 a的ASCII值为 97

// 3、 str[index]  H5新增的
console.log(str[0]);  // a  获取索引号位置的元素
```

统计出现次数最多的字符
```js
// 有一个对象 来判断是否有该属性 对象['属性名']
var o = {
    age: 18
}
if (o['sex']) {
    console.log('里面有该属性');
} else {
    console.log('没有该属性');
}


// 例子：
// 判断字符串 'abcoefoxyozzopp' 出现次数最多的字符，并统计其次数
var str = 'abcoefoxyozzopp';
var o = {};
for (var i = 0; i < str.length; i++) {
    var chars = str.charAt(i); // 字符串的每一个字符
    if (o[chars]) { // o[chars] 对象o里 有chars这个属性
        o[chars]++; // 每个元素出现的次数累加
    } else {
        o[chars] = 1; // 首次出现 赋次数为 1
    }
}
console.log(o); // {a: 1, b: 1, c: 1, o: 4, e: 1, …}
// 遍历对象
var max = 0;
var ch = ''; // 建立一个空字符串
for (var k in o) {
    // k 是属性名 
    // o[k] 是属性值
    if (o[k] > max) { 
        max = o[k];
        ch = k;
    }
}
console.log(max);  // 4
console.log('最多的字符是' + ch); // o
```

字符串操作方法
```js
// 1、concat('字符串1','字符串2'……)
// 拼接字符串：连接两个或多个字符串，等效于 +  但 + 更常用
var str = 'andy';
console.log(str.concat('red')); // andyred

// 2、 substr('截取的起始位置','截取几个字符')
var str = '改革吹风吹满地';
console.log(str.substr(2, 3)); // 从索引号2开始 取3字符  吹风吹

// 3、slice ('截取的起始位置索引号','截取的结束位置索引号')
// 截取的结束位置 取不到
//  substring 基本与 slice 一样，但是不接受负值
var str = '改革吹风吹满地';
console.log(str.slice(0, 2)); // 改革

// 4、 replace('被替换的字符','替换的字符')
// 只会替换第一个字符
var str = 'aabb';
console.log(str.replace('a', 'c')); // cabb

// 例子： 把字符串 'axbxcxd' 把里面所有的 y 替换为 *
var str = 'axbxcxd';
while (str.indexOf('x') !== -1) {
    str = str.replace('x', '*');
}
console.log(str); // a*b*c*d

// 5、 split('分隔符')  字符串转换为数组 
// 前面学过 用 join 把数组转换为字符串
var str = 'red,blue,pink';
console.log(str.split(',')); //  ['red', 'blue', 'pink']
var str = 'red&blue&pink';
console.log(str.split('&')); //  ['red', 'blue', 'pink']

// 6、 toUpperCase()  转换大写 

// 7、 toLowerCase()  转换小写 
```

## DOM 
- 文档对象模型（Document Object Model 简称DOM)，是 W3C 标准规范
- DOM 就是把「文档」当做一个「对象」来看待
- DOM 的顶级对象是 document
- DOM 主要学习的是操作页面元素
- 通过DOM接口可以改变网页的内容、结构和样式

DOM 树
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221016/image.52uc29o6xm40.webp)
- 文档：一个页面就是一个文档，DOM中使用`document`表示
- 元素：页面中所有的标签都是元素，DOM中使用`element`表示
- 节点：网页中所有内容都是节点（标签、属性、文本、注释等），DOM中使用`node`表示  

DOM中，把以上内容都看作对象。

### 获取元素 （DOM方法）
想操作元素，先要获取元素。  
以下是利用 DOM 提供的方法来获取元素。逻辑性不强、繁琐，但是兼容性比采用节点操作好一些

#### 根据ID获取元素
- `document.getElementById('id名');`
- 可以获取带有 ID 的元素对象。

```html
<body>
    <div id="time">2019-9-9</div>
    <script>
        // 1. 因为我们文档页面从上往下加载，所以先得有标签 所以我们script写到标签的下面
        // 2. get 获得 element 元素 by 通过 驼峰命名法 
        // 3. 参数 id是大小写敏感的字符串
        // 4. 返回的是一个元素对象
        var timer = document.getElementById('time');
        console.log(timer);
        console.log(typeof timer);
        // 5. console.dir 打印我们返回的元素对象 更好的查看里面的属性和方法
        console.dir(timer);
    </script>
</body>
```

#### 根据标签名获取元素
1、`document.getElementsByTagName('标签名');`
- 返回带有指定标签名的对象的集合。
- 因为得到的是一个对象的集合，所以我们想要操作里面的元素就需要遍历。
得到元素对象是动态的。

2、`element.getElementsByTagName('标签名');`
- 获取某个父元素内部的指定标签名的子元素
- 父元素必须是单个对象（必须指明是哪一个对象），获取的时候不包括父元素自己

```html
<body>
    <ul>
        <li>知否知否，应是等你好久11</li>
        <li>知否知否，应是等你好久22</li>
        <li>知否知否，应是等你好久33</li>
        <li>知否知否，应是等你好久44</li>
    </ul>
    <ol id="ol">
        <li>生僻字</li>
        <li>生僻字</li>
        <li>生僻字</li>
        <li>生僻字</li>
    </ol>

    <script>
        // 1.返回的是 获取过来元素对象的集合 以伪数组的形式存储的
        var lis = document.getElementsByTagName('li');
        console.log(lis);
        console.log(lis[0]);
        // 2. 我们想要依次打印里面的元素对象我们可以采取遍历的方式
        for (var i = 0; i < lis.length; i++) {
            console.log(lis[i]);

        }
        // 3. 如果页面中只有一个li 返回的还是伪数组的形式 
        // 4. 如果页面中没有这个元素 返回的是空的伪数组的形式
        // 5. element.getElementsByTagName('标签名'); 父元素必须是指定的单个元素
        // var ol = document.getElementsByTagName('ol'); // [ol]
        // console.log(ol[0].getElementsByTagName('li'));
        var ol = document.getElementById('ol');
        console.log(ol.getElementsByTagName('li'));
    </script>
</body>
```

#### H5新增 获取元素方式
1、`document.getElementsByClassName('类名');`
- 根据class类名返回元素对象集合

2、`document.querySelector('选择器');`       
- 根据指定选择器返回第一个元素对象
- 注意选择器需要加符号 如 .box  #nav  
- 标签名也属于选择器，不用加符号

3、`document.querySelectorAll('选择器');`
- 根据指定选择器返回所有元素对象集合
- 注意选择器需要加符号 如 .box  #nav  
- 标签名也属于选择器，不用加符号

```html
<body>
    <div class="box">盒子1</div>
    <div class="box">盒子2</div>
    <div id="nav">
        <ul>
            <li>首页</li>
            <li>产品</li>
        </ul>
    </div>
    <script>
        // 1. getElementsByClassName 根据class类名获得某些元素集合
        var boxs = document.getElementsByClassName('box');
        console.log(boxs);
        // 2. querySelector 返回指定选择器的第一个元素对象  切记 里面的选择器需要加符号 .box  #nav
        var firstBox = document.querySelector('.box');
        console.log(firstBox);
        var nav = document.querySelector('#nav');
        console.log(nav);
        var li = document.querySelector('li');
        console.log(li);
        // 3. querySelectorAll()返回指定选择器的所有元素对象集合
        var allBox = document.querySelectorAll('.box');
        console.log(allBox);
        var lis = document.querySelectorAll('li');
        console.log(lis);
    </script>
</body>
```

#### 获取body和html元素
1、获取body 元素
- `document.body;`

2、获取html 元素
- `document.documentElement;`

```html
<body>
    <script>
        // 1.获取body 元素
        var bodyEle = document.body;
        console.log(bodyEle);
        console.dir(bodyEle);
        // 2.获取html 元素
        // var htmlEle = document.html;
        var htmlEle = document.documentElement;
        console.log(htmlEle);
    </script>
</body>
```

### 执行事件
- JavaScript 创建动态页面，而事件是可以被 JavaScript 侦测到的行为。
简单理解： 触发--- 响应机制。例如，我们可以在用户点击某按钮时产生一个 事件，然后去执行某些操作。

#### 事件三要素
1. 事件源 （谁）
2. 事件类型 （什么事件）
3. 事件处理程序 （做啥）

```html
body>
    <button id="btn">唐伯虎</button>
    <script>
        // 点击一个按钮，弹出对话框
        // 1. 事件是有三部分组成  事件源  事件类型  事件处理程序 
        //(1) 事件源 事件被触发的对象   谁  按钮
        var btn = document.getElementById('btn');
        //(2) 事件类型  如何触发 什么事件 比如鼠标点击(onclick) 还是鼠标经过 还是键盘按下
        //(3) 事件处理程序  通过一个函数赋值的方式 完成
        btn.onclick = function() {
            alert('点秋香');
        }
    </script>
</body>
```

#### 执行事件流程
1. 获取事件源
2. 注册事件（绑定事件）
3. 添加事件处理程序（采取函数赋值形式）

```html
<body>
    <div>123</div>
    <script>
        // 执行事件步骤
        // 点击div 控制台输出 我被选中了
        // 1. 获取事件源
        var div = document.querySelector('div');
        // 2.绑定事件 注册事件
        // div.onclick 
        // 3.添加事件处理程序 
        div.onclick = function() {
            console.log('我被选中了');
        }
    </script>
</body>
```

#### 注册事件（绑定事件）
元素注册事件的两种方式：传统方式、方法监听。

1、传统方式

- 利用 on 开头的事件 onclick 
- <button onclick=“alert('hi~')”></button>
- btn.onclick = function() {} 
- 特点： 注册事件的唯一性
- 同一个元素同一个事件只能设置一个处理函数，最后注册的处理函数将会覆盖前面注册的处理函数

2、方法监听

- w3c 标准 推荐方式
- `addEventListener()` 它是一个方法
- IE9 之前的 IE 不支持此方法，可使用 `attachEvent()` 代替
- 特点：同一个元素同一个事件可以注册多个监听器
- 按注册顺序依次执行

```html
<body>
    <button>传统注册事件</button>
    <button>方法监听注册事件</button>
    <button>ie9 attachEvent</button>
    <script>
        var btns = document.querySelectorAll('button');
        // 1. 传统方式注册事件
        btns[0].onclick = function() {
            alert('hi');
        }
        btns[0].onclick = function() {
                alert('hao a u');
            }
            // 2. 事件侦听注册事件 addEventListener  ie9以前的版本不支持
            // (1) 里面的事件类型是字符串 必定加引号 
            // 而且不带on   click 、mouseover 
            // (2) 同一个元素 同一个事件可以添加多个侦听器（事件处理程序）
        btns[1].addEventListener('click', function() {
            alert(22);
        })
        btns[1].addEventListener('click', function() {
                alert(33);
            })
            // 3. attachEvent  ie9以前的旧版本也支持 
            // 要带on  onclick 、onmouseover 
        btns[2].attachEvent('onclick', function() {
            alert(11);
        })
    </script>
</body>
```

#### 删除事件（解绑事件）
删除事件的两种方式：传统方式、方法监听

方法监听方式：  
1、`removeEventListener() `

2、`detachEvent()`

```html
<head>
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div>1</div>
    <div>2</div>
    <div>3</div>
    <script>
        var divs = document.querySelectorAll('div');
        divs[0].onclick = function() {
                alert(11);
                // 1. 传统方式删除事件
                divs[0].onclick = null;
            }
            // 2. removeEventListener 删除事件
        divs[1].addEventListener('click', fn) // 里面的fn 不需要调用加小括号

        function fn() {
            alert(22);
            divs[1].removeEventListener('click', fn);
        }
        // 3. detachEvent
        divs[2].attachEvent('onclick', fn1);

        function fn1() {
            alert(33);
            divs[2].detachEvent('onclick', fn1);
        }
    </script>
</body>

</html>
```

#### DOM事件流
- 事件发生时会在元素节点之间按照特定的顺序传播，这个传播过程即 DOM 事件流。

- DOM 事件流的三个阶段
1. 捕获阶段
2. 当前目标阶段
3. 冒泡阶段 

![1666252198054](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221016/1666252198054.87b5p9ooonc.webp)

```html
<head>
    <style>
        .father {
            overflow: hidden;
            width: 300px;
            height: 300px;
            margin: 100px auto;
            background-color: pink;
            text-align: center;
        }
        
        .son {
            width: 200px;
            height: 200px;
            margin: 50px;
            background-color: purple;
            line-height: 200px;
            color: #fff;
        }
    </style>
</head>

<body>
    <div class="father">
        <div class="son">son盒子</div>
    </div>
    <script>
        // dom 事件流 三个阶段
        // 1. JS 代码中只能执行捕获或者冒泡其中的一个阶段。
        // 2. onclick 和 attachEvent（ie） 只能得到冒泡阶段。
        // 3. 捕获阶段 如果addEventListener 第三个参数是 true 那么则处于捕获阶段  document -> html -> body -> father -> son
        // var son = document.querySelector('.son');
        // son.addEventListener('click', function() {
        //     alert('son');
        // }, true);
        // var father = document.querySelector('.father');
        // father.addEventListener('click', function() {
        //     alert('father');
        // }, true);
        // 4. 冒泡阶段 如果addEventListener 第三个参数是 false 或者 省略 那么则处于冒泡阶段  son -> father ->body -> html -> document
        var son = document.querySelector('.son');
        son.addEventListener('click', function() {
            alert('son');
        }, false);
        var father = document.querySelector('.father');
        father.addEventListener('click', function() {
            alert('father');
        }, false);
        document.addEventListener('click', function() {
            alert('document');
        })
    </script>
</body>
```
#### 事件对象

事件对象的使用语法：
```html
<head>
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div>123</div>
    <script>
        // 事件对象
        var div = document.querySelector('div');
        div.onclick = function(e) {
                // console.log(e);
                // console.log(window.event);
                // e = e || window.event;
                console.log(e);


            }
            // div.addEventListener('click', function(e) {
            //         console.log(e);

        //     })
        // 1. event 就是一个事件对象 写到我们侦听函数的 小括号里面 当形参来看
        // 2. 事件对象只有有了事件才会存在，它是系统给我们自动创建的，不需要我们传递参数
        // 3. 事件对象 是 我们事件的一系列相关数据的集合 跟事件相关的 比如鼠标点击里面就包含了鼠标的相关信息，鼠标坐标啊，如果是键盘事件里面就包含的键盘事件的信息 比如 判断用户按下了那个键
        // 4. 这个事件对象我们可以自己命名 比如 event 、 evt、 e
        // 5. 事件对象也有兼容性问题 ie678 通过 window.event 兼容性的写法  e = e || window.event;
    </script>
</body>
```

事件对象的常见属性和方法：

|事件对象属性方法|说明|
|:--|:--|
|e.target|返回触发事件的对象  标准|
|e.srcElement|触发事件的对象 非标准 ie6-8使用|
|e.type|返回事件的类型 比如click mouseover 不带on|
|e.cancelBubble|该属性 阻止冒泡 非标准 ie6-8使用|
|e.returnValue|该属性 阻止默认事件（默认行为）非标准 ie6-8使用 比如不让链接跳转|
|e.preventDefault|该方法 阻止默认事件（默认行为）标准 比如不让链接跳转|
|e.stopPropagation|阻止冒泡 标准|


e.target 和 this 的区别：
```html
<head>
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div>123</div>
    <ul>
        <li>abc</li>
        <li>abc</li>
        <li>abc</li>
    </ul>
    <script>
        // 常见事件对象的属性和方法
        // 1. e.target 返回的是触发事件的对象（元素）  this 返回的是绑定事件的对象（元素）
        // 区别 ： e.target 点击了那个元素，就返回那个元素 this 那个元素绑定了这个点击事件，那么就返回谁
        var div = document.querySelector('div');
        div.addEventListener('click', function(e) {
            console.log(e.target);
            console.log(this);
        })
        var ul = document.querySelector('ul');
        ul.addEventListener('click', function(e) {
                // 我们给ul 绑定了事件  那么this 就指向ul  
                console.log(this);
                console.log(e.currentTarget);

                // e.target 指向我们点击的那个对象 谁触发了这个事件 我们点击的是li e.target 指向的就是li
                console.log(e.target);

            })
            // 了解兼容性
            // div.onclick = function(e) {
            //     e = e || window.event;
            //     var target = e.target || e.srcElement;
            //     console.log(target);

        // }
        // 2. 了解 跟 this 有个非常相似的属性 currentTarget  ie678不认识
    </script>
</body>
```

事件对象阻止默认行为：
```html
<head>
    <style>

    </style>
</head>

<body>
    <div>123</div>
    <a href="http://www.baidu.com">百度</a>
    <form action="http://www.baidu.com">
        <input type="submit" value="提交" name="sub">
    </form>
    <script>
        // 常见事件对象的属性和方法
        // 1. 返回事件类型
        var div = document.querySelector('div');
        div.addEventListener('click', fn);
        div.addEventListener('mouseover', fn);
        div.addEventListener('mouseout', fn);

        function fn(e) {
            console.log(e.type);
        }
        // 2. 阻止默认行为（事件） 让链接不跳转 或者让提交按钮不提交
        var a = document.querySelector('a');
        a.addEventListener('click', function(e) {
                e.preventDefault(); //  dom 标准写法
            })
            // 3. 传统的注册方式
        a.onclick = function(e) {
            // 普通浏览器 e.preventDefault();  方法
            // e.preventDefault();
            // 低版本浏览器 ie678  returnValue  属性
            // e.returnValue;
            // 我们可以利用return false 也能阻止默认行为 没有兼容性问题 特点： return 后面的代码不执行了， 而且只限于传统的注册方式
            return false;
            alert(11);
        }
    </script>
</body>
```

#### 阻止事件冒泡
- 事件冒泡：开始时由最具体的元素接收，然后逐级向上传播到 DOM 最顶层节点。
- 事件冒泡本身的特性，会带来坏处，也会带来好处，需要我们灵活掌握。

阻止事件冒泡的两种方式：  
1. ` e.stopPropagation(); `
- 标准写法：利用事件对象里面的 stopPropagation()方法

2. ` e.cancelBubble = true;`
- 非标准写法：IE 6-8  利用事件对象 cancelBubble 属性 

```html
<head>
    <style>
        .father {
            overflow: hidden;
            width: 300px;
            height: 300px;
            margin: 100px auto;
            background-color: pink;
            text-align: center;
        }
        
        .son {
            width: 200px;
            height: 200px;
            margin: 50px;
            background-color: purple;
            line-height: 200px;
            color: #fff;
        }
    </style>
</head>

<body>
    <div class="father">
        <div class="son">son儿子</div>
    </div>
    <script>
        // 常见事件对象的属性和方法
        // 阻止冒泡  dom 推荐的标准 stopPropagation() 
        var son = document.querySelector('.son');
        son.addEventListener('click', function(e) {
            alert('son');
            e.stopPropagation(); // stop 停止  Propagation 传播
            e.cancelBubble = true; // 非标准 cancel 取消 bubble 泡泡
        }, false);

        var father = document.querySelector('.father');
        father.addEventListener('click', function() {
            alert('father');
        }, false);
        document.addEventListener('click', function() {
            alert('document');
        })
    </script>
</body>
```

封装阻止冒泡的兼容性函数
```js
  if(e && e.stopPropagation){
      e.stopPropagation();
  }else{
      window.event.cancelBubble = true;
  }
```

#### 事件委托（代理、委派）

1、事件委托也称为事件代理， 在 jQuery 里面称为事件委派。

2、事件委托的原理
- 不是每个子节点单独设置事件监听器，而是事件监听器设置在其父节点上，然后利用冒泡原理影响设置每个子节点。
- 以上案例：给 ul 注册点击事件，然后`利用事件对象的 target` 来找到当前点击的 li，因为点击 li，事件会冒泡到 ul 上， ul 有注册事件，就会触发事件监听器。

3、事件委托只操作了一次 DOM ，提高了程序的性能。

```html
<body>
    <ul>
        <li>知否知否，点我应有弹框在手！</li>
        <li>知否知否，点我应有弹框在手！</li>
        <li>知否知否，点我应有弹框在手！</li>
        <li>知否知否，点我应有弹框在手！</li>
        <li>知否知否，点我应有弹框在手！</li>
    </ul>
    <script>
        // 事件委托的核心原理：给父节点添加侦听器， 利用事件冒泡影响每一个子节点
        var ul = document.querySelector('ul');
        ul.addEventListener('click', function(e) {
            // alert('知否知否，点我应有弹框在手！');
            // e.target 这个可以得到我们点击的对象
            e.target.style.backgroundColor = 'pink';
        })
    </script>
</body>
```

#### 常用的鼠标事件

|鼠标事件|触发条件|
|:--|:--|
|onclick|鼠标点击左键触发|
|onmouseover|鼠标经过触发|
|onmouseout|鼠标离开触发|
|onfocus|获得鼠标焦点（光标）触发|
|onblur|失去鼠标焦点（光标）触发|
|onmousemove|鼠标移动触发|
|onmouseup|鼠标弹起触发|
|onmousedown|鼠标按下触发|

禁用鼠标右键菜单、禁止鼠标选中：
```html
<body>
    我是一段不愿意分享的文字
    <script>
        // 1. contextmenu 我们可以禁用右键菜单
        document.addEventListener('contextmenu', function(e) {
                e.preventDefault();
            })
        // 2. 禁止选中文字 selectstart
        document.addEventListener('selectstart', function(e) {
            e.preventDefault();
        })
    </script>
</body>
```

鼠标事件对象：
|鼠标事件对象|说明|
|:--|:--|
|e.clientX|返回鼠标相对于浏览器窗口可视区的X坐标|
|e.clientY|返回鼠标相对于浏览器窗口可视区的Y坐标|
|e.pageX|返回鼠标相对于文档页面的X坐标 IE9+支持|
|e.pageY|返回鼠标相对于文档页面的Y坐标 IE9+支持|
|e.screenX|返回鼠标相对于电脑屏幕的X坐标|
|e.screenY|返回鼠标相对于电脑屏幕的Y坐标|

```html
<head>
    <style>
        body {
            height: 3000px;
        }
    </style>
</head>

<body>
    <script>
        // 鼠标事件对象 MouseEvent
        document.addEventListener('click', function(e) {
            // 1. client 鼠标在可视区的x和y坐标
            console.log(e.clientX);
            console.log(e.clientY);
            console.log('---------------------');

            // 2. page 鼠标在页面文档的x和y坐标
            console.log(e.pageX);
            console.log(e.pageY);
            console.log('---------------------');

            // 3. screen 鼠标在电脑屏幕的x和y坐标
            console.log(e.screenX);
            console.log(e.screenY);

        })
    </script>
</body>
```

案例：跟随鼠标的天使  
思路：  
1、鼠标不断的移动，使用鼠标移动事件： mousemove  
2、在页面中移动，给document注册事件  
3、图片要移动距离，而且不占位置，我们使用绝对定位即可  
4、核心原理： 每次鼠标移动，我们都会获得最新的鼠标坐标， 把这个x和y坐标做为图片的top和left 值就可以移动图片

```html
<head>
    <style>
        img {
            position: absolute;
            top: 2px;
        }
    </style>
</head>

<body>
    <img src="images/angel.gif" alt="">
    <script>
        var pic = document.querySelector('img');
        document.addEventListener('mousemove', function(e) {
            // 1. mousemove只要我们鼠标移动1px 就会触发这个事件
            // console.log(1);
            // 2.核心原理： 每次鼠标移动，我们都会获得最新的鼠标坐标， 把这个x和y坐标做为图片的top和left 值就可以移动图片
            var x = e.pageX;
            var y = e.pageY;
            console.log('x坐标是' + x, 'y坐标是' + y);
            //3 . 千万不要忘记给left 和top 添加px 单位
            pic.style.left = x - 50 + 'px';
            pic.style.top = y - 30 + 'px';
        });
    </script>
</body>
```

#### 常用的键盘事件

|键盘事件|触发条件|
|:--|:--|
|`onkeyup`|某个按键被按下时触发|
|`onkeydown`|某个按键被按下时触发|
|onkeypress|某个按键被按下时触发 但是他不识别功能键 比如ctrl shift箭头等|

```html
<body>
    <script>
        // 常用的键盘事件
        //1. keyup 按键弹起的时候触发 
        // document.onkeyup = function() {
        //         console.log('我弹起了');
        //     }

        // 如果使用addEventListener 不需要加 on
        document.addEventListener('keyup', function() {
            console.log('我弹起了');
        })

        //3. keypress 按键按下的时候触发  不能识别功能键 比如 ctrl shift 左右箭头啊
        document.addEventListener('keypress', function() {
                console.log('我按下了press');
            })
            //2. keydown 按键按下的时候触发  能识别功能键 比如 ctrl shift 左右箭头啊
        document.addEventListener('keydown', function() {
                console.log('我按下了down');
            })
            // 4. 三个事件的执行顺序  keydown -- keypress -- keyup
    </script>
</body>
```

键盘事件对象属性
- `keyCode`属性，可以得到相应键的ASCII码值
```html
<body>
    <script>
        // 键盘事件对象中的keyCode属性可以得到相应键的ASCII码值
        // 1. 我们的keyup 和keydown事件不区分字母大小写  a 和 A 得到的都是65
        // 2. 我们的keypress 事件 区分字母大小写  a  97 和 A 得到的是65
        document.addEventListener('keyup', function(e) {
            // console.log(e);
            console.log('up:' + e.keyCode);
            // 我们可以利用keycode返回的ASCII码值来判断用户按下了那个键
            if (e.keyCode === 65) {
                alert('您按下的a键');
            } else {
                alert('您没有按下a键')
            }

        })
        document.addEventListener('keypress', function(e) {
            // console.log(e);
            console.log('press:' + e.keyCode);

        })
    </script>
</body>
```

ASCII 表：
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221016/image.2z2hkuuq6bs0.webp)

案例1：模拟京东按键输入内容  
要求：当我们按下 s 键， 光标就定位到搜索框  

```html
<body>
    <input type="text">
    <script>
        // 核心思路： 检测用户是否按下了s 键，如果按下s 键，就把光标定位到搜索框里面
        // 使用键盘事件对象里面的keyCode 判断用户按下的是否是s键
        // 搜索框获得焦点： 使用 js 里面的 focus() 方法
        var search = document.querySelector('input');
        document.addEventListener('keyup', function(e) {
            // console.log(e.keyCode);
            if (e.keyCode === 83) {
                search.focus();
            }
        })
    </script>
</body>
```

案例2：模拟京东快递单号查询  
要求：当我们在文本框中输入内容时，文本框上面自动显示大字号的内容。

```html
<head>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        .search {
            position: relative;
            width: 178px;
            margin: 100px;
        }
        
        .con {
            display: none;
            position: absolute;
            top: -40px;
            width: 171px;
            border: 1px solid rgba(0, 0, 0, .2);
            box-shadow: 0 2px 4px rgba(0, 0, 0, .2);
            padding: 5px 0;
            font-size: 18px;
            line-height: 20px;
            color: #333;
        }
        
        .con::before {
            content: '';
            width: 0;
            height: 0;
            position: absolute;
            top: 28px;
            left: 18px;
            border: 8px solid #000;
            border-style: solid dashed dashed;
            border-color: #fff transparent transparent;
        }
    </style>
</head>

<body>
    <div class="search">
        <div class="con">123</div>
        <input type="text" placeholder="请输入您的快递单号" class="jd">
    </div>
    <script>
        // 快递单号输入内容时， 上面的大号字体盒子（con）显示(这里面的字号更大）
        // 表单检测用户输入： 给表单添加键盘事件
        // 同时把快递单号里面的值（value）获取过来赋值给 con盒子（innerText）做为内容
        // 如果快递单号里面内容为空，则隐藏大号字体盒子(con)盒子
        var con = document.querySelector('.con');
        var jd_input = document.querySelector('.jd');
        jd_input.addEventListener('keyup', function() {
                // console.log('输入内容啦');
                if (this.value == '') {
                    con.style.display = 'none';
                } else {
                    con.style.display = 'block';
                    con.innerText = this.value;
                }
            })
            // 当我们失去焦点，就隐藏这个con盒子
        jd_input.addEventListener('blur', function() {
                con.style.display = 'none';
            })
            // 当我们获得焦点，就显示这个con盒子
        jd_input.addEventListener('focus', function() {
            if (this.value !== '') {
                con.style.display = 'block';
            }
        })
    </script>
</body>
```

### 操作元素（修改元素）
操作元素来改变元素里面的内容 、属性等。注意以下都是属性

#### 修改元素内容
1. `element.innerText `
2. `element.innerHTML `  比较常用

两者区别：
```html
<body>
    <div></div>
    <p>
        我是文字
        <span>123</span>
    </p>
    <script>
        // innerText 和 innerHTML的区别 
        // 1. innerText 不识别html标签 非标准  会去除空格和换行
        var div = document.querySelector('div');
        // div.innerText = '<strong>今天是：</strong> 2019';  // 不会加粗
        // 2. innerHTML 识别html标签 W3C标准 保留空格和换行的
        div.innerHTML = '<strong>今天是：</strong> 2019';
        // 这两个属性是可读写的  可以获取元素里面的内容
        var p = document.querySelector('p');
        console.log(p.innerText);
        console.log(p.innerHTML);
    </script>
</body>
```
案例：
```html
<head>
    <style>
        div,
        p {
            width: 300px;
            height: 30px;
            line-height: 30px;
            color: #fff;
            background-color: pink;
        }
    </style>
</head>

<body>
    <button>显示当前系统时间</button>
    <div>某个时间</div>
    <p>1123</p>
    <script>
        // 当我们点击了按钮，  div里面的文字会发生变化
        // 1. 获取元素 
        var btn = document.querySelector('button');
        var div = document.querySelector('div');
        // 2.注册事件
        btn.onclick = function() {
            // div.innerText = '2019-6-6';
            div.innerHTML = getDate();
        }

        function getDate() {
            var date = new Date();
            // 我们写一个 2019年 5月 1日 星期三
            var year = date.getFullYear();
            var month = date.getMonth() + 1;
            var dates = date.getDate();
            var arr = ['星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六'];
            var day = date.getDay();
            return '今天是：' + year + '年' + month + '月' + dates + '日 ' + arr[day];
        }
        // 我们元素可以不用添加事件
        var p = document.querySelector('p');
        p.innerHTML = getDate();
    </script>
</body>
```

#### 修改常见元素中的属性
src、alt、title、href、id

```html
<head>
    <style>
        img {
            width: 300px;
        }
    </style>
</head>

<body>
    <button id="ldh">刘德华</button>
    <button id="zxy">张学友</button> <br>
    <img src="images/ldh.jpg" alt="" title="刘德华">

    <script>
        // 修改元素属性  src
        // 1. 获取元素
        var ldh = document.getElementById('ldh');
        var zxy = document.getElementById('zxy');
        var img = document.querySelector('img');
        // 2. 注册事件  处理程序
        zxy.onclick = function() {
            img.src = 'images/zxy.jpg';
            img.title = '是张学友呀';
        }
        ldh.onclick = function() {
            img.src = 'images/ldh.jpg';
            img.title = '刘德华好帅呀';
        }
    </script>
</body>
```
案例：
```html
<head>
    <style>
        img {
            width: 300px;
        }
    </style>
</head>

<body>
    <img src="images/s.gif" alt="">
    <div>上午好</div>
    <script>
        // 根据系统不同时间来判断，所以需要用到日期内置对象
        // 利用多分支语句来设置不同的图片
        // 需要一个图片，并且根据时间修改图片，就需要用到操作元素src属性
        // 需要一个div元素，显示不同问候语，修改元素内容即可
        // 1.获取元素
        var img = document.querySelector('img');
        var div = document.querySelector('div');
        // 2. 得到当前的小时数
        var date = new Date();
        var h = date.getHours();
        // 3. 判断小时数改变图片和文字信息
        if (h < 12) {
            img.src = 'images/s.gif';
            div.innerHTML = '亲，上午好，好好写代码';
        } else if (h < 18) {
            img.src = 'images/x.gif';
            div.innerHTML = '亲，下午好，好好写代码';
        } else {
            img.src = 'images/w.gif';
            div.innerHTML = '亲，晚上好，好好写代码';
        }
    </script>
</body>
```

#### 修改表单元素的属性   
可以操作如下表单元素的属性：  
type、value、checked、selected、disabled

```html
<body>
    <button>按钮</button>
    <input type="text" value="输入内容">
    <script>
        // 1. 获取元素
        var btn = document.querySelector('button');
        var input = document.querySelector('input');
        // 2. 注册事件 处理程序
        btn.onclick = function() {
            // input.innerHTML = '点击了';  这个是 普通盒子 比如 div 标签里面的内容
            // 表单里面的值 文字内容是通过 value 来修改的
            input.value = '被点击了';
            // 如果想要某个表单被禁用 不能再点击； disabled 我们想要这个按钮 button禁用
            // btn.disabled = true;
            this.disabled = true;
            // this 指向的是事件函数的调用者 btn
        }
    </script>
</body>
```

案例：小眼睛 显示/隐藏密码
```html
<head>
    <style>
        .box {
            position: relative;
            width: 400px;
            border-bottom: 1px solid #ccc;
            margin: 100px auto;
        }
        
        .box input {
            width: 370px;
            height: 30px;
            border: 0;
            outline: none;
        }
        
        .box img {
            position: absolute; /* 子绝父相 定位 */
            top: 2px;
            right: 2px;
            width: 24px;
        }
    </style>
</head>

<body>
    <div class="box">
        <label for="">
            <img src="images/close.png" alt="" id="eye">
        </label>
        <input type="password" name="" id="pwd">
    </div>
    <script>
        // 1. 获取元素
        var eye = document.getElementById('eye');
        var pwd = document.getElementById('pwd');
        // 2. 注册事件 处理程序
        var flag = 0; // 一个东西 有多个不同状态 利用flag变量
        eye.onclick = function() {
            // 点击一次之后， flag 一定要变化
            if (flag == 0) {
                pwd.type = 'text'; // 文本框 可见密码
                eye.src = 'images/open.png';
                flag = 1; // 赋值操作
            } else {
                pwd.type = 'password'; // 密码框 隐藏密码
                eye.src = 'images/close.png';
                flag = 0;
            }
        }
    </script>
</body>
```

#### 修改样式属性
修改元素的大小、颜色、位置等样式。

1、`element.style.样式名 ` 

2、`element.className `  比较常用

3、区别：如果样式修改较多，采取className。样式修改少，可采取style。

```html
<head>
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
        // 1. 获取元素
        var div = document.querySelector('div');
        // 2. 注册事件 处理程序
        div.onclick = function() {
            // div.style里面的属性 采取驼峰命名法 
            this.style.backgroundColor = 'purple';
            this.style.width = '250px';
        }
    </script>
</body>
```

```html
<head>
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: pink;
        }
        
        .change {
            background-color: purple;
            color: #fff;
            font-size: 25px;
            margin-top: 100px;
        }
    </style>
</head>

<body>
    <div class="first">文本</div>
    <script>
        // 1. 使用 element.style 获得修改元素样式  如果样式比较少 或者 功能简单的情况下使用
        var test = document.querySelector('div');
        test.onclick = function() {
            // this.style.backgroundColor = 'purple';
            // this.style.color = '#fff';
            // this.style.fontSize = '25px';
            // this.style.marginTop = '100px';
            // 让我们当前元素的类名改为了 change

            // 2. 我们可以通过 修改元素的className更改元素的样式 适合于样式较多或者功能复杂的情况  更改元素的类名，会覆盖原先的类名
            // this.className = 'change';
            // 3. 如果想要保留原先的类名，我们可以这么做 多类名选择器
            this.className = 'first change'; // 类名first修改为 change
        }
    </script>
</body>
```

案例1：淘宝点击叉号关闭二维码
```html
<head>
    <style>
        .box {
            position: relative;
            width: 74px;
            height: 88px;
            border: 1px solid #ccc;
            margin: 100px auto;
            font-size: 12px;
            text-align: center;
            color: #f40;
            /* display: block; */   /* 显示 */
        }
        
        .box img {
            width: 60px;
            margin-top: 5px;
        }
        
        .close-btn {           
            position: absolute;  /* 子绝父相 定位 */
            top: -1px;
            left: -16px;
            width: 14px;
            height: 14px;
            border: 1px solid #ccc;
            line-height: 14px;
            font-family: Arial, Helvetica, sans-serif;
            cursor: pointer;
        }
    </style>
</head>

<body>
    <div class="box">
        淘宝二维码
        <img src="images/tao.png" alt="">
        <i class="close-btn">×</i>
    </div>
    <script>
        // 1. 获取元素 
        var btn = document.querySelector('.close-btn');
        var box = document.querySelector('.box');
        // 2.注册事件 程序处理
        btn.onclick = function() {
            box.style.display = 'none'; // 隐藏
        }
    </script>
</body>
```

案例2：设置精灵图背景 可利用循环来实现
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
        
        .box {
            width: 250px;
            margin: 100px auto;
        }
        
        .box li {
            float: left;
            width: 24px;
            height: 24px;
            background-color: pink;
            margin: 15px;
            background: url(images/sprite.png) no-repeat;
        }
    </style>
</head>

<body>
    <div class="box">
        <ul>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </div>
    <script>
        // 1. 获取元素 所有的小li 
        var lis = document.querySelectorAll('li');
        for (var i = 0; i < lis.length; i++) {
            // 让索引号 乘以 44 就是每个li 的背景y坐标  index就是我们的y坐标  精灵图中的小图是竖着一列放的 横坐标一样 纵坐标不一样找规律
            var index = i * 44;
            // 注意纵坐标是负的  字符串型拼接  带单位px
            lis[i].style.backgroundPosition = '0 -' + index + 'px';
        }
    </script>
</body>
```

案例3：显示隐藏文本框内容
```html
<head>
    <style>
        input {
            color: #999;
        }
    </style>
</head>

<body>
    <input type="text" value="手机">
    <script>
        // 当光标在文本框时，里面的默认文字隐藏，当光标离开文本框时，里面的文字显示。
        // 1.获取元素
        var text = document.querySelector('input');
        // 2.注册事件 获得焦点事件 onfocus 
        text.onfocus = function() {
                // console.log('得到了焦点');
                if (this.value === '手机') {
                    this.value = '';
                }
                // 获得焦点需要把文本框里面的文字颜色变黑
                this.style.color = '#333';
            }
            // 3. 注册事件 失去焦点事件 onblur
        text.onblur = function() {
            // console.log('失去了焦点');
            if (this.value === '') {
                this.value = '手机';
            }
            // 失去焦点需要把文本框里面的文字颜色变浅色
            this.style.color = '#999';
        }
    </script>
</body>
```

案例4：密码框格式提示错误信息
```html
<head>
    <style>
        div {
            width: 600px;
            margin: 100px auto;
        }
        
        .message {
            display: inline-block;  /* 行内块 */
            font-size: 12px;
            color: #999;
            background: url(images/mess.png) no-repeat left center;
            padding-left: 20px;
        }
        
        .wrong {
            color: red;
            background-image: url(images/wrong.png);
        }
        
        .right {
            color: green;
            background-image: url(images/right.png);
        }
    </style>
</head>

<body>
    <div class="register">
        <input type="password" class="ipt">
        <p class="message">请输入6~16位密码</p>
    </div>
    <script>
        // 用户如果离开密码框，里面输入个数不是6~16，则提示错误信息，否则提示输入正确信息。
        // 首先判断的事件是表单失去焦点 onblur
        // 如果输入正确则提示正确的信息颜色为绿色小图标变化
        // 如果输入不是6到16位，则提示错误信息颜色为红色 小图标变化
        // 因为里面变化样式较多，我们采取className修改样式
        // 1.获取元素
        var ipt = document.querySelector('.ipt');
        var message = document.querySelector('.message');
        //2. 注册事件 失去焦点
        ipt.onblur = function() {
            // 根据表单里面值的长度 ipt.value.length
            if (this.value.length < 6 || this.value.length > 16) {
                // console.log('错误');
                message.className = 'message wrong';
                message.innerHTML = '您输入的位数不对要求6~16位';
            } else {
                message.className = 'message right';
                message.innerHTML = '您输入的正确';
            }
        }
    </script>
</body>
```

#### 排他思想（算法）
如果有同一组元素，我们想要某一个元素实现某种样式， 需要用到循环的排他思想算法：
1. 所有元素全部清除样式（干掉其他人）
2. 给当前元素设置样式 （留下我自己）
3. 注意顺序不能颠倒，首先干掉其他人，再设置自己

```html
<body>
    <button>按钮1</button>
    <button>按钮2</button>
    <button>按钮3</button>
    <button>按钮4</button>
    <button>按钮5</button>
    <script>
        // 1. 获取所有按钮元素
        var btns = document.getElementsByTagName('button');
        // btns得到的是伪数组  里面的每一个元素 btns[i]
        for (var i = 0; i < btns.length; i++) {
            btns[i].onclick = function() {
                // (1) 我们先把所有的按钮背景颜色去掉  干掉所有人
                for (var i = 0; i < btns.length; i++) {
                    btns[i].style.backgroundColor = '';
                }
                // (2) 然后才让当前的元素背景颜色为pink 留下我自己
                this.style.backgroundColor = 'pink';
            }
        }
        //2. 首先先排除其他人，然后才设置自己的样式 这种排除其他人的思想我们成为排他思想
    </script>
</body>
```

案例1：百度换肤
```html
<head>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        body {
            background: url(images/1.jpg) no-repeat center top;
        }
        
        li {
            list-style: none;
        }
        
        .baidu {
            overflow: hidden;
            margin: 100px auto;
            background-color: #fff;
            width: 410px;
            padding-top: 3px;
        }
        
        .baidu li {
            float: left;
            margin: 0 1px;
            cursor: pointer;
        }
        
        .baidu img {
            width: 100px;
        }
    </style>
</head>

<body>
    <ul class="baidu">
        <li><img src="images/1.jpg"></li>
        <li><img src="images/2.jpg"></li>
        <li><img src="images/3.jpg"></li>
        <li><img src="images/4.jpg"></li>
    </ul>
    <script>
        // 1. 获取元素 
        var imgs = document.querySelector('.baidu').querySelectorAll('img');
        // var imgs = document.querySelectorAll('img');
        // console.log(imgs);
        // 2. 循环注册事件 
        for (var i = 0; i < imgs.length; i++) {
            imgs[i].onclick = function() {
                // this.src 就是我们点击图片的路径   images/2.jpg
                // console.log(this.src);
                // 把这个路径 this.src 给body 就可以了
                document.body.style.backgroundImage = 'url(' + this.src + ')';
            }
        }
    </script>
</body>
```

案例2：表格隔行变色
```html
<head>
    <style>
        table {
            width: 800px;
            margin: 100px auto;
            text-align: center;
            border-collapse: collapse;
            font-size: 14px;
        }
        
        thead tr {
            height: 30px;
            background-color: skyblue;
        }
        
        tbody tr {
            height: 30px;
        }
        
        tbody td {
            border-bottom: 1px solid #d7d7d7;
            font-size: 12px;
            color: blue;
        }
        
        .bg {
            background-color: pink;
        }
    </style>
</head>

<body>
    <table>
        <thead>
            <tr>
                <th>代码</th>
                <th>名称</th>
                <th>最新公布净值</th>
                <th>累计净值</th>
                <th>前单位净值</th>
                <th>净值增长率</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
        </tbody>
    </table>
    <script>
        // 1.获取元素 获取的是 tbody 里面所有的行
        var trs = document.querySelector('tbody').querySelectorAll('tr');
        // 2. 利用循环绑定注册事件
        for (var i = 0; i < trs.length; i++) {
            // 3. 鼠标经过事件 onmouseover
            trs[i].onmouseover = function() {
                    // console.log(11);
                    this.className = 'bg';
                }
                // 4. 鼠标离开事件 onmouseout
            trs[i].onmouseout = function() {
                this.className = '';
            }
        }
    </script>
</body>
```

案例3：表单全选取消全选案例
```html
<head lang="en">
    <style>
        * {
            padding: 0;
            margin: 0;
        }
        
        .wrap {
            width: 300px;
            margin: 100px auto 0;
        }
        
        table {
            border-collapse: collapse;
            border-spacing: 0;
            border: 1px solid #c0c0c0;
            width: 300px;
        }
        
        th,
        td {
            border: 1px solid #d0d0d0;
            color: #404060;
            padding: 10px;
        }
        
        th {
            background-color: #09c;
            font: bold 16px "微软雅黑";
            color: #fff;
        }
        
        td {
            font: 14px "微软雅黑";
        }
        
        tbody tr {
            background-color: #f0f0f0;
        }
        
        tbody tr:hover {
            cursor: pointer;
            background-color: #fafafa;
        }
    </style>

</head>

<body>
    <div class="wrap">
        <table>
            <thead>
                <tr>
                    <th>
                        <input type="checkbox" id="j_cbAll" />
                    </th>
                    <th>商品</th>
                    <th>价钱</th>
                </tr>
            </thead>
            <tbody id="j_tb">
                <tr>
                    <td>
                        <input type="checkbox" />
                    </td>
                    <td>iPhone8</td>
                    <td>8000</td>
                </tr>
                <tr>
                    <td>
                        <input type="checkbox" />
                    </td>
                    <td>iPad Pro</td>
                    <td>5000</td>
                </tr>
                <tr>
                    <td>
                        <input type="checkbox" />
                    </td>
                    <td>iPad Air</td>
                    <td>2000</td>
                </tr>
                <tr>
                    <td>
                        <input type="checkbox" />
                    </td>
                    <td>Apple Watch</td>
                    <td>2000</td>
                </tr>

            </tbody>
        </table>
    </div>
    <script>
        // 1. 全选和取消全选做法：  让下面所有复选框的checked属性（选中状态） 跟随 全选按钮即可
        // 获取元素
        var j_cbAll = document.getElementById('j_cbAll'); // 全选按钮
        var j_tbs = document.getElementById('j_tb').getElementsByTagName('input'); // 下面所有的复选框
        // 注册事件
        j_cbAll.onclick = function() {
                // this.checked 它可以得到当前复选框的选中状态如果是true 就是选中，如果是false 就是未选中
                console.log(this.checked);
                for (var i = 0; i < j_tbs.length; i++) {
                    j_tbs[i].checked = this.checked;
                }
            }
            // 2. 下面复选框需要全部选中， 上面全选才能选中做法： 给下面所有复选框绑定点击事件，每次点击，都要循环查看下面所有的复选框是否有没选中的，如果有一个没选中的， 上面全选就不选中。
        for (var i = 0; i < j_tbs.length; i++) {
            j_tbs[i].onclick = function() {
                // flag 控制全选按钮是否选中
                var flag = true;
                // 每次点击下面的复选框都要循环检查者4个小按钮是否全被选中
                for (var i = 0; i < j_tbs.length; i++) {
                    if (!j_tbs[i].checked) {
                        flag = false;
                        break; // 退出for循环 这样可以提高执行效率 因为只要有一个没有选中，剩下的就无需循环判断了
                    }
                }
                j_cbAll.checked = flag;
            }
        }
    </script>
</body>
```

#### 自定义属性的操作
1、获取属性值
- `element.属性`  获取内置属性值（元素本身自带的属性）
- `element.getAttribute(‘属性’)` 获得程序员自定义的属性

2、设置属性值
- `element.属性 = '值';`  设置内置属性值
- `element.setAttribute('属性', '值');`  设置自定义的属性

3、移除属性
- `element.removeAttribute('属性');`

```html
<body>
    <div id="demo" index="1" class="nav"></div>
    <script>
        var div = document.querySelector('div');
        // 1. 获取元素的属性值
        // (1) element.属性
        // 获取内置属性值（元素本身自带的属性）
        console.log(div.id); 
        //(2) element.getAttribute('属性')  get得到获取 attribute 属性的意思 我们程序员自己添加的属性我们称为自定义属性 index
        console.log(div.getAttribute('id'));
        console.log(div.getAttribute('index'));
        // 2. 设置元素属性值
        // (1) element.属性= '值';  针对设置内置属性值
        div.id = 'test';
        console.log(div.id); 
        div.className = 'navs';
        console.log(div.className); 
        // (2) element.setAttribute('属性', '值');  主要针对于自定义属性
        div.setAttribute('index', 2);
        // console.log(div.getAttribute('index'));
        div.setAttribute('class', 'footer'); // class 特殊  这里面写的就是class 不是className
        // console.log(div.className); 
        // 3 移除属性 removeAttribute(属性)    
        div.removeAttribute('index');
    </script>
</body>
```
  
案例：tab 栏切换（重点案例）  

思路：当鼠标点击上面相应的选项卡（tab），下面内容跟随变化
1. Tab栏切换有2个大的模块
2. 上的模块选项卡，点击某一个，当前这一个底色会是红色，其余不变（排他思想） 修改类名的方式
3. 下面的模块内容，会跟随上面的选项卡变化。所以下面模块变化写到点击事件里面。
4. 规律：下面的模块显示内容和上面的选项卡一一对应，相匹配。
5. 核心思路： 给上面的tab_list 里面的所有小li 添加自定义属性，属性值从0开始编号。
6. 当我们点击tab_list 里面的某个小li，让tab_con 里面对应序号的 内容显示，其余隐藏（排他思想）

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
        // 获取元素
        var tab_list = document.querySelector('.tab_list');
        var lis = tab_list.querySelectorAll('li');
        var items = document.querySelectorAll('.item');
        // for循环绑定点击事件
        for (var i = 0; i < lis.length; i++) {
            // 开始给5个小li 设置索引号 
            lis[i].setAttribute('index', i);
            lis[i].onclick = function() {
                // 1. 上的模块选项卡，点击某一个，当前这一个底色会是红色，其余不变（排他思想） 修改类名的方式

                // 干掉所有人 其余的li清除 class 这个类
                for (var i = 0; i < lis.length; i++) {
                    lis[i].className = '';
                }
                // 留下我自己 
                this.className = 'current';
                // 2. 下面的显示内容模块
                var index = this.getAttribute('index');
                console.log(index);
                // 干掉所有人 让其余的item 这些div 隐藏
                for (var i = 0; i < items.length; i++) {
                    items[i].style.display = 'none';
                }
                // 留下我自己 让对应的item 显示出来
                items[index].style.display = 'block';
            }
        }
    </script>
</body>
```

#### H5自定义属性
1. 设置H5自定义属性       
以data-index名为例，泛指起的属性名
- H5规定：自定义属性data-开头做为属性名并且赋值。
- 比如 `<div data-index="1"></div>`
- 或使用JS设置 `element.setAttribute('data-index', 2);`

2. 获取H5自定义属性  
- 兼容性获取`element.getAttribute('data-index');`
- H5新增`element.dataset.index ` 或者`element.dataset['index'] `  ie 11才开始支持

```html
<body>
    <div getTime="20" data-index="2" data-list-name="andy"></div>
    <script>
        var div = document.querySelector('div');
        // console.log(div.getTime);
        console.log(div.getAttribute('getTime'));
        div.setAttribute('data-time', 20);
        // 获取自定义属性 兼容性
        console.log(div.getAttribute('data-index'));
        console.log(div.getAttribute('data-list-name'));
        // h5新增的获取自定义属性的方法 它只能获取data-开头的
        // dataset 是一个集合里面存放了所有以data开头的自定义属性
        console.log(div.dataset);
        console.log(div.dataset.属性名);
        console.log(div.dataset['属性名']);
        // 如果自定义属性里面有多个-链接的单词，我们获取的时候采取 驼峰命名法
        console.log(div.dataset.listName);
        console.log(div.dataset['listName']);
    </script>
</body>
```

### 节点操作（查增删元素）
使用节点操作来`获取元素更简单`，逻辑性强，但是兼容性稍差。
- 节点：网页中的所有内容（标签、属性、文本、注释等），使用node来表示。所有节点均可被修改、创建、删除。

- 节点基本属性：nodeType（节点类型）、nodeName（节点名称）和nodeValue（节点值）。
    - 元素节点  nodeType  为 1
    - 属性节点  nodeType  为 2
    - 文本节点  nodeType  为 3 （文本节点包含文字、空格、换行等）
    - 在实际开发中，节点操作主要操作的是元素节点

- 把节点划分为不同的层级关系，常见的是`父子兄层级关系`

#### 父节点
- `node名.parentNode`   
- 返回的是`某节点的父节点`，注意是最近的一个父节点。如果指定的节点没有父节点则返回 null 

```html
<body>
    <!-- 节点的优点 -->
    <div>我是div</div>
    <span>我是span</span>
    <ul>
        <li>我是li</li>
        <li>我是li</li>
        <li>我是li</li>
        <li>我是li</li>
    </ul>
    <div class="demo">
        <div class="box">
            <span class="erweima">×</span>
        </div>
    </div>

    <script>
        // 1. 父节点 parentNode
        var erweima = document.querySelector('.erweima');
        // var box = document.querySelector('.box');
        // 得到的是离元素最近的父级节点(亲爸爸) 如果找不到父节点就返回为 null
        console.log(erweima.parentNode);
    </script>
</body>
```

#### 子节点
1、`parentNode.childNodes `
- 返回所有的子元素节点，包含元素、文本等等

2、`parentNode.childNode `
- 只返回子元素节点，其余节点不返回 

3、`parentNode.firstChild`   
- 返回第一个子节点，找不到则返回null。同样，也是包含所有的节点。

4、`parentNode.lastChild`    
- 返回最后一个子节点，找不到则返回null。同样，也是包含所有的节点。

5、`parentNode.firstElementChild`   
- 返回第一个子元素节点，找不到则返回null。 
- 有兼容性问题，IE9 以上才支持。

6、`parentNode.lastElementChild`    
- 返回最后一个子元素节点，找不到则返回null。  
- 有兼容性问题，IE9 以上才支持。

实际开发中，3、4、5、6不用

子元素节点：
```html
<body>
    <!-- 节点的优点 -->
    <div>我是div</div>
    <span>我是span</span>
    <ul>
        <li>我是li</li>
        <li>我是li</li>
        <li>我是li</li>
        <li>我是li</li>

    </ul>
    <ol>
        <li>我是li</li>
        <li>我是li</li>
        <li>我是li</li>
        <li>我是li</li>
    </ol>

    <div class="demo">
        <div class="box">
            <span class="erweima">×</span>
        </div>
    </div>

    <script>
        // DOM 提供的方法（API）获取
        var ul = document.querySelector('ul');
        var lis = ul.querySelectorAll('li');
        // 1. 子节点  childNodes 所有的子节点 包含 元素节点 文本节点等等
        console.log(ul.childNodes);
        console.log(ul.childNodes[0].nodeType);
        console.log(ul.childNodes[1].nodeType);
        // 2. children 获取所有的子元素节点 也是我们实际开发常用的
        console.log(ul.children);
    </script>
</body>
```

第一个和最后一个子元素节点：
```html
<body>
    <ol>
        <li>我是li1</li>
        <li>我是li2</li>
        <li>我是li3</li>
        <li>我是li4</li>
        <li>我是li5</li>
    </ol>
    <script>
        var ol = document.querySelector('ol');
        // 1. firstChild 第一个子节点 不管是文本节点还是元素节点
        console.log(ol.firstChild);
        console.log(ol.lastChild);
        // 2. firstElementChild 返回第一个子元素节点 ie9才支持
        console.log(ol.firstElementChild);
        console.log(ol.lastElementChild);
        // 3. 实际开发的写法  既没有兼容性问题又返回第一个子元素
        // 第一个子元素节点
        console.log(ol.children[0]);
        // 最后一个子元素节点
        console.log(ol.children[ol.children.length - 1]);
    </script>
</body>
```

案例：下拉菜单  
思路：  
1、导航栏里面的li 都要有鼠标经过效果，所以需要循环注册鼠标事件  
2、核心原理：当鼠标经过li 里面的 第二个孩子 ul 显示， 当鼠标离开，则ul 隐藏

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
            position: absolute;  /* 子绝父相 定位 */
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
        // 1. 获取元素
        var nav = document.querySelector('.nav');
        var lis = nav.children; // 得到4个小li
        // 2.循环注册事件
        for (var i = 0; i < lis.length; i++) {
            lis[i].onmouseover = function() {
                this.children[1].style.display = 'block';
            }
            lis[i].onmouseout = function() {
                this.children[1].style.display = 'none';
            }
        }
    </script>
</body>
```

#### 兄弟节点
1、`node.nextSibling`
- 返回当前元素的下一个兄弟元素节点，找不到则返回null。同样，也是包含所有的节点。

2、`node.previousSibling`
- 返回当前元素上一个兄弟元素节点，找不到则返回null。同样，也是包含所有的节点。

3、`node.nextElementSibling`
- 返回当前元素下一个兄弟元素节点，找不到则返回null。
- 有兼容性问题， IE9 以上才支持。 

4、`node.previousElementSibling `
- 返回当前元素上一个兄弟节点，找不到则返回null。 
- 有兼容性问题， IE9 以上才支持。

```html
<body>
    <div>我是div</div>
    <span>我是span</span>
    <script>
        var div = document.querySelector('div');
        // 1.nextSibling 下一个兄弟节点 包含元素节点或者 文本节点等等
        console.log(div.nextSibling);
        console.log(div.previousSibling);
        // 2. nextElementSibling 得到下一个兄弟元素节点
        console.log(div.nextElementSibling);
        console.log(div.previousElementSibling);
    </script>
</body>
```

#### 创建和添加节点
我们想要页面添加一个新的元素 ： 1. 创建元素 2. 添加元素

1、创建节点
- `document.createElement('tagName')`  
方法创建由 tagName 指定的 HTML 元素。因为这些元素原先不存在，是根据我们的需求动态生成的，所以我们也称为动态创建元素节点。

2、添加节点
- `node.appendChild(child) `   
方法将一个节点添加到指定父节点的子节点列表末尾。类似于 CSS 里面的 after 伪元素。

- `node.insertBefore(child, 指定元素) `   
方法将一个节点添加到父节点的指定子节点前面。类似于 CSS 里面的 before 伪元素。

```html
<body>
    <ul>
        <li>123</li>
    </ul>
    <script>
        // 1. 创建节点元素节点
        var li = document.createElement('li');
        // 2. 添加节点 node.appendChild(child)  node 父级  child 是子级 从后面追加元素  类似于数组中的push
        var ul = document.querySelector('ul');
        ul.appendChild(li);
        // 3. 添加节点 node.insertBefore(child, 指定元素);
        var lili = document.createElement('li');
        ul.insertBefore(lili, ul.children[0]);
        // 4. 我们想要页面添加一个新的元素 ： 1. 创建元素 2. 添加元素
    </script>
</body>
```

案例：简单版发布留言案例  
思路：  
1、核心思路： 点击按钮之后，就动态创建一个li，添加到ul 里面。  
2、创建li 的同时，把文本域里面的值通过li.innerHTML 赋值给 li  
3、如果想要新的留言后面显示就用 appendChild 如果想要前面显示就用insertBefore

```html
<head>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        body {
            padding: 100px;
        }
        
        textarea {
            width: 200px;
            height: 100px;
            border: 1px solid pink;
            outline: none;
            resize: none;
        }
        
        ul {
            margin-top: 50px;
        }
        
        li {
            width: 300px;
            padding: 5px;
            background-color: rgb(245, 209, 243);
            color: red;
            font-size: 14px;
            margin: 15px 0;
        }
    </style>
</head>

<body>
     <textarea name="" id=""></textarea>    <!--文本框 -->
    <button>发布</button>
    <ul>

    </ul>
    <script>
        // 1. 获取元素
        var btn = document.querySelector('button');
        var text = document.querySelector('textarea');
        var ul = document.querySelector('ul');
        // 2. 注册事件
        btn.onclick = function() {
            if (text.value == '') {
                alert('您没有输入内容');
                return false;
            } else {
                // console.log(text.value);
                // (1) 创建元素
                var li = document.createElement('li');
                // 先有li 才能赋值
                li.innerHTML = text.value;
                // (2) 添加元素
                // ul.appendChild(li);
                ul.insertBefore(li, ul.children[0]);
            }
        }
    </script>
</body>
```

#### 删除节点
- `node.removeChild(child) `  
从 DOM 中删除一个子节点，返回删除的节点。

```html
<body>
    <button>删除</button>
    <ul>
        <li>熊大</li>
        <li>熊二</li>
        <li>光头强</li>
    </ul>
    <script>
        // 1.获取元素
        var ul = document.querySelector('ul');
        var btn = document.querySelector('button');
        // 2. 删除元素  node.removeChild(child)
        // ul.removeChild(ul.children[0]);
        // 3. 点击按钮依次删除里面的孩子
        btn.onclick = function() {
            if (ul.children.length == 0) {
                this.disabled = true; // 禁用按钮
            } else {
                ul.removeChild(ul.children[0]); // 每次删除第一个
            }
        }
    </script>
</body>
```

案例：删除留言案例  
思路：    
1、当我们把文本域里面的值赋值给li 的时候，多添加一个删除的链接  
2、需要把所有的链接获取过来，当我们点击当前的链接的时候，删除当前链接所在的li  
3、阻止链接跳转需要添加 javascript:void(0); 或者  javascript:;

```html
<head>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        body {
            padding: 100px;
        }
        
        textarea {
            width: 200px;
            height: 100px;
            border: 1px solid pink;
            outline: none;
            resize: none;
        }
        
        ul {
            margin-top: 50px;
        }
        
        li {
            width: 300px;
            padding: 5px;
            background-color: rgb(245, 209, 243);
            color: red;
            font-size: 14px;
            margin: 15px 0;
        }
        
        li a {
            float: right;
        }
    </style>
</head>

<body>
    <textarea name="" id=""></textarea>
    <button>发布</button>
    <ul>

    </ul>
    <script>
        // 1. 获取元素
        var btn = document.querySelector('button');
        var text = document.querySelector('textarea');
        var ul = document.querySelector('ul');
        // 2. 注册事件
        btn.onclick = function() {
            if (text.value == '') {
                alert('您没有输入内容');
                return false;
            } else {
                // console.log(text.value);
                // (1) 创建元素
                var li = document.createElement('li');
                // 先有li 才能赋值
                li.innerHTML = text.value + "<a href='javascript:;'>删除</a>";  // 阻止链接跳转
                // (2) 添加元素
                // ul.appendChild(li);
                ul.insertBefore(li, ul.children[0]);
                // (3) 删除元素 删除的是当前链接的li  它的父亲
                var as = document.querySelectorAll('a');
                for (var i = 0; i < as.length; i++) {
                    as[i].onclick = function() {
                        // node.removeChild(child); 删除的是 li 当前a所在的li  this.parentNode;
                        ul.removeChild(this.parentNode);
                    }
                }
            }
        }
    </script>
</body>
```

#### 复制节点
- `node.cloneNode()`

```html
<body>
    <ul>
        <li>1111</li>
        <li>2</li>
        <li>3</li>
    </ul>
    <script>
        var ul = document.querySelector('ul');
        // 1. node.cloneNode(); 括号为空或者里面是false 浅拷贝 只复制标签不复制里面的内容
        // 2. node.cloneNode(true); 括号为true 深拷贝 复制标签复制里面的内容
        var lili = ul.children[0].cloneNode(true);
        ul.appendChild(lili);
    </script>
</body>
```

案例：动态生成表格  
思路：  
1、因为里面的学生数据都是动态的，我们需要js 动态生成。 这里我们模拟数据，自己定义好数据。 数据我们采取对象形式存储。  
2、所有的数据都是放到tbody里面的行里面。  
3、因为行很多，我们需要循环创建多个行（对应多少人）  
4、每个行里面又有很多单元格（对应里面的数据），我们还继续使用循环创建多个单元格，并且把数据存入里面（双重for循环）  
5、最后一列单元格是删除，需要单独创建单元格。  
6、最后添加删除操作，单击删除，可以删除当前行。

```html
<head>
    <style>
        table {
            width: 500px;
            margin: 100px auto;
            border-collapse: collapse;
            text-align: center;
        }
        
        td,
        th {
            border: 1px solid #333;
        }
        
        thead tr {
            height: 40px;
            background-color: #ccc;
        }
    </style>
</head>

<body>
    <table cellspacing="0">
        <thead>
            <tr>
                <th>姓名</th>
                <th>科目</th>
                <th>成绩</th>
                <th>操作</th>
            </tr>
        </thead>
        <tbody>

        </tbody>
    </table>
    <script>
        // 1.先去准备好学生的数据
        var datas = [{
            name: '魏璎珞',
            subject: 'JavaScript',
            score: 100
        }, {
            name: '弘历',
            subject: 'JavaScript',
            score: 98
        }, {
            name: '傅恒',
            subject: 'JavaScript',
            score: 99
        }, {
            name: '明玉',
            subject: 'JavaScript',
            score: 88
        }, {
            name: '大猪蹄子',
            subject: 'JavaScript',
            score: 0
        }];
        // 2. 往tbody 里面创建行： 有几个人（通过数组的长度）我们就创建几行
        var tbody = document.querySelector('tbody');
        for (var i = 0; i < datas.length; i++) { // 外面的for循环管行 tr
            // 1. 创建 tr行
            var tr = document.createElement('tr');
            tbody.appendChild(tr);
            // 2. 行里面创建单元格(跟数据有关系的3个单元格) td 单元格的数量取决于每个对象里面的属性个数  for循环遍历对象 datas[i]
            for (var k in datas[i]) { // 里面的for循环管列 td
                // 创建单元格 
                var td = document.createElement('td');
                // 把对象里面的属性值 datas[i][k] 给 td  
                // console.log(datas[i][k]);
                td.innerHTML = datas[i][k];
                tr.appendChild(td);
            }
            // 3. 创建有删除2个字的单元格 
            var td = document.createElement('td');
            td.innerHTML = '<a href="javascript:;">删除 </a>';
            tr.appendChild(td);

        }
        // 4. 删除操作 开始 
        var as = document.querySelectorAll('a');
        for (var i = 0; i < as.length; i++) {
            as[i].onclick = function() {
                // 点击a 删除 当前a 所在的行(链接的爸爸的爸爸)  node.removeChild(child)  
                tbody.removeChild(this.parentNode.parentNode)
            }
        }
        // for(var k in obj) {
        //     k 得到的是属性名
        //     obj[k] 得到是属性值
        // }
    </script>
</body>
```

#### 三种动态创建元素区别
1、`document.write()` (只了解)
- 直接将内容写入页面的内容流，但是文档流执行完毕，则它会导致页面全部重绘 

2、`element.innerHTML`
- 是将内容写入某个 DOM 节点，不会导致页面全部重绘
- 创建多个元素效率更高（不要拼接字符串，采取数组形式拼接），结构稍微复杂

3、`document.createElement()`
- 创建多个元素效率稍低一点点，但是结构更清晰

总结：不同浏览器下，innerHTML 效率要比 creatElement 高

### DOM 总结
关于dom操作，我们主要针对于元素的操作。主要有创建、增、删、改、查、属性操作、事件操作。

1、创建元素
- document.write
- innerHTML
- createElement

2、增加元素
- appendChild
- insertBefore

3、删除元素
- removeChild

4、修改元素
主要修改dom的元素属性，dom元素的内容、属性, 表单的值等
- 修改普通元素内容： innerHTML 、innerText
- 修改元素属性： src、href、title等
- 修改表单元素： value、type、disabled等
- 修改元素样式： style、className

5、获取查询元素
- DOM提供的API 方法：  getElementById、getElementsByTagName  古老用法 不太推荐 
- H5提供的新方法： querySelector、querySelectorAll   提倡
- 利用节点操作获取元素： 父(parentNode)、子(children)、兄(previousElementSibling、nextElementSibling)  提倡

6、自定义属性操作
- setAttribute：设置dom的属性值
- getAttribute：得到dom的属性值
- removeAttribute移除属性

7、鼠标事件操作


## BOM
- BOM（Browser Object Model）即浏览器对象模型，它提供了独立于内容而与浏览器窗口进行交互的对象，其核心对象是 window。
- BOM 缺乏标准，JavaScript 语法的标准化组织是 ECMA，DOM 的标准化组织是 W3C，BOM 最初是Netscape 浏览器标准的一部分，是浏览器厂商在各自浏览器上定义的，兼容性较差。
- 把「浏览器」当做一个「对象」来看待
- BOM 的顶级对象是 window
- BOM 学习的是浏览器窗口交互的一些对象

BOM 的构成：BOM 比 DOM 更大，它包含 DOM。
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221016/image.6vh4yt6tlws0.webp)

```html
<body>
    <script>
        // window.document.querySelector()
        var num = 10;
        console.log(num);
        console.log(window.num);

        function fn() {
            console.log(11);

        }
        fn();
        window.fn();
        // alert(11);
        // window.alert(11)
        console.dir(window);
        // var name = 10;
        console.log(window.name);
    </script>
</body>
```

### window 对象的常见事件
#### 窗口（页面）加载事件 
- `window.onload = function(){} `
- 或者 `window.addEventListener('load',function(){});`

注意：
1. 有了 window.onload 就可以把 JS 代码写到页面元素的上方，因为 onload 是等页面内容全部加载完毕，再去执行处理函数。
2. window.onload 传统注册事件方式 只能写一次，如果有多个，会以最后一个 window.onload 为准。
3. 如果使用 addEventListener 则没有限制

```html
<head>
    <script>
        // window.onload = function() {
        //     var btn = document.querySelector('button');
        //     btn.addEventListener('click', function() {
        //         alert('点击我');
        //     })
        // }
        // window.onload = function() {
        //     alert(22);
        // }
        window.addEventListener('load', function() {
            var btn = document.querySelector('button');
            btn.addEventListener('click', function() {
                alert('点击我');
            })
        })
        window.addEventListener('load', function() {

            alert(22);
        })
        document.addEventListener('DOMContentLoaded', function() {
                alert(33);
            })
            // load 等页面内容全部加载完毕，包含页面dom元素 图片 flash  css 等等
            // DOMContentLoaded 是DOM 加载完毕，不包含图片 falsh css 等就可以执行 加载速度比 load更快一些  Ie9以上才支持
            // 如果页面的图片很多的话, 从用户访问到onload触发可能需要较长的时间, 交互效果就不能实现，必然影响用户的体验，此时用 DOMContentLoaded 事件比较合适。

    </script>
</head>

<body>

    <button>点击</button>

</body>
```

#### 调整窗口大小事件
- `window.onresize = function(){}`

- `window.addEventListener('resize',function(){});`

注意：
1. 只要窗口大小发生像素变化，就会触发这个事件。
2. 我们经常利用这个事件完成响应式布局。 window.innerWidth 当前屏幕的宽度

```html
<head>
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
        window.addEventListener('load', function() {
            var div = document.querySelector('div');
            window.addEventListener('resize', function() {
                console.log(window.innerWidth);

                console.log('变化了');
                if (window.innerWidth <= 800) {
                    div.style.display = 'none';
                } else {
                    div.style.display = 'block';
                }
            })
        })
    </script>
    <div></div>
</body>
```

### 定时器
1、`setTimeout() `
- 设置一个定时器，该定时器在定时器到期后执行调用函数。（回调函数）
- 延时时间到了，就去调用这个回调函数，只调用一次 就结束了

2、`clearTimeout()`
- 取消了先前通过调用 setTimeout() 建立的定时器。
- 里面的参数就是定时器的标识符 。

3、`setInterval() ` 
- 方法重复调用一个函数，每隔这个时间，就去调用一次回调函数。

4、`clearInterval()`
- 取消了先前通过调用 setInterval()建立的定时器。
- 里面的参数就是定时器的标识符 。

5、`this`

```html
<body>
    <script>
        // 1. setTimeout 
        // 语法规范：  window.setTimeout(调用函数, 延时时间);
        // 1. 这个window在调用的时候可以省略
        // 2. 这个延时时间单位是毫秒 但是可以省略，如果省略默认的是0   1秒=10000毫秒 
        // 3. 这个调用函数可以直接写函数 还可以写 函数名 还有一个写法 '函数名()'
        // 4. 页面中可能有很多的定时器，我们经常给定时器加标识符 （名字)
        // setTimeout(function() {
        //     console.log('时间到了');

        // }, 2000);
        function callback() {
            console.log('爆炸了');

        }
        var timer1 = setTimeout(callback, 3000);
        var timer2 = setTimeout(callback, 5000);
        // setTimeout('callback()', 3000); // 我们不提倡这个写法
    </script>
</body>
```

```html
<body>
    <button>点击停止定时器</button>
    <script>
        var btn = document.querySelector('button');
        var timer = setTimeout(function() {
            console.log('爆炸了');

        }, 5000);
        btn.addEventListener('click', function() {
            clearTimeout(timer);
        })
    </script>
</body>
```

```html
<body>
    <script>
        // 1. setInterval 
        // 语法规范：  window.setInterval(调用函数, 延时时间);
        // window 可以省略
        setInterval(function() {
            console.log('继续输出');

        }, 1000);
        // 2. setTimeout  延时时间到了，就去调用这个回调函数，只调用一次 就结束了这个定时器
        // 3. setInterval  每隔这个延时时间，就去调用这个回调函数，会调用很多次，重复调用这个函数
    </script>
</body>
```

```html
<body>
    <button class="begin">开启定时器</button>
    <button class="stop">停止定时器</button>
    <script>
        var begin = document.querySelector('.begin');
        var stop = document.querySelector('.stop');
        var timer = null; // 全局变量  null是一个空对象
        begin.addEventListener('click', function() {
            timer = setInterval(function() {
                console.log('ni hao ma');
            }, 1000);
        })
        stop.addEventListener('click', function() {
            clearInterval(timer);
        })
    </script>
</body>
```

```html
<body>
    <button>点击</button>
    <script>
        // this 指向问题 一般情况下this的最终指向的是那个调用它的对象

        // 1. 全局作用域或者普通函数中this指向全局对象window（ 注意定时器里面的this指向window）
        console.log(this);

        function fn() {
            console.log(this);

        }
        window.fn();
        window.setTimeout(function() {
            console.log(this);

        }, 1000);
        // 2. 方法调用中谁调用this指向谁
        var o = {
            sayHi: function() {
                console.log(this); // this指向的是 o 这个对象

            }
        }
        o.sayHi();
        var btn = document.querySelector('button');
        // btn.onclick = function() {
        //     console.log(this); // this指向的是btn这个按钮对象

        // }
        btn.addEventListener('click', function() {
                console.log(this); // this指向的是btn这个按钮对象

            })
            // 3. 构造函数中this指向构造函数的实例
        function Fun() {
            console.log(this); // this 指向的是fun 实例对象

        }
        var fun = new Fun();
    </script>
</body>
```


案例1：5秒后自动关闭的广告  
核心思路：  
1、5秒之后，就把这个广告隐藏起来  
2、用定时器setTimeout  

```html
<body>
    <img src="images/ad.jpg" alt="" class="ad">
    <script>
        var ad = document.querySelector('.ad');
        setTimeout(function() {
            ad.style.display = 'none';
        }, 5000);
    </script>
</body>
```

案例2：倒计时  
思路：  
1、这个倒计时是不断变化的，因此需要定时器来自动变化（setInterval）  
2、三个黑色盒子里面分别存放时分秒  
3、三个黑色盒子利用innerHTML 放入计算的小时分钟秒数   
4、第一次执行也是间隔毫秒数，因此刚刷新页面会有空白  
5、最好采取封装函数的方式， 这样可以先调用一次这个函数，防止刚开始刷新页面有空白问题

```html
<head>
    <style>
        div {
            margin: 200px;
        }
        
        span {
            display: inline-block;
            width: 40px;
            height: 40px;
            background-color: #333;
            font-size: 20px;
            color: #fff;
            text-align: center;
            line-height: 40px;
        }
    </style>
</head>

<body>
    <div>
        <span class="hour">1</span>
        <span class="minute">2</span>
        <span class="second">3</span>
    </div>
    <script>
        // 1. 获取元素 
        var hour = document.querySelector('.hour'); // 小时的黑色盒子
        var minute = document.querySelector('.minute'); // 分钟的黑色盒子
        var second = document.querySelector('.second'); // 秒数的黑色盒子
        var inputTime = +new Date('2022-10-22 18:00:00'); // 返回的是用户输入时间总的毫秒数 将来时间
        countDown(); // 我们先调用一次这个函数，防止第一次刷新页面有空白 
        // 2. 开启定时器
        setInterval(countDown, 1000);

        function countDown() {
            var nowTime = +new Date(); // 返回的是当前时间总的毫秒数
            var times = (inputTime - nowTime) / 1000; // times是剩余时间总的秒数 
            var h = parseInt(times / 60 / 60 % 24); //时
            h = h < 10 ? '0' + h : h;
            hour.innerHTML = h; // 把剩余的小时给 小时黑色盒子

            var m = parseInt(times / 60 % 60); // 分
            m = m < 10 ? '0' + m : m;
            minute.innerHTML = m;
            
            var s = parseInt(times % 60); // 当前的秒
            s = s < 10 ? '0' + s : s;
            second.innerHTML = s;
        }
    </script>
</body>
```

案例3： 发送短信  
点击按钮后，该按钮60秒之内不能再次点击，防止重复发送短信

```html
<body>
    手机号码： <input type="number"> <button>发送</button>
    <script>
        // 按钮点击之后，会禁用 disabled 为true 
        // 同时按钮里面的内容会变化， 注意 button 里面的内容通过 innerHTML修改
        // 里面秒数是有变化的，因此需要用到定时器
        // 定义一个变量，在定时器里面，不断递减
        // 如果变量为0 说明到了时间，我们需要停止定时器，并且复原按钮初始状态
        var btn = document.querySelector('button');
        var time = 3; // 定义剩下的秒数
        btn.addEventListener('click', function() {
            btn.disabled = true;
            var timer = setInterval(function() {
                if (time == 0) {
                    // 清除定时器和复原按钮
                    clearInterval(timer);
                    btn.disabled = false;
                    btn.innerHTML = '发送';
                } else {
                    btn.innerHTML = '还剩下' + time + '秒';
                    time--;
                }
            }, 1000);
        })
    </script>
</body>
```


### JS 执行机制
#### JS 是单线程
- JavaScript 语言特点就是单线程，同一个时间只能做一件事。
- 比如我们对某个 DOM 元素进行添加和删除操作，不能同时进行。 应该先进行添加，之后再删除。
- 单线程就意味着，所有任务需要排队，前一个任务结束，才会执行后一个任务。
- 这样所导致的问题是： 如果 JS 执行的时间过长，这样就会造成页面的渲染不连贯，导致页面渲染加载阻塞的感觉。

```html
<body>
    <script>
        // 第一个问题
        // console.log(1);
        // setTimeout(function() {
        //     console.log(3);
        // }, 1000);
        // console.log(2);
        
        // 2. 第二个问题
        // console.log(1);
        // setTimeout(function() {
        //     console.log(3);
        // }, 0);
        // console.log(2);     

        // 3. 第三个问题
        console.log(1);
        document.onclick = function() {
            console.log('click');
        }
        console.log(2);
        setTimeout(function() {
            console.log(3)
        }, 3000)

    </script>
</body>
```

#### 同步和异步
先省略


### location 对象

- window 对象给我们提供了一个 location 属性用于获取或设置窗体的 URL，并且可以用于解析 URL 。 因为这个属性返回的是一个对象，所以我们将这个属性也称为 location 对象。
- 完成页面之间的跳转

#### URL
- 统一资源定位符 (Uniform Resource Locator, URL) 是互联网上标准资源的地址。互联网上的每个文件都有一个唯一的 URL，它包含的信息指出文件的位置以及浏览器应该怎么处理它。

- URL 的一般语法格式为：  
    - protocol://host[:port]/path/[?query]#fragment

    - http://www.itcast.cn/index.html?name=andy&age=18#link

![1666416704876](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221016/1666416704876.7rr3fd50ruo.webp)

#### location 对象的属性

重点记住： href 和 search

|location 对象属性|返回值|
|:--|:--|
|location.href|获取或者设置整个URL|
|location.host|返回主机（域名）www.itheima.com|
|location.port|返回端口号 如果未写返回 空字符串|
|location.pathname|返回路径|
|location.search|返回参数|
|location.hash|返回片段 #后面内容常见于链接 锚点|

案例1：5秒钟之后自动跳转页面
1、利用定时器做倒计时效果  
2、时间到了，就跳转页面。 使用 location.href

```html
<body>
    <button>点击</button>
    <div></div>
    <script>
        var btn = document.querySelector('button');
        var div = document.querySelector('div');
        btn.addEventListener('click', function() {
            // console.log(location.href);
            location.href = 'http://www.itcast.cn';
        })
        var timer = 5;
        setInterval(function() {
            if (timer == 0) {
                location.href = 'http://www.itcast.cn';
            } else {
                div.innerHTML = '您将在' + timer + '秒钟之后跳转到首页';
                timer--;
            }
        }, 1000);
    </script>
</body>
```

案例2：获取 URL 参数数据  
主要练习数据在不同页面中的传递。  

```html
<!-- 思路：  
1、第一个登录页面，里面有提交表单， action 提交到 index.html页面  
2、第二个页面，可以使用第一个页面的参数，这样实现了一个数据不同页面之间的传递效果  
3、第二个页面之所以可以使用第一个页面的数据，是利用了URL 里面的 location.search参数  
4、在第二个页面中，需要把这个参数提取。  
5、第一步去掉？  利用 substr   
6、第二步 利用=号分割 键 和 值     split(‘=‘)  
7、第一个数组就是键   第二个数组就是值 
-->

<!--  index.html 文档中 -->
<body>
    <div></div>
    <script>
        console.log(location.search); // ?uname=andy
        // 1.先去掉？  substr('起始的位置'，截取几个字符);
        var params = location.search.substr(1); // uname=andy
        console.log(params);
        // 2. 利用=把字符串分割为数组 split('=');
        var arr = params.split('=');
        console.log(arr); // ["uname", "ANDY"]
        var div = document.querySelector('div');
        // 3.把数据写入div中
        div.innerHTML = arr[1] + '欢迎您';
    </script>
</body>

<!-- login.html 文档中 -->
// 
<body>
    <form action="index(1).html">
        用户名： <input type="text" name="uname">
        <input type="submit" value="登录">
    </form>
</body>
```

#### location 对象的方法
|location 对象方法|返回值|
|:--|:--|
|location.assign|跟href一样 可以跳转页面（也称为重定向页面）|
|location.replace|替换当前页面，因为不记录历史，所以不能后退页面|
|location.reload|重新加载页面，相当于刷新按钮或者f5 如果参数为true 强制刷新ctrl+f5|

```html
<body>
    <button>点击</button>
    <script>
        var btn = document.querySelector('button');
        btn.addEventListener('click', function() {
            // 记录浏览历史，所以可以实现后退功能
            // location.assign('http://www.itcast.cn');

            // 不记录浏览历史，所以不可以实现后退功能
            location.replace('http://www.itcast.cn');

            // 重新加载页面，相当于刷新按钮或者f5 如果参数为true 强制刷新ctrl+f5
            // location.reload(true);
        })
    </script>
</body>
```

### navigator 对象
- navigator 对象包含有关浏览器的信息，它有很多属性，我们最常用的是 userAgent，该属性可以返回由客户机发送服务器的 user-agent 头部的值

下面前端代码可以判断用户那个终端打开页面，实现跳转

```js
if((navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i))) {
    window.location.href = "";     //手机
 } else {
    window.location.href = "";     //电脑
 }
```

### history 对象
- window 对象给我们提供了一个 history 对象，与浏览器历史记录进行交互。该对象包含用户（在浏览器窗口中）访问过的 URL。
- history 对象一般在实际开发中比较少用，但是会在一些 OA 办公系统中见到

|history 对象方法|作用|
|:--|:--|
|back()|可以后退功能|
|forward()|前进功能|
|go(参数)|前进后退功能，参数如果是1 前进一个页面，-1后退一个页面|

案例：
```html
<!-- index.html 文档中 -->
<body>
    <a href="list.html">点击我去往列表页</a>
    <button>前进</button>
    <script>
        var btn = document.querySelector('button');
        btn.addEventListener('click', function() {
            // history.forward();
            history.go(1);
        })
    </script>
</body>

<!-- list.html文档中 -->
<body>
    <a href="index.html">点击我去往首页</a>
    <button>后退</button>
    <script>
        var btn = document.querySelector('button');
        btn.addEventListener('click', function() {
            // history.back();
            history.go(-1);
        })
    </script>
</body>
```

## 网页特效

### PC 端网页特效
#### 元素偏移量 offset 系列
- offset 翻译过来就是偏移量， 我们使用 offset 系列相关属性可以动态的得到该`元素的位置（偏移）`、大小等。

1、`element.offsetParent`  
2、`element.offsetTop`  
3、`element.offsetLeft`  
4、`element.offsetWidth`  
5、`element.offsetHeight`  

注意： 返回的数值都不带单位

![1666498425963](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221016/1666498425963.2ns4l2o8a680.webp)
```html
<head>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        .father {
            /* position: relative; */
            width: 200px;
            height: 200px;
            background-color: pink;
            margin: 150px;
        }
        
        .son {
            width: 100px;
            height: 100px;
            background-color: purple;
            margin-left: 45px;
        }
        
        .w {
            height: 200px;
            background-color: skyblue;
            margin: 0 auto 200px;
            padding: 10px;
            border: 15px solid red;
        }
    </style>
</head>

<body>
    <div class="father">
        <div class="son"></div>
    </div>
    <div class="w"></div>
    <script>
        // offset 系列
        var father = document.querySelector('.father');
        var son = document.querySelector('.son');
        // 1.可以得到元素的偏移 位置 返回的不带单位的数值   即margin值
        console.log(father.offsetTop);   
        console.log(father.offsetLeft);
        // 它以带有定位的父亲为准  如果么有父亲或者父亲没有定位 则以 body 为准
        console.log(son.offsetLeft);
        var w = document.querySelector('.w');
        // 2.可以得到元素的大小 宽度和高度 是包含padding + border + width 
        console.log(w.offsetWidth);
        console.log(w.offsetHeight);
        // 3. 返回带有定位的父亲 否则返回的是body
        console.log(son.offsetParent); // 返回带有定位的父亲 否则返回的是body
        console.log(son.parentNode); // 返回父亲 是最近一级的父亲 亲爸爸 不管父亲有没有定位
    </script>
</body>
```

offset 与 style 区别: 
 
1、offset   
- offset 可以得到任意样式表中的样式值
- offset 系列获得的数值是没有单位的
- offsetWidth 包含padding+border+width
- offsetWidth 等属性是只读属性，只能获取不能赋值
- 所以，我们想要获取元素大小位置，用offset更合适  

2、style   
- style 只能得到行内样式表中的样式值
- style.width 获得的是带有单位的字符串
- style.width 获得不包含padding和border 的值
- style.width 是可读写属性，可以获取也可以赋值
- 所以，我们想要给元素更改值，则需要用style改变

```html
<head>
    <style>
        .box {
            width: 200px;
            height: 200px;
            background-color: pink;
            padding: 10px;
        }
    </style>
</head>

<body>
    <div class="box" style="width: 200px;"></div>
    <script>
        // offset与style的区别
        var box = document.querySelector('.box');
        console.log(box.offsetWidth);
        console.log(box.style.width);
        // box.offsetWidth = '300px';
        box.style.width = '300px';
    </script>
</body>
```

案例1：获取鼠标在盒子内的坐标
```html
<head>
    <style>
        .box {
            width: 300px;
            height: 300px;
            background-color: pink;
            margin: 200px;
        }
    </style>
</head>

<body>
    <div class="box"></div>
    <script>
        // 我们在盒子内点击， 想要得到鼠标距离盒子左右的距离。
        // 首先得到鼠标在页面中的坐标（ e.pageX, e.pageY）
        // 其次得到盒子在页面中的距离(box.offsetLeft, box.offsetTop)
        // 用鼠标距离页面的坐标减去盒子在页面中的距离， 得到 鼠标在盒子内的坐标
        var box = document.querySelector('.box');
        box.addEventListener('mousemove', function(e) {
            // console.log(e.pageX);
            // console.log(e.pageY);
            // console.log(box.offsetLeft);
            var x = e.pageX - this.offsetLeft;
            var y = e.pageY - this.offsetTop;
            this.innerHTML = 'x坐标是' + x + ' y坐标是' + y;
        })
    </script>
</body>
```

案例2：模态框拖拽  
弹出框，我们也称为模态框。  
思路：  
1、点击弹出层， 会弹出模态框， 并且显示灰色半透明的遮挡层。  
2、点击关闭按钮，可以关闭模态框，并且同时关闭灰色半透明遮挡层。  
3、鼠标放到模态框最上面一行，可以按住鼠标拖拽模态框在页面中移动。  
4、鼠标松开，可以停止拖动模态框移动。  

```html
<head lang="en">
    <style>
        .login-header {
            width: 100%;
            text-align: center;
            height: 30px;
            font-size: 24px;
            line-height: 30px;
        }
        
        ul,
        li,
        ol,
        dl,
        dt,
        dd,
        div,
        p,
        span,
        h1,
        h2,
        h3,
        h4,
        h5,
        h6,
        a {
            padding: 0px;
            margin: 0px;
        }
        
        .login {
            display: none;
            width: 512px;
            height: 280px;
            position: fixed;
            border: #ebebeb solid 1px;
            left: 50%;
            top: 50%;
            background: #ffffff;
            box-shadow: 0px 0px 20px #ddd;
            z-index: 9999;
            transform: translate(-50%, -50%);
        }
        
        .login-title {
            width: 100%;
            margin: 10px 0px 0px 0px;
            text-align: center;
            line-height: 40px;
            height: 40px;
            font-size: 18px;
            position: relative;
            cursor: move;
        }
        
        .login-input-content {
            margin-top: 20px;
        }
        
        .login-button {
            width: 50%;
            margin: 30px auto 0px auto;
            line-height: 40px;
            font-size: 14px;
            border: #ebebeb 1px solid;
            text-align: center;
        }
        
        .login-bg {
            display: none;
            width: 100%;
            height: 100%;
            position: fixed;
            top: 0px;
            left: 0px;
            background: rgba(0, 0, 0, .3);
        }
        
        a {
            text-decoration: none;
            color: #000000;
        }
        
        .login-button a {
            display: block;
        }
        
        .login-input input.list-input {
            float: left;
            line-height: 35px;
            height: 35px;
            width: 350px;
            border: #ebebeb 1px solid;
            text-indent: 5px;
        }
        
        .login-input {
            overflow: hidden;
            margin: 0px 0px 20px 0px;
        }
        
        .login-input label {
            float: left;
            width: 90px;
            padding-right: 10px;
            text-align: right;
            line-height: 35px;
            height: 35px;
            font-size: 14px;
        }
        
        .login-title span {
            position: absolute;
            font-size: 12px;
            right: -20px;
            top: -30px;
            background: #ffffff;
            border: #ebebeb solid 1px;
            width: 40px;
            height: 40px;
            border-radius: 20px;
        }
    </style>
</head>

<body>
    <div class="login-header"><a id="link" href="javascript:;">点击，弹出登录框</a></div>
    <div id="login" class="login">
        <div id="title" class="login-title">登录会员
            <span><a id="closeBtn" href="javascript:void(0);" class="close-login">关闭</a></span>
        </div>
        <div class="login-input-content">
            <div class="login-input">
                <label>用户名：</label>
                <input type="text" placeholder="请输入用户名" name="info[username]" id="username" class="list-input">
            </div>
            <div class="login-input">
                <label>登录密码：</label>
                <input type="password" placeholder="请输入登录密码" name="info[password]" id="password" class="list-input">
            </div>
        </div>
        <div id="loginBtn" class="login-button"><a href="javascript:void(0);" id="login-button-submit">登录会员</a></div>
    </div>
    <!-- 遮盖层 -->
    <div id="bg" class="login-bg"></div>
    <script>
        // 1. 获取元素
        var login = document.querySelector('.login');
        var mask = document.querySelector('.login-bg');
        var link = document.querySelector('#link');
        var closeBtn = document.querySelector('#closeBtn');
        var title = document.querySelector('#title');
        // 2. 点击弹出层这个链接 link  让mask 和login 显示出来
        link.addEventListener('click', function() {
                mask.style.display = 'block';
                login.style.display = 'block';
            })
            // 3. 点击 closeBtn 就隐藏 mask 和 login 
        closeBtn.addEventListener('click', function() {
                mask.style.display = 'none';
                login.style.display = 'none';
            })
            // 4. 开始拖拽
            // (1) 当我们鼠标按下， 就获得鼠标在盒子内的坐标
        title.addEventListener('mousedown', function(e) {
            var x = e.pageX - login.offsetLeft;
            var y = e.pageY - login.offsetTop;
            // (2) 鼠标移动的时候，把鼠标在页面中的坐标，减去 鼠标在盒子内的坐标就是模态框的left和top值
            document.addEventListener('mousemove', move)

            function move(e) {
                login.style.left = e.pageX - x + 'px';
                login.style.top = e.pageY - y + 'px';
            }
            // (3) 鼠标弹起，就让鼠标移动事件移除
            document.addEventListener('mouseup', function() {
                document.removeEventListener('mousemove', move);
            })
        })
    </script>
</body>
```

案例3：仿京东放大镜
```js
window.addEventListener('load', function() {
    var preview_img = document.querySelector('.preview_img');
    var mask = document.querySelector('.mask');
    var big = document.querySelector('.big');
    // 1. 当我们鼠标经过 preview_img 就显示和隐藏 mask 遮挡层 和 big 大盒子
    preview_img.addEventListener('mouseover', function() {
        mask.style.display = 'block';
        big.style.display = 'block';
    })
    preview_img.addEventListener('mouseout', function() {
            mask.style.display = 'none';
            big.style.display = 'none';
        })
        // 2. 鼠标移动的时候，让黄色的盒子跟着鼠标来走
    preview_img.addEventListener('mousemove', function(e) {
        // (1). 先计算出鼠标在盒子内的坐标
        var x = e.pageX - this.offsetLeft;
        var y = e.pageY - this.offsetTop;
        // console.log(x, y);
        // (2) 减去盒子高度 300的一半 是 150 就是我们mask 的最终 left 和top值了
        // (3) 我们mask 移动的距离
        var maskX = x - mask.offsetWidth / 2;
        var maskY = y - mask.offsetHeight / 2;
        // (4) 如果x 坐标小于了0 就让他停在0 的位置
        // 遮挡层的最大移动距离
        var maskMax = preview_img.offsetWidth - mask.offsetWidth;
        if (maskX <= 0) {
            maskX = 0;
        } else if (maskX >= maskMax) {
            maskX = maskMax;
        }
        if (maskY <= 0) {
            maskY = 0;
        } else if (maskY >= maskMax) {
            maskY = maskMax;
        }
        mask.style.left = maskX + 'px';
        mask.style.top = maskY + 'px';
        // 3. 大图片的移动距离 = 遮挡层移动距离 * 大图片最大移动距离 / 遮挡层的最大移动距离
        // 大图
        var bigIMg = document.querySelector('.bigImg');
        // 大图片最大移动距离
        var bigMax = bigIMg.offsetWidth - big.offsetWidth;
        // 大图片的移动距离 X Y
        var bigX = maskX * bigMax / maskMax;
        var bigY = maskY * bigMax / maskMax;
        bigIMg.style.left = -bigX + 'px';
        bigIMg.style.top = -bigY + 'px';
    })
})
```

#### 元素可视区 client 系列
- client 翻译过来就是客户端，我们使用 client 系列的相关属性来获取元素可视区的相关信息。通过 client 系列的相关属性可以动态的得到该元素的边框大小、`元素大小`等。

|client 系列属性|作用|
|:--|:--|
|element.clientTop|返回元素上边框的大小|
|element.clientLeft|  返回元素左边框的大小|
|element.clientWidth| 返回自身包括padding、内容区的宽度、不含边框，返回数值不带单位|
|element.clientHeight|  返回自身包括padding、内容区的高度、不含边框，返回数值不带单位|

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221016/image.5gcg9mvkcg00.webp)

```html
<head>
    <style>
        div {
            width: 200px;
            height: 200px;
            background-color: pink;
            border: 10px solid red;
            padding: 10px;
        }
    </style>
</head>

<body>
    <div></div>
    <script>
        // client 宽度 和我们offsetWidth 最大的区别就是 不包含边框
        var div = document.querySelector('div');
        console.log(div.clientWidth);
    </script>
</body>
```

立即执行函数  (function() {})()  或者 (function(){}())  
主要作用： 创建一个独立的作用域。 避免了命名冲突问题
```html
<body>
    <script>
        // 1.立即执行函数: 不需要调用，立马能够自己执行的函数
        function fn() {
            console.log(1);

        }
        fn();
        // 2. 写法 也可以传递参数进来
        // 1.(function() {})()    或者  2. (function(){}());
        (function(a, b) {
            console.log(a + b);
            var num = 10;
        })(1, 2); // 第二个小括号可以看做是调用函数
        (function sum(a, b) {
            console.log(a + b);
            var num = 10; // 局部变量
        }(2, 3));
        // 3. 立即执行函数最大的作用就是 独立创建了一个作用域, 里面所有的变量都是局部变量 不会有命名冲突的情况
    </script>
</body>
```

下面三种情况都会刷新页面都会触发 load 事件。    
1、a标签的超链接  
2、F5或者刷新按钮（强制刷新）  
3、前进后退按钮  
- 但是 火狐中，有个特点，有个“往返缓存”，这个缓存中不仅保存着页面数据，还保存了DOM和JavaScript的状态；实际上是将整个页面都保存在了内存里。
所以此时后退按钮不能刷新页面。  
- 此时可以使用 pageshow事件来触发。，这个事件在页面显示时触发，无论页面是否来自缓存。在重新加载页面中，pageshow会在load事件触发后触发；根据事件对象中的persisted来判断是否是缓存中的页面触发的pageshow事件，注意这个事件给window添加。

```html
<head>
    <!-- <script src="flexible.js"></script> -->
</head>

<body>

    <script>
        // console.log(window.devicePixelRatio);
        window.addEventListener('pageshow', function() {
            alert(11);
        })
    </script>
    <a href="http://www.itcast.cn">链接</a>
</body>
```

案例： 淘宝 flexible.js 源码分析
```js
(function flexible(window, document) {
    // 获取的html 的根元素
    var docEl = document.documentElement
        // dpr 物理像素比
    var dpr = window.devicePixelRatio || 1

    // adjust body font size  设置我们body 的字体大小
    function setBodyFontSize() {
        // 如果页面中有body 这个元素 就设置body的字体大小
        if (document.body) {
            document.body.style.fontSize = (12 * dpr) + 'px'
        } else {
            // 如果页面中没有body 这个元素，则等着 我们页面主要的DOM元素加载完毕再去设置body
            // 的字体大小
            document.addEventListener('DOMContentLoaded', setBodyFontSize)
        }
    }
    setBodyFontSize();

    // set 1rem = viewWidth / 10    设置我们html 元素的文字大小
    function setRemUnit() {
        var rem = docEl.clientWidth / 10
        docEl.style.fontSize = rem + 'px'
    }

    setRemUnit()

    // reset rem unit on page resize  当我们页面尺寸大小发生变化的时候，要重新设置下rem 的大小
    window.addEventListener('resize', setRemUnit)
        // pageshow 是我们重新加载页面触发的事件
    window.addEventListener('pageshow', function(e) {
        // e.persisted 返回的是true 就是说如果这个页面是从缓存取过来的页面，也需要从新计算一下rem 的大小
        if (e.persisted) {
            setRemUnit()
        }
    })

    // detect 0.5px supports  有些移动端的浏览器不支持0.5像素的写法
    if (dpr >= 2) {
        var fakeBody = document.createElement('body')
        var testElement = document.createElement('div')
        testElement.style.border = '.5px solid transparent'
        fakeBody.appendChild(testElement)
        docEl.appendChild(fakeBody)
        if (testElement.offsetHeight === 1) {
            docEl.classList.add('hairlines')
        }
        docEl.removeChild(fakeBody)
    }
}(window, document))
```

#### 元素滚动 scroll 系列
- scroll 翻译过来就是滚动的，我们使用 scroll 系列的相关属性可以动态的得到该元素的大小、`滚动距离`等。

|scroll 系列属性|作用|
|:--|:--|
|element.scrollTop|返回被卷去的上侧距离，返回数值不带单位|
|element.scrollLeft|返回被卷去的左侧距离，返回数值不带单位|
|element.scrollWidth| 返回自身实际的宽度、不含边框，返回数值不带单位|
|element.scrollHeight|  返回自身实际的高度、不含边框，返回数值不带单位|

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221016/image.5x7kwvtv2ag0.webp)

```html
<head>
    <style>
        div {
            width: 200px;
            height: 200px;
            background-color: pink;
            border: 10px solid red;
            padding: 10px;
            overflow: auto;
        }
    </style>
</head>

<body>
    <div>
        我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容 我是内容
    </div>
    <script>
        // scroll 系列
        var div = document.querySelector('div');
        console.log(div.scrollHeight);
        console.log(div.clientHeight);
        // scroll滚动事件当我们滚动条发生变化会触发的事件
        div.addEventListener('scroll', function() {
            console.log(div.scrollTop);
        })
    </script>
</body>
```

页面被卷去的头部兼容性解决方案：  
- 如果浏览器的高（或宽）度不足以显示整个页面时，会自动出现滚动条。当滚动条向下滚动时，页面上面被隐藏掉的高度，我们就称为页面被卷去的头部。滚动条在滚动时会触发 onscroll 事件。

- 需要注意的是，页面被卷去的头部，有兼容性问题，因此被卷去的头部通常有如下几种写法：
    - 声明了 DTD，使用 document.documentElement.scrollTop
    - 未声明 DTD，使用  document.body.scrollTop
    - 新方法 window.pageYOffset 和 window.pageXOffset，IE9 开始支持

```js
 function getScroll() {
    return {
      left: window.pageXOffset || document.documentElement.scrollLeft || document.body.scrollLeft||0,
      top: window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop || 0
    };
 } 
使用的时候  getScroll().left
```

案例：仿淘宝固定右侧侧边栏  
1. 原先侧边栏是绝对定位
2. 当页面滚动到一定位置，侧边栏改为固定定位
3. 页面继续滚动，会让 返回顶部显示出来

思路：
- 需要用到页面滚动事件 scroll  因为是页面滚动，所以事件源是 document
- 滚动到某个位置，就是判断页面被卷去的上部值。
- 页面被卷去的头部：可以通过window.pageYOffset 获得  如果是被卷去的左侧 window.pageXOffset
- 注意，元素被卷去的头部是 element.scrollTop  , 如果是页面被卷去的头部 则是 window.pageYOffset
- 其实这个值 可以通过盒子的 offsetTop 可以得到，如果大于等于这个值，就可以让盒子固定定位了

```html
<head>
    <style>
        .slider-bar {
            position: absolute;
            left: 50%;
            top: 300px;
            margin-left: 600px;
            width: 45px;
            height: 130px;
            background-color: pink;
        }
        
        .w {
            width: 1200px;
            margin: 10px auto;
        }
        
        .header {
            height: 150px;
            background-color: purple;
        }
        
        .banner {
            height: 250px;
            background-color: skyblue;
        }
        
        .main {
            height: 1000px;
            background-color: yellowgreen;
        }
        
        span {
            display: none;
            position: absolute;
            bottom: 0;
        }
    </style>
</head>

<body>
    <div class="slider-bar">
        <span class="goBack">返回顶部</span>
    </div>
    <div class="header w">头部区域</div>
    <div class="banner w">banner区域</div>
    <div class="main w">主体部分</div>
    <script>
        //1. 获取元素
        var sliderbar = document.querySelector('.slider-bar');
        var banner = document.querySelector('.banner');
        // banner.offestTop 就是被卷去头部的大小 一定要写到滚动的外面
        var bannerTop = banner.offsetTop
            // 当我们侧边栏固定定位之后应该变化的数值
        var sliderbarTop = sliderbar.offsetTop - bannerTop;
        // 获取main 主体元素
        var main = document.querySelector('.main');
        var goBack = document.querySelector('.goBack');
        var mainTop = main.offsetTop;
        // 2. 页面滚动事件 scroll
        document.addEventListener('scroll', function() {
            // console.log(11);
            // window.pageYOffset 页面被卷去的头部
            // console.log(window.pageYOffset);
            // 3 .当我们页面被卷去的头部大于等于了 172 此时 侧边栏就要改为固定定位
            if (window.pageYOffset >= bannerTop) {
                sliderbar.style.position = 'fixed';
                sliderbar.style.top = sliderbarTop + 'px';
            } else {
                sliderbar.style.position = 'absolute';
                sliderbar.style.top = '300px';
            }
            // 4. 当我们页面滚动到main盒子，就显示 goback模块
            if (window.pageYOffset >= mainTop) {
                goBack.style.display = 'block';
            } else {
                goBack.style.display = 'none';
            }
        })
    </script>
</body>
```

mouseenter 和mouseover的区别：  
- 当鼠标移动到元素上时就会触发 mouseenter 事件
- 类似 mouseover，它们两者之间的差别是
- mouseover 鼠标经过自身盒子会触发，经过子盒子还会触发。 mouseenter  只会经过自身盒子触发
- 之所以这样，就是因为mouseenter不会冒泡
- 跟mouseenter搭配 鼠标离开 mouseleave  同样不会冒泡

```html
<head>
    <style>
        .father {
            width: 300px;
            height: 300px;
            background-color: pink;
            margin: 100px auto;
        }
        
        .son {
            width: 200px;
            height: 200px;
            background-color: purple;
        }
    </style>
</head>

<body>
    <div class="father">
        <div class="son"></div>
    </div>
    <script>
        var father = document.querySelector('.father');
        var son = document.querySelector('.son');
        father.addEventListener('mouseenter', function() {
            console.log(11);
        })
    </script>
</body>
```

#### 动画函数封装

动画实现原理：通过定时器 setInterval() 不断移动盒子位置。
```html
<head>
    <style>
        div {
            position: absolute;
            left: 0;
            width: 100px;
            height: 100px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div></div>
    <script>
        // 动画原理
        // 1. 获得盒子当前位置  
        // 2. 让盒子在当前位置加上1个移动距离
        // 3. 利用定时器不断重复这个操作
        // 4. 加一个结束定时器的条件
        // 5. 注意此元素需要添加定位， 才能使用element.style.left
        var div = document.querySelector('div');
        var timer = setInterval(function() {
            if (div.offsetLeft >= 400) {
                // 停止动画 本质是停止定时器
                clearInterval(timer);
            }
            div.style.left = div.offsetLeft + 1 + 'px';
        }, 30);
    </script>
</body>
```

动画函数简单封装：
- 注意函数需要传递2个参数，动画对象和移动到的距离。
```html
<head>
    <style>
        div {
            position: absolute;
            left: 0;
            width: 100px;
            height: 100px;
            background-color: pink;
        }
        
        span {
            position: absolute;
            left: 0;
            top: 200px;
            display: block;
            width: 150px;
            height: 150px;
            background-color: purple;
        }
    </style>
</head>

<body>
    <div></div>
    <span>夏雨荷</span>
    <script>
        // 简单动画函数封装  obj目标对象  target目标位置
        function animate(obj, target) {
            var timer = setInterval(function() {
                if (obj.offsetLeft >= target) {
                    // 停止动画 本质是停止定时器
                    clearInterval(timer);
                }
                obj.style.left = obj.offsetLeft + 1 + 'px';

            }, 30);
        }

        var div = document.querySelector('div');
        var span = document.querySelector('span');
        // 调用函数
        animate(div, 300);
        animate(span, 200);
    </script>
</body>
```

动画函数给不同元素记录不同定时器：
- 如果多个元素都使用这个动画函数，每次都要var 声明定时器。我们可以给不同的元素使用不同的定时器（自己专门用自己的定时器）。
- 核心原理：利用 JS 是一门动态语言，可以很方便的给当前对象添加属性。

```html
<head>
    <style>
        div {
            position: absolute;
            left: 0;
            width: 100px;
            height: 100px;
            background-color: pink;
        }
        
        span {
            position: absolute;
            left: 0;
            top: 200px;
            display: block;
            width: 150px;
            height: 150px;
            background-color: purple;
        }
    </style>
</head>

<body>
    <button>点击夏雨荷才走</button>
    <div></div>
    <span>夏雨荷</span>
    <script>
        // var obj = {};
        // obj.name = 'andy';
        // 简单动画函数封装obj目标对象 target 目标位置
        // 给不同的元素指定了不同的定时器
        function animate(obj, target) {
            // 当我们不断的点击按钮，这个元素的速度会越来越快，因为开启了太多的定时器
            // 解决方案就是 让我们元素只有一个定时器执行
            // 先清除以前的定时器，只保留当前的一个定时器执行
            clearInterval(obj.timer);
            obj.timer = setInterval(function() {
                if (obj.offsetLeft >= target) {
                    // 停止动画 本质是停止定时器
                    clearInterval(obj.timer);
                }
                obj.style.left = obj.offsetLeft + 1 + 'px';

            }, 30);
        }

        var div = document.querySelector('div');
        var span = document.querySelector('span');
        var btn = document.querySelector('button');
        // 调用函数
        animate(div, 300);
        btn.addEventListener('click', function() {
            animate(span, 200);
        })
    </script>
</body>
```

缓动动画原理：  
```html
<head>
    <style>
        div {
            position: absolute;
            left: 0;
            width: 100px;
            height: 100px;
            background-color: pink;
        }
        
        span {
            position: absolute;
            left: 0;
            top: 200px;
            display: block;
            width: 150px;
            height: 150px;
            background-color: purple;
        }
    </style>
</head>

<body>
    <button>点击夏雨荷才走</button>
    <span>夏雨荷</span>
    <script>
        // 缓动动画函数封装obj目标对象 target 目标位置
        // 思路：
        // 1. 让盒子每次移动的距离慢慢变小， 速度就会慢慢落下来。
        // 2. 核心算法：(目标值 - 现在的位置) / 10 做为每次移动的距离 步长
        // 3. 停止的条件是： 让当前盒子位置等于目标位置就停止定时器
        // 4、注意步长值需要取整   
        function animate(obj, target) {
            // 先清除以前的定时器，只保留当前的一个定时器执行
            clearInterval(obj.timer);
            obj.timer = setInterval(function() {
                // 步长值写到定时器的里面
                var step = (target - obj.offsetLeft) / 10;
                if (obj.offsetLeft == target) {
                    // 停止动画 本质是停止定时器
                    clearInterval(obj.timer);
                }
                // 把每次加1 这个步长值改为一个慢慢变小的值  步长公式：(目标值 - 现在的位置) / 10
                obj.style.left = obj.offsetLeft + step + 'px';

            }, 15);
        }
        var span = document.querySelector('span');
        var btn = document.querySelector('button');

        btn.addEventListener('click', function() {
                // 调用函数
                animate(span, 500);
            })
            // 匀速动画 就是 盒子是当前的位置 +  固定的值 10 
            // 缓动动画就是  盒子当前的位置 + 变化的值(目标值 - 现在的位置) / 10）
    </script>
</body>
```

动画函数多个目标值之间移动：  

- 可以让动画函数从 800 移动到 500。    
- 当我们点击按钮时候，判断步长是正值还是负值    
    1. 如果是正值，则步长 往大了取整
    2. 如果是负值，则步长 向小了取整
```html
<head>
    <style>
        div {
            position: absolute;
            left: 0;
            width: 100px;
            height: 100px;
            background-color: pink;
        }
        
        span {
            position: absolute;
            left: 0;
            top: 200px;
            display: block;
            width: 150px;
            height: 150px;
            background-color: purple;
        }
    </style>
</head>

<body>
    <button class="btn500">点击夏雨荷到500</button>
    <button class="btn800">点击夏雨荷到800</button>
    <span>夏雨荷</span>
    <script>
        // 缓动动画函数封装obj目标对象 target 目标位置
        // 思路：
        // 1. 让盒子每次移动的距离慢慢变小， 速度就会慢慢落下来。
        // 2. 核心算法：(目标值 - 现在的位置) / 10 做为每次移动的距离 步长
        // 3. 停止的条件是： 让当前盒子位置等于目标位置就停止定时器
        function animate(obj, target) {
            // 先清除以前的定时器，只保留当前的一个定时器执行
            clearInterval(obj.timer);
            obj.timer = setInterval(function() {
                // 步长值写到定时器的里面
                // 把我们步长值改为整数 不要出现小数的问题
                // var step = Math.ceil((target - obj.offsetLeft) / 10);
                var step = (target - obj.offsetLeft) / 10;
                step = step > 0 ? Math.ceil(step) : Math.floor(step);
                if (obj.offsetLeft == target) {
                    // 停止动画 本质是停止定时器
                    clearInterval(obj.timer);
                }
                // 把每次加1 这个步长值改为一个慢慢变小的值  步长公式：(目标值 - 现在的位置) / 10
                obj.style.left = obj.offsetLeft + step + 'px';

            }, 15);
        }
        var span = document.querySelector('span');
        var btn500 = document.querySelector('.btn500');
        var btn800 = document.querySelector('.btn800');

        btn500.addEventListener('click', function() {
            // 调用函数
            animate(span, 500);
        })
        btn800.addEventListener('click', function() {
                // 调用函数
                animate(span, 800);
            })
            // 匀速动画 就是 盒子是当前的位置 +  固定的值 10 
            // 缓动动画就是  盒子当前的位置 + 变化的值(目标值 - 现在的位置) / 10）
    </script>
</body>
```

动画函数添加回调函数：

- 回调函数原理：函数可以作为一个参数。将这个函数作为参数传到另一个函数里面，当那个函数执行完之后，再执行传进去的这个函数，这个过程就叫做回调。
- 回调函数写的位置：定时器结束的位置。

```html
<head>
    <style>
        div {
            position: absolute;
            left: 0;
            width: 100px;
            height: 100px;
            background-color: pink;
        }
        
        span {
            position: absolute;
            left: 0;
            top: 200px;
            display: block;
            width: 150px;
            height: 150px;
            background-color: purple;
        }
    </style>
</head>

<body>
    <button class="btn500">点击夏雨荷到500</button>
    <button class="btn800">点击夏雨荷到800</button>
    <span>夏雨荷</span>
    <script>
        // 缓动动画函数封装obj目标对象 target 目标位置
        // 思路：
        // 1. 让盒子每次移动的距离慢慢变小， 速度就会慢慢落下来。
        // 2. 核心算法：(目标值 - 现在的位置) / 10 做为每次移动的距离 步长
        // 3. 停止的条件是： 让当前盒子位置等于目标位置就停止定时器
        function animate(obj, target, callback) {
            // console.log(callback);  callback = function() {}  调用的时候 callback()

            // 先清除以前的定时器，只保留当前的一个定时器执行
            clearInterval(obj.timer);
            obj.timer = setInterval(function() {
                // 步长值写到定时器的里面
                // 把我们步长值改为整数 不要出现小数的问题
                // var step = Math.ceil((target - obj.offsetLeft) / 10);
                var step = (target - obj.offsetLeft) / 10;
                step = step > 0 ? Math.ceil(step) : Math.floor(step);
                if (obj.offsetLeft == target) {
                    // 停止动画 本质是停止定时器
                    clearInterval(obj.timer);
                    // 回调函数写到定时器结束里面
                    if (callback) {
                        // 调用函数
                        callback();
                    }
                }
                // 把每次加1 这个步长值改为一个慢慢变小的值  步长公式：(目标值 - 现在的位置) / 10
                obj.style.left = obj.offsetLeft + step + 'px';

            }, 15);
        }
        var span = document.querySelector('span');
        var btn500 = document.querySelector('.btn500');
        var btn800 = document.querySelector('.btn800');

        btn500.addEventListener('click', function() {
            // 调用函数
            animate(span, 500);
        })
        btn800.addEventListener('click', function() {
                // 调用函数
                animate(span, 800, function() {
                    // alert('你好吗');
                    span.style.backgroundColor = 'red';
                });
            })
            // 匀速动画 就是 盒子是当前的位置 +  固定的值 10 
            // 缓动动画就是  盒子当前的位置 + 变化的值(目标值 - 现在的位置) / 10）
    </script>
</body>
```

动画函数封装到单独JS文件里面:
```js
(function flexible(window, document) {
    var docEl = document.documentElement
    var dpr = window.devicePixelRatio || 1

    // adjust body font size
    function setBodyFontSize() {
        if (document.body) {
            document.body.style.fontSize = (12 * dpr) + 'px'
        } else {
            document.addEventListener('DOMContentLoaded', setBodyFontSize)
        }
    }
    setBodyFontSize();

    // set 1rem = viewWidth / 10
    function setRemUnit() {
        var rem = docEl.clientWidth / 10
        docEl.style.fontSize = rem + 'px'
    }

    setRemUnit()

    // reset rem unit on page resize
    window.addEventListener('resize', setRemUnit)
    window.addEventListener('pageshow', function(e) {
        if (e.persisted) {
            setRemUnit()
        }
    })

    // detect 0.5px supports
    if (dpr >= 2) {
        var fakeBody = document.createElement('body')
        var testElement = document.createElement('div')
        testElement.style.border = '.5px solid transparent'
        fakeBody.appendChild(testElement)
        docEl.appendChild(fakeBody)
        if (testElement.offsetHeight === 1) {
            docEl.classList.add('hairlines')
        }
        docEl.removeChild(fakeBody)
    }
}(window, document))
```

引用animate动画函数：
```html
<head>
    <style>
        .sliderbar {
            position: fixed;
            right: 0;
            bottom: 100px;
            width: 40px;
            height: 40px;
            text-align: center;
            line-height: 40px;
            cursor: pointer;
            color: #fff;
        }
        
        .con {
            position: absolute;
            left: 0;
            top: 0;
            width: 200px;
            height: 40px;
            background-color: purple;
            z-index: -1;
        }
    </style>
    <script src="animate.js"></script>
</head>

<body>
    <div class="sliderbar">
        <span>←</span>
        <div class="con">问题反馈</div>
    </div>

    <script>
        // 1. 获取元素
        var sliderbar = document.querySelector('.sliderbar');
        var con = document.querySelector('.con');
        // 当我们鼠标经过 sliderbar 就会让 con这个盒子滑动到左侧
        // 当我们鼠标离开 sliderbar 就会让 con这个盒子滑动到右侧
        sliderbar.addEventListener('mouseenter', function() {
            // animate(obj, target, callback);
            animate(con, -160, function() {
                // 当我们动画执行完毕，就把 ← 改为 →
                sliderbar.children[0].innerHTML = '→';
            });

        })
        sliderbar.addEventListener('mouseleave', function() {
            // animate(obj, target, callback);
            animate(con, 0, function() {
                sliderbar.children[0].innerHTML = '←';
            });

        })
    </script>
</body>
```

```js
// animate.js文件

function animate(obj, target, callback) {
    // console.log(callback);  callback = function() {}  调用的时候 callback()

    // 先清除以前的定时器，只保留当前的一个定时器执行
    clearInterval(obj.timer);
    obj.timer = setInterval(function() {
        // 步长值写到定时器的里面
        // 把我们步长值改为整数 不要出现小数的问题
        // var step = Math.ceil((target - obj.offsetLeft) / 10);
        var step = (target - obj.offsetLeft) / 10;
        step = step > 0 ? Math.ceil(step) : Math.floor(step);
        if (obj.offsetLeft == target) {
            // 停止动画 本质是停止定时器
            clearInterval(obj.timer);
            // 回调函数写到定时器结束里面
            // if (callback) {
            //     // 调用函数
            //     callback();
            // }
            callback && callback();
        }
        // 把每次加1 这个步长值改为一个慢慢变小的值  步长公式：(目标值 - 现在的位置) / 10
        obj.style.left = obj.offsetLeft + step + 'px';

    }, 15);
}
```

#### 常见网页特效案例

案例1：网页轮播图
```js
window.addEventListener('load', function() {
    // 1. 获取元素
    var arrow_l = document.querySelector('.arrow-l');
    var arrow_r = document.querySelector('.arrow-r');
    var focus = document.querySelector('.focus');
    var focusWidth = focus.offsetWidth;
    // 2. 鼠标经过focus 就显示隐藏左右按钮
    focus.addEventListener('mouseenter', function() {
        arrow_l.style.display = 'block';
        arrow_r.style.display = 'block';
        clearInterval(timer);
        timer = null; // 清除定时器变量
    });
    focus.addEventListener('mouseleave', function() {
        arrow_l.style.display = 'none';
        arrow_r.style.display = 'none';
        timer = setInterval(function() {
            //手动调用点击事件
            arrow_r.click();
        }, 2000);
    });
    // 3. 动态生成小圆圈  有几张图片，我就生成几个小圆圈
    var ul = focus.querySelector('ul');
    var ol = focus.querySelector('.circle');
    // console.log(ul.children.length);
    for (var i = 0; i < ul.children.length; i++) {
        // 创建一个小li 
        var li = document.createElement('li');
        // 记录当前小圆圈的索引号 通过自定义属性来做 
        li.setAttribute('index', i);
        // 把小li插入到ol 里面
        ol.appendChild(li);
        // 4. 小圆圈的排他思想 我们可以直接在生成小圆圈的同时直接绑定点击事件
        li.addEventListener('click', function() {
            // 干掉所有人 把所有的小li 清除 current 类名
            for (var i = 0; i < ol.children.length; i++) {
                ol.children[i].className = '';
            }
            // 留下我自己  当前的小li 设置current 类名
            this.className = 'current';
            // 5. 点击小圆圈，移动图片 当然移动的是 ul 
            // ul 的移动距离 小圆圈的索引号 乘以 图片的宽度 注意是负值
            // 当我们点击了某个小li 就拿到当前小li 的索引号
            var index = this.getAttribute('index');
            // 当我们点击了某个小li 就要把这个li 的索引号给 num  
            num = index;
            // 当我们点击了某个小li 就要把这个li 的索引号给 circle  
            circle = index;
            // num = circle = index;
            console.log(focusWidth);
            console.log(index);

            animate(ul, -index * focusWidth);
        })
    }
    // 把ol里面的第一个小li设置类名为 current
    ol.children[0].className = 'current';
    // 6. 克隆第一张图片(li)放到ul 最后面
    var first = ul.children[0].cloneNode(true);
    ul.appendChild(first);
    // 7. 点击右侧按钮， 图片滚动一张
    var num = 0;
    // circle 控制小圆圈的播放
    var circle = 0;
    // flag 节流阀
    var flag = true;
    arrow_r.addEventListener('click', function() {
        if (flag) {
            flag = false; // 关闭节流阀
            // 如果走到了最后复制的一张图片，此时 我们的ul 要快速复原 left 改为 0
            if (num == ul.children.length - 1) {
                ul.style.left = 0;
                num = 0;
            }
            num++;
            animate(ul, -num * focusWidth, function() {
                flag = true; // 打开节流阀
            });
            // 8. 点击右侧按钮，小圆圈跟随一起变化 可以再声明一个变量控制小圆圈的播放
            circle++;
            // 如果circle == 4 说明走到最后我们克隆的这张图片了 我们就复原
            if (circle == ol.children.length) {
                circle = 0;
            }
            // 调用函数
            circleChange();
        }
    });

    // 9. 左侧按钮做法
    arrow_l.addEventListener('click', function() {
        if (flag) {
            flag = false;
            if (num == 0) {
                num = ul.children.length - 1;
                ul.style.left = -num * focusWidth + 'px';

            }
            num--;
            animate(ul, -num * focusWidth, function() {
                flag = true;
            });
            // 点击左侧按钮，小圆圈跟随一起变化 可以再声明一个变量控制小圆圈的播放
            circle--;
            // 如果circle < 0  说明第一张图片，则小圆圈要改为第4个小圆圈（3）
            // if (circle < 0) {
            //     circle = ol.children.length - 1;
            // }
            circle = circle < 0 ? ol.children.length - 1 : circle;
            // 调用函数
            circleChange();
        }
    });

    function circleChange() {
        // 先清除其余小圆圈的current类名
        for (var i = 0; i < ol.children.length; i++) {
            ol.children[i].className = '';
        }
        // 留下当前的小圆圈的current类名
        ol.children[circle].className = 'current';
    }
    // 10. 自动播放轮播图
    var timer = setInterval(function() {
        //手动调用点击事件
        arrow_r.click();
    }, 2000);
})
```
节流阀：  
- 防止轮播图按钮连续点击造成播放过快。  
- 节流阀目的：当上一个函数动画内容执行完毕，再去执行下一个函数动画，让事件无法连续触发。  
- 核心实现思路：利用回调函数，添加一个变量来控制，锁住函数和解锁函数。   
- 开始设置一个变量 var flag = true;  
- If(flag) {flag = false; do something}       关闭水龙头  
- 利用回调函数 动画执行完毕， flag = true     打开水龙头

案例2：返回顶部 仿淘宝  

滚动窗口至文档中的特定位置。
window.scroll(x, y) 
注意，里面的x和y 不跟单位，直接写数字  

- 带有动画的返回顶部
- 此时可以继续使用我们封装的动画函数
- 只需要把所有的left 相关的值 改为 跟 页面垂直滚动距离相关就可以了
- 页面滚动了多少，可以通过 window.pageYOffset 得到
- 最后是页面滚动，使用 window.scroll(x,y) 

```html
<head>
    <style>
        .slider-bar {
            position: absolute;
            left: 50%;
            top: 300px;
            margin-left: 600px;
            width: 45px;
            height: 130px;
            background-color: pink;
        }
        
        .w {
            width: 1200px;
            margin: 10px auto;
        }
        
        .header {
            height: 150px;
            background-color: purple;
        }
        
        .banner {
            height: 250px;
            background-color: skyblue;
        }
        
        .main {
            height: 1000px;
            background-color: yellowgreen;
        }
        
        span {
            display: none;
            position: absolute;
            bottom: 0;
        }
    </style>
</head>

<body>
    <div class="slider-bar">
        <span class="goBack">返回顶部</span>
    </div>
    <div class="header w">头部区域</div>
    <div class="banner w">banner区域</div>
    <div class="main w">主体部分</div>
    <script>
        //1. 获取元素
        var sliderbar = document.querySelector('.slider-bar');
        var banner = document.querySelector('.banner');
        // banner.offestTop 就是被卷去头部的大小 一定要写到滚动的外面
        var bannerTop = banner.offsetTop
            // 当我们侧边栏固定定位之后应该变化的数值
        var sliderbarTop = sliderbar.offsetTop - bannerTop;
        // 获取main 主体元素
        var main = document.querySelector('.main');
        var goBack = document.querySelector('.goBack');
        var mainTop = main.offsetTop;
        // 2. 页面滚动事件 scroll
        document.addEventListener('scroll', function() {
                // console.log(11);
                // window.pageYOffset 页面被卷去的头部
                // console.log(window.pageYOffset);
                // 3 .当我们页面被卷去的头部大于等于了 172 此时 侧边栏就要改为固定定位
                if (window.pageYOffset >= bannerTop) {
                    sliderbar.style.position = 'fixed';
                    sliderbar.style.top = sliderbarTop + 'px';
                } else {
                    sliderbar.style.position = 'absolute';
                    sliderbar.style.top = '300px';
                }
                // 4. 当我们页面滚动到main盒子，就显示 goback模块
                if (window.pageYOffset >= mainTop) {
                    goBack.style.display = 'block';
                } else {
                    goBack.style.display = 'none';
                }

            })
            // 3. 当我们点击了返回顶部模块，就让窗口滚动的页面的最上方
        goBack.addEventListener('click', function() {
            // 里面的x和y 不跟单位的 直接写数字即可
            // window.scroll(0, 0);
            // 因为是窗口滚动 所以对象是window
            animate(window, 0);
        });
        // 动画函数
        function animate(obj, target, callback) {
            // console.log(callback);  callback = function() {}  调用的时候 callback()

            // 先清除以前的定时器，只保留当前的一个定时器执行
            clearInterval(obj.timer);
            obj.timer = setInterval(function() {
                // 步长值写到定时器的里面
                // 把我们步长值改为整数 不要出现小数的问题
                // var step = Math.ceil((target - obj.offsetLeft) / 10);
                var step = (target - window.pageYOffset) / 10;
                step = step > 0 ? Math.ceil(step) : Math.floor(step);
                if (window.pageYOffset == target) {
                    // 停止动画 本质是停止定时器
                    clearInterval(obj.timer);
                    // 回调函数写到定时器结束里面
                    // if (callback) {
                    //     // 调用函数
                    //     callback();
                    // }
                    callback && callback();
                }
                // 把每次加1 这个步长值改为一个慢慢变小的值  步长公式：(目标值 - 现在的位置) / 10
                // obj.style.left = window.pageYOffset + step + 'px';
                window.scroll(0, window.pageYOffset + step);
            }, 15);
        }
    </script>
</body>
```

案例3：筋头云案例
```html
<head lang="en">
    <style>
        * {
            margin: 0;
            padding: 0
        }
        
        ul {
            list-style: none;
        }
        
        body {
            background-color: black;
        }
        
        .c-nav {
            width: 900px;
            height: 42px;
            background: #fff url(images/rss.png) no-repeat right center;
            margin: 100px auto;
            border-radius: 5px;
            position: relative;
        }
        
        .c-nav ul {
            position: absolute;
        }
        
        .c-nav li {
            float: left;
            width: 83px;
            text-align: center;
            line-height: 42px;
        }
        
        .c-nav li a {
            color: #333;
            text-decoration: none;
            display: inline-block;
            height: 42px;
        }
        
        .c-nav li a:hover {
            color: white;
        }
        
        .c-nav li.current a {
            color: #0dff1d;
        }
        
        .cloud {
            position: absolute;
            left: 0;
            top: 0;
            width: 83px;
            height: 42px;
            background: url(images/cloud.gif) no-repeat;
        }
    </style>
    <script src="animate.js"></script>
    <script>
        window.addEventListener('load', function() {
            // 1. 获取元素
            var cloud = document.querySelector('.cloud');
            var c_nav = document.querySelector('.c-nav');
            var lis = c_nav.querySelectorAll('li');
            // 2. 给所有的小li绑定事件 
            // 这个current 做为筋斗云的起始位置
            var current = 0;
            for (var i = 0; i < lis.length; i++) {
                // (1) 鼠标经过把当前小li 的位置做为目标值
                lis[i].addEventListener('mouseenter', function() {
                    animate(cloud, this.offsetLeft);
                });
                // (2) 鼠标离开就回到起始的位置 
                lis[i].addEventListener('mouseleave', function() {
                    animate(cloud, current);
                });
                // (3) 当我们鼠标点击，就把当前位置做为目标值
                lis[i].addEventListener('click', function() {
                    current = this.offsetLeft;
                });
            }
        })
    </script>
</head>

<body>
    <div id="c_nav" class="c-nav">
        <span class="cloud"></span>
        <ul>
            <li class="current"><a href="#">首页新闻</a></li>
            <li><a href="#">师资力量</a></li>
            <li><a href="#">活动策划</a></li>
            <li><a href="#">企业文化</a></li>
            <li><a href="#">招聘信息</a></li>
            <li><a href="#">公司简介</a></li>
            <li><a href="#">我是佩奇</a></li>
            <li><a href="#">啥是佩奇</a></li>
        </ul>
    </div>
</body>
```

### 移动端网页特效
#### 触屏事件
- 移动端浏览器兼容性较好，我们不需要考虑以前 JS 的兼容性问题，可以放心的使用原生 JS 书写效果，但是移动端也有自己独特的地方。比如触屏事件 touch（也称触摸事件），Android 和 IOS 都有。
- touch 对象代表一个触摸点。触摸点可能是一根手指，也可能是一根触摸笔。触屏事件可响应用户手指（或触控笔）对屏幕或者触控板操作。

常见的触屏事件如下：
|触屏touch事件|说明|
|:--|:--|
|touchstart|手指触摸到一个DOM元素时触发|
|touchmove|手指在一个DOM元素上滑动时触发|
|touchend|手指从一个DOM元素上移开时触发|

```html
<head>
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
    <script>
        // 1. 获取元素
        // 2. 手指触摸DOM元素事件
        var div = document.querySelector('div');
        div.addEventListener('touchstart', function() {
            console.log('我摸了你');

        });
        // 3. 手指在DOM元素身上移动事件
        div.addEventListener('touchmove', function() {
            console.log('我继续摸');

        });
        // 4. 手指离开DOM元素事件
        div.addEventListener('touchend', function() {
            console.log('轻轻的我走了');

        });
    </script>
</body>
```

触摸事件对象：

|触摸列表|说明|
|:--|:--|
|touches|正在触摸屏幕的所有手指的一个列表|
|targetTouches|正在触摸当前DOM元素上的手指的一个列表|
|changedtouches|手指状态发生了改变的列表，从无到有，从有到无变化|

```html
<head>
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
    <script>
        // 触摸事件对象
        // 1. 获取元素
        // 2. 手指触摸DOM元素事件
        var div = document.querySelector('div');
        div.addEventListener('touchstart', function(e) {
            // console.log(e);
            // touches 正在触摸屏幕的所有手指的列表 
            // targetTouches 正在触摸当前DOM元素的手指列表
            // 如果侦听的是一个DOM元素，他们两个是一样的
            // changedTouches 手指状态发生了改变的列表 从无到有 或者 从有到无
            // 因为我们一般都是触摸元素 所以最经常使用的是 targetTouches
            console.log(e.targetTouches[0]);
            // targetTouches[0] 就可以得到正在触摸dom元素的第一个手指的相关信息比如 手指的坐标等等

        });
        // 3. 手指在DOM元素身上移动事件
        div.addEventListener('touchmove', function() {

        });
        // 4. 手指离开DOM元素事件
        div.addEventListener('touchend', function(e) {
            // console.log(e);
            // 当我们手指离开屏幕的时候，就没有了 touches 和 targetTouches 列表
            // 但是会有 changedTouches
        });
    </script>
</body>
```

移动端拖动元素：  

1. touchstart、touchmove、touchend 可以实现拖动元素
2. 但是拖动元素需要当前手指的坐标值 我们可以使用  targetTouches[0] 里面的pageX 和 pageY 
3. 移动端拖动的原理：    手指移动中，计算出手指移动的距离。然后用盒子原来的位置 + 手指移动的距离
4. 手指移动的距离：   手指滑动中的位置 减去  手指刚开始触摸的位置  
拖动元素三步曲：  
（1） 触摸元素 touchstart：  获取手指初始坐标，同时获得盒子原来的位置  
（2） 移动手指 touchmove：  计算手指的滑动距离，并且移动盒子  
（3） 离开手指 touchend:  

注意： 手指移动也会触发滚动屏幕所以这里要阻止默认的屏幕滚动 e.preventDefault();  

```html
<head>
    <style>
        div {
            position: absolute;
            left: 0;
            width: 100px;
            height: 100px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div></div>
    <script>
        // （1） 触摸元素 touchstart：  获取手指初始坐标，同时获得盒子原来的位置
        // （2） 移动手指 touchmove：  计算手指的滑动距离，并且移动盒子
        // （3） 离开手指 touchend:
        var div = document.querySelector('div');
        var startX = 0; //获取手指初始坐标
        var startY = 0;
        var x = 0; //获得盒子原来的位置
        var y = 0;
        div.addEventListener('touchstart', function(e) {
            //  获取手指初始坐标
            startX = e.targetTouches[0].pageX;
            startY = e.targetTouches[0].pageY;
            x = this.offsetLeft;
            y = this.offsetTop;
        });

        div.addEventListener('touchmove', function(e) {
            //  计算手指的移动距离： 手指移动之后的坐标减去手指初始的坐标
            var moveX = e.targetTouches[0].pageX - startX;
            var moveY = e.targetTouches[0].pageY - startY;
            // 移动我们的盒子 盒子原来的位置 + 手指移动的距离
            this.style.left = x + moveX + 'px';
            this.style.top = y + moveY + 'px';
            e.preventDefault(); // 阻止屏幕滚动的默认行为
        });
    </script>
</body>
```

#### 移动端常见特效

案例1：移动端轮播图
```js
window.addEventListener('load', function() {
    // alert(1);
    // 1. 获取元素 
    var focus = document.querySelector('.focus');
    var ul = focus.children[0];
    // 获得focus 的宽度
    var w = focus.offsetWidth;
    var ol = focus.children[1];
    // 2. 利用定时器自动轮播图图片
    var index = 0;
    var timer = setInterval(function() {
        index++;
        var translatex = -index * w;
        ul.style.transition = 'all .3s';
        ul.style.transform = 'translateX(' + translatex + 'px)';
    }, 2000);
    // 等着我们过渡完成之后，再去判断 监听过渡完成的事件 transitionend 
    ul.addEventListener('transitionend', function() {
        // 无缝滚动
        if (index >= 3) {
            index = 0;
            // console.log(index);
            // 去掉过渡效果 这样让我们的ul 快速的跳到目标位置
            ul.style.transition = 'none';
            // 利用最新的索引号乘以宽度 去滚动图片
            var translatex = -index * w;
            ul.style.transform = 'translateX(' + translatex + 'px)';
        } else if (index < 0) {
            index = 2;
            ul.style.transition = 'none';
            // 利用最新的索引号乘以宽度 去滚动图片
            var translatex = -index * w;
            ul.style.transform = 'translateX(' + translatex + 'px)';
        }
        // 3. 小圆点跟随变化
        // 把ol里面li带有current类名的选出来去掉类名 remove
        ol.querySelector('.current').classList.remove('current');
        // 让当前索引号 的小li 加上 current   add
        ol.children[index].classList.add('current');
    });

    // 4. 手指滑动轮播图 
    // 触摸元素 touchstart： 获取手指初始坐标
    var startX = 0;
    var moveX = 0; // 后面我们会使用这个移动距离所以要定义一个全局变量
    var flag = false;
    ul.addEventListener('touchstart', function(e) {
        startX = e.targetTouches[0].pageX;
        // 手指触摸的时候就停止定时器
        clearInterval(timer);
    });
    // 移动手指 touchmove： 计算手指的滑动距离， 并且移动盒子
    ul.addEventListener('touchmove', function(e) {
        // 计算移动距离
        moveX = e.targetTouches[0].pageX - startX;
        // 移动盒子：  盒子原来的位置 + 手指移动的距离 
        var translatex = -index * w + moveX;
        // 手指拖动的时候，不需要动画效果所以要取消过渡效果
        ul.style.transition = 'none';
        ul.style.transform = 'translateX(' + translatex + 'px)';
        flag = true; // 如果用户手指移动过我们再去判断否则不做判断效果
        e.preventDefault(); // 阻止滚动屏幕的行为
    });
    // 手指离开 根据移动距离去判断是回弹还是播放上一张下一张
    ul.addEventListener('touchend', function(e) {
        if (flag) {
            // (1) 如果移动距离大于50像素我们就播放上一张或者下一张
            if (Math.abs(moveX) > 50) {
                // 如果是右滑就是 播放上一张 moveX 是正值
                if (moveX > 0) {
                    index--;
                } else {
                    // 如果是左滑就是 播放下一张 moveX 是负值
                    index++;
                }
                var translatex = -index * w;
                ul.style.transition = 'all .3s';
                ul.style.transform = 'translateX(' + translatex + 'px)';
            } else {
                // (2) 如果移动距离小于50像素我们就回弹
                var translatex = -index * w;
                ul.style.transition = 'all .1s';
                ul.style.transform = 'translateX(' + translatex + 'px)';
            }
        }
        // 手指离开的时候就重新开启定时器
        clearInterval(timer);
        timer = setInterval(function() {
            index++;
            var translatex = -index * w;
            ul.style.transition = 'all .3s';
            ul.style.transform = 'translateX(' + translatex + 'px)';
        }, 2000);
    });

    // 返回顶部模块制作
    var goBack = document.querySelector('.goBack');
    var nav = document.querySelector('nav');
    window.addEventListener('scroll', function() {
        if (window.pageYOffset >= nav.offsetTop) {
            goBack.style.display = 'block';
        } else {
            goBack.style.display = 'none';
        }
    });
    goBack.addEventListener('click', function() {
        window.scroll(0, 0);
    })
})
```

classList 属性：  
- classList属性是HTML5新增的一个属性，返回元素的类名。但是ie10以上版本支持。
该属性用于在元素中添加，移除及切换 CSS 类。
- 注意以下方法里面，所有类名都不带点

1、添加类：`element.classList.add('类名');`  
2、移除类：`element.classList.remove('类名');`  
3、切换类：`element.classList.toggle('类名');`

```html
<head>
    <style>
        .bg {
            background-color: black;
        }
    </style>
</head>

<body>
    <div class="one two"></div>
    <button> 开关灯</button>
    <script>
        // classList 返回元素的类名
        var div = document.querySelector('div');
        // console.log(div.classList[1]);
        // 1. 添加类名  是在后面追加类名不会覆盖以前的类名 注意前面不需要加.
        div.classList.add('three');
        // 2. 删除类名
        div.classList.remove('one');
        // 3. 切换类
        var btn = document.querySelector('button');
        btn.addEventListener('click', function() {
            document.body.classList.toggle('bg');
        })
    </script>
</body>
```

click 延时解决方案：
- 移动端 click 事件会有 300ms 的延时，原因是移动端屏幕双击会缩放(double tap to zoom) 页面。
- 解决方案：
1. 禁用缩放。 浏览器禁用默认的双击缩放行为并且去掉 300ms 的点击延迟。
  <meta name="viewport" content="user-scalable=no">
2. 利用touch事件自己封装这个事件解决 300ms 延迟。 
    原理就是：
    1. 当我们手指触摸屏幕，记录当前触摸时间
    2. 当我们手指离开屏幕， 用离开的时间减去触摸的时间
    3. 如果时间小于150ms，并且没有滑动过屏幕， 那么我们就定义为点击
3. 使用插件。 fastclick 插件解决 300ms 延迟。 


#### 移动端常用开发插件
- 移动端要求的是快速开发，所以我们经常会借助于一些插件来帮我完成操作。
- JS 插件是 js 文件，它遵循一定规范编写，方便程序展示效果，拥有特定功能且方便调用。如轮播图和瀑布流插件。
- 特点：它一般是为了解决某个问题而专门存在，其功能单一，并且比较小。 我们以前写的animate.js 也算一个最简单的插件
- fastclick 插件解决 300ms 延迟。 使用延时  
- GitHub官网地址： https://github.com/ftlabs/fastclick

插件的使用：
1. 引入 js 插件文件。
2. 按照规定语法使用。

- Swiper 插件中文官网地址： https://www.swiper.com.cn/ 
- superslide插件： http://www.superslide2.com/
- iscroll插件： https://github.com/cubiq/iscroll

插件的使用总结：  
1、确认插件实现的功能  
2、去官网查看使用说明  
3、下载插件  
4、打开demo实例文件，查看需要引入的相关文件，并且引入  
5、复制demo实例文件中的结构html，样式css以及js代码  

fastclick插件使用：
```html
<head>
    <style>
        div {
            width: 50px;
            height: 50px;
            background-color: pink;
        }
    </style>
    <script src="fastclick.js"></script>
</head>

<body>
    <div></div>
    <script>
        if ('addEventListener' in document) {
            document.addEventListener('DOMContentLoaded', function() {
                FastClick.attach(document.body);
            }, false);
        }
        var div = document.querySelector('div');
        div.addEventListener('click', function() {
            alert(11);
        })
    </script>
</body>
```

swiper插件使用：
```js
window.addEventListener('load', function() {
    var swiper = new Swiper('.swiper-container', {
        spaceBetween: 30,
        centeredSlides: true,
        autoplay: {
            delay: 5000,
            disableOnInteraction: false,
        },
        pagination: {
            el: '.swiper-pagination',
            clickable: true,
        },
        navigation: {
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev',
        },
    });
})
```

移动端视频插件 zy.media.js

- H5 给我们提供了 video 标签，但是浏览器的支持情况不同。
不同的视频格式文件，我们可以通过source 解决。
但是外观样式，还有暂停，播放，全屏等功能我们只能自己写代码解决。
这个时候我们可以使用插件方式来制作。

```html
<head>
    <link rel="stylesheet" href="zy.media.min.css">
    <script src="zy.media.min.js"></script>
    <style type="text/css">
        #modelView {
            background-color: #DDDDDD;
            z-index: 0;
            opacity: 0.7;
            height: 100%;
            width: 100%;
            position: relative;
        }
        
        .playvideo {
            padding-top: auto;
            z-index: 9999;
            position: relative;
            width: 300px;
            height: 200px;
        }
        
        .zy_media {
            z-index: 999999999
        }
    </style>

</head>

<body>

    <div class="playvideo">
        <div class="zy_media">
            <video data-config='{"mediaTitle": "小蝴蝶"}'>
                    <source src="mov.mp4" type="video/mp4">
                    您的浏览器不支持HTML5视频
                </video>

        </div>
        <div id="modelView">&nbsp;</div>
    </div>
    <script>
        zymedia('video', {
            autoplay: false
        });
    </script>

</body>
```

#### 移动端常用开发框架
框架:
- 框架，顾名思义就是一套架构，它会基于自身的特点向用户提供一套较为完整的解决方案。框架的控制权在框架本身，使用者要按照框架所规定的某种规范进行开发。
- 框架： 大而全，一整套解决方案
- 前端常用的框架有 Bootstrap、Vue、Angular、React 等。既能开发PC端，也能开发移动端

插件：
- 插件一般是为了解决某个问题而专门存在，其功能单一，并且比较小。
- 插件： 小而专一，某个功能的解决方案
- 前端常用的移动端插件有 swiper、superslide、iscroll等。

Bootstrap 
- 是一个简洁、直观、强悍的前端开发框架，它让 web 开发更迅速、简单。
- 它能开发PC端，也能开发移动端 
- Bootstrap JS插件使用步骤：
1. 引入相关js 文件
2. 复制HTML 结构
3. 修改对应样式
4. 修改相应JS 参数

案例：  
Bootstrap轮播图  
阿里百秀轮播图


## 面向对象+ES6

### 面向对象
#### 面向对象编程介绍
#### ES6 中的类和对象
#### 类的继承
#### 面向对象案例




### 构造函数
#### 构造函数和原型
#### 继承
#### ES5 中的新增方法



### 函数进阶
#### 函数的定义和调用
#### this
#### 严格模式
#### 高阶函数
#### 闭包
#### 递归



### 正则表达式
#### 正则表达式概述
#### 正则表达式在 JavaScript 中的使用
#### 正则表达式中的特殊字符
#### 正则表达式中的替换



### ES6
#### ES6 简介
#### ES6 的新增语法
#### ES6 的内置对象扩展



```html

```


## 扩展

### 本地存储

本地存储之sessionStorage
```html
<body>
    <input type="text">
    <button class="set">存储数据</button>
    <button class="get">获取数据</button>
    <button class="remove">删除数据</button>
    <button class="del">清空所有数据</button>
    <script>
        console.log(localStorage.getItem('username'));

        var ipt = document.querySelector('input');
        var set = document.querySelector('.set');
        var get = document.querySelector('.get');
        var remove = document.querySelector('.remove');
        var del = document.querySelector('.del');
        set.addEventListener('click', function() {
            // 当我们点击了之后，就可以把表单里面的值存储起来
            var val = ipt.value;
            sessionStorage.setItem('uname', val);
            sessionStorage.setItem('pwd', val);
        });
        get.addEventListener('click', function() {
            // 当我们点击了之后，就可以把表单里面的值获取过来
            console.log(sessionStorage.getItem('uname'));

        });
        remove.addEventListener('click', function() {
            // 
            sessionStorage.removeItem('uname');

        });
        del.addEventListener('click', function() {
            // 当我们点击了之后，清除所有的
            sessionStorage.clear();

        });
    </script>
</body>
```

本地存储之localStorage
```html
<body>
    <input type="text">
    <button class="set">存储数据</button>
    <button class="get">获取数据</button>
    <button class="remove">删除数据</button>
    <button class="del">清空所有数据</button>
    <script>
        var ipt = document.querySelector('input');
        var set = document.querySelector('.set');
        var get = document.querySelector('.get');
        var remove = document.querySelector('.remove');
        var del = document.querySelector('.del');
        set.addEventListener('click', function() {
            var val = ipt.value;
            localStorage.setItem('username', val);
        })
        get.addEventListener('click', function() {
            console.log(localStorage.getItem('username'));

        })
        remove.addEventListener('click', function() {
            localStorage.removeItem('username');

        })
        del.addEventListener('click', function() {
            localStorage.clear();

        })
    </script>
</body>
```

记住用户名
```html
<body>
    <input type="text" id="username"> <input type="checkbox" name="" id="remember"> 记住用户名
    <script>
        var username = document.querySelector('#username');
        var remember = document.querySelector('#remember');
        if (localStorage.getItem('username')) {
            username.value = localStorage.getItem('username');
            remember.checked = true;
        }
        remember.addEventListener('change', function() {
            if (this.checked) {
                localStorage.setItem('username', username.value)
            } else {
                localStorage.removeItem('username');
            }
        })
    </script>
</body>
```

## 参考
{{< card "https://www.liaoxuefeng.com/wiki/1022910821149312" >}}             
{{< card "https://www.runoob.com/css/css-tutorial.html" >}}      
{{< card "https://humble-blog.vercel.app/html" >}}  


