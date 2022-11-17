---
title: "Ajax的使用"
date: 2022-10-28T19:37:30+08:00
tags: ['Support']
series: ['前端学习之旅']
---

## 服务器基本概念
### 客户端与服务器
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221107/image.q60rxguuc3k.webp)

### URL地址
1、
URL（全称是UniformResourceLocator）中文叫`统一资源定位符`，用于标识互联网上每个资源的唯一存放位置。浏览器只有通过URL地址，才能正确定位资源的存放位置，从而成功访问到对应的资源。

2、常见的URL举例：  
http://www.baidu.com  
http://www.taobao.com  
http://www.cnblogs.com/liulongbinblogs/p/11649393.html  

3、URL地址一般由三部组成：  
① 客户端与服务器之间的通信协议  
② 存有该资源的服务器名称  
③ 资源在服务器上具体的存放位置

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.nkvhhgoy434.webp)


### 浏览器开发者工具分析通信过程  
一、客户端与服务器的通信过程  
- 客户端与服务器之间的通信过程，分为 请求 – 处理 – 响应 三个步骤。   
- 网页中的每一个资源，都是通过 请求 – 处理 – 响应 的方式从服务器获取回来的。  

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.507iihnidpo0.webp)

二、基于浏览器的开发者工具分析通信过程  
1. 打开 Chrome 浏览器  
2. Ctrl+Shift+I 打开 Chrome 的开发者工具  
3. 切换到 Network 面板  
4. 选中 Doc 页签  
5. 刷新页面，分析客户端与服务器的通信过程  
6. 左侧Name为资源，选择其中一个资源
7. Headers请求，Response为响应

### 请求数据（get 与 post）
一、网页中常见的资源  

文字、图片、视频、音频、数据……  
数据是网页的灵魂

二、网页中请求数据

- 在网页中请求服务器上的数据资源，则需要用到 XMLHttpRequest 对象。
- XMLHttpRequest（简称 xhr）是浏览器提供的 js 成员，通过它，可以请求服务器上的数据资源。
- 最简单的用法 `var xhrObj = new XMLHttpRequest()`

三、资源的请求方式

客户端请求服务器时，最常见的两种请求方式：`get 和 post 请求`。  

1、 get 请求通常用于`获取服务端资源`（向服务器要资源）  
- 例如：根据 URL 地址，从服务器获取 HTML 文件、css 文件、js文件、图片文件、数据资源等

2、post 请求通常用于`向服务器提交数据`（往服务器发送资源）  
- 例如：登录时向服务器提交的登录信息、注册时向服务器提交的注册信息、添加用户时向服务器提交的用户信息等各种数据提交操作

## 接口  
使用 Ajax 请求数据时，`被请求的 URL 地址`，就叫做`数据接口`（简称接口）。同时，每个接口必须有`请求方式`。  

例如：  
http://www.liulongbin.top:3006/api/getbooks  获取图书列表的接口(GET请求)  
http://www.liulongbin.top:3006/api/addbook   添加图书的接口（POST请求）

### 接口的请求过程
1、通过GET方式请求接口的过程

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.28xrh5hluizo.webp)

2、通过POST方式请求接口的过程

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.17n0cgciyrpc.webp)

### 接口测试工具PostMan
一、概念  

1、为了验证接口能否被正常被访问，我们常常需要使用接口测试工具，来对数据接口进行检测。接口测试工具能让我们在不写任何代码的情况下，对接口进行调用和测试。  

2、PostMan官方下载网址     
<https://www.getpostman.com/downloads/>

二、工具的界面  
PostMan界面的组成部分，从上到下，从左到右，分别是：  
- 菜单栏  
- 工具栏  
- 左侧历史记录与集合面板  
- 请求页签  
- 请求地址区域  
- 请求参数区域  
- 响应结果区域  
- 状态栏  

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.6f4tcyubwek0.webp)

三、使用PostMan测试GET接口  
1. 选择请求的方式  
2. 填写请求的URL地址  
3. 填写请求的参数  
4. 点击 Send 按钮发起 GET 请求  
5. 查看服务器响应的结果  

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.553kg09jdwg0.webp)

四、使用PostMan测试POST接口  
1. 选择请求的方式  
2. 填写请求的URL地址  
3. 选择 Body 面板并勾选数据格式  
4. 填写要发送到服务器的数据  
5. 点击 Send 按钮发起 POST 请求  
6. 查看服务器响应的结果  

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.iv7ykqrsun4.webp)

### 接口文档
1、概念  
接口文档，顾名思义就是接口的说明文档，它是我们调用接口的依据。好的接口文档包含了对接口URL，参数以及输出内容的说明，我们参照接口文档就能方便的知道接口的作用，以及接口如何进行调用。

2、接口文档的组成部分

接口文档可以包含很多信息，也可以按需进行精简，不过，一个合格的接口文档，应该包含以下6项内容，从而为接口的调用提供依据：
- `接口名称`：用来标识各个接口的简单说明，如登录接口，获取图书列表接口等。
- `接口URL`：接口的调用地址。
- `调用方式`：接口的调用方式，如 GET 或 POST。
- `参数格式`：接口需要传递的参数，每个参数必须包含参数名称、参数类型、是否必选、参数说明这4项内容。
- `响应格式`：接口的返回值的详细描述，一般包含数据名称、数据类型、说明3项内容。
- 返回示例（可选）：通过对象的形式，例举服务器返回数据的结构。

## form表单
### form表单的基本使用 
一、概念   
表单在网页中主要负责数据采集功能。HTML中的`<form>`标签，就是用于采集用户输入的信息，并通过`<form>`标签的提交操作，把采集到的信息提交到服务器端进行处理。

二、表单组成  
表单由三个基本部分组成：表单标签、表单域、表单按钮
```js
<form>
    <input type="text" name="email_or_mobile" />
    <input type="password" name="password" />
    <input type="checkbox" name="remember_me" checked />
    <button type="submit">提交</button>
</form>
```

三、`<form>`标签的属性  
用来采集数据，标签的属性则是用来规定如何把采集到的数据发送到服务器。

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.315f3lb9qdm0.webp)


1、action

action 属性的值应该是后端提供的一个 URL 地址，这个 URL 地址专门负责接收表单提交过来的数据。  
当表单在未指定 action 属性值的情况下，action 的默认值为当前页面的 URL 地址。  
当提交表单后，页面会立即跳转到 action 属性指定的 URL 地址

2、target

可选值有5个：  
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.53slmcimhu40.webp)

3、method

默认情况下，method 的值为 get，表示通过URL地址的形式，把表单数据提交到 action URL。

注意：  
get 方式适合用来提交少量的、简单的数据。  
post 方式适合用来提交大量的、复杂的、或包含文件上传的数据。  
在实际开发中，表单的 post 提交方式用的最多，很少用 get。例如登录、注册、添加数据等表单操作，都需要使用 post 方式来提交表单。  

4、enctype

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.6pt4c9bcq6o0.webp)

注意：  
在涉及到文件上传的操作时，必须将 enctype 的值设置为 multipart/form-data  
如果表单的提交不涉及到文件上传操作，则直接将 enctype 的值设置为 application/x-www-form-urlencoded 即可！


四、表单提交数据的缺点

如果使用表单提交数据，则会导致以下两个问题：
- 页面会发生跳转
- 页面之前的状态和数据会丢失

解决方案：表单只负责采集数据，Ajax 负责将数据提交到服务器。

### 通过Ajax提交表单数据
一、监听表单提交事件   
在 jQuery 中，可以使用如下两种方式，监听到表单的提交事件：
```js
$('#form1').submit(function(e) {
   alert('监听到了表单的提交事件')
})

$('#form1').on('submit', function(e) {
   alert('监听到了表单的提交事件')
})
```

二、阻止表单默认提交行为

当监听到表单的提交事件以后，可以调用事件对象的 event.preventDefault() 函数，来阻止表单的提交和页面的跳转，示例代码如下：
```js
$('#form1').submit(function(e) {
   // 阻止表单的提交和页面的跳转
   e.preventDefault()
})

$('#form1').on('submit', function(e) {
   // 阻止表单的提交和页面的跳转
   e.preventDefault()
})
```

三、快速获取表单中的数据  
1、serialize()函数  

- 为了简化表单中数据的获取操作，jQuery 提供了 serialize() 函数，可以一次性获取到表单中的所有的数据。
- 在使用 serialize() 函数快速获取表单数据时，必须为每个表单元素添加 name 属性！

其语法格式如下：`$(selector).serialize()`

```js
<form id="form1">
    <input type="text" name="username" />
    <input type="password" name="password" />
    <button type="submit">提交</button>
</form>

$('#form1').serialize()
// 调用的结果：
// username=用户名的值&password=密码的值
```

案例 - 评论列表（见PPT）  
关于模板引擎 （略 见PPT）

## Ajax
### Ajax基本概念
一、概念  
- Ajax 的全称是 Asynchronous Javascript And XML（异步 JavaScript 和 XML）。通俗的理解：在网页中`利用 XMLHttpRequest 对象和服务器进行数据交互`的方式，就是Ajax。

二、为什么学习Ajax  
- 之前所学的技术，只能把网页做的更美观漂亮，或添加一些动画效果，但是，Ajax能让我们轻松`实现网页与服务器之间的数据交互`。

三、Ajax的典型应用场景  
1. 用户名检测：注册用户时，通过 ajax 的形式，动态检测用户名是否被占用
2. 搜索提示：当输入搜索关键字时，通过 ajax 的形式，动态加载搜索提示列表
3. 数据分页显示：当点击页码值的时候，通过 ajax 的形式，根据页码值动态刷新表格的数据
4. 数据的增删改查：数据的添加、删除、修改、查询操作，都需要通过 ajax 的形式，来实现数据的交互

### jQuery中的Ajax

- 浏览器中提供的 XMLHttpRequest 用法比较复杂，所以 jQuery 对 XMLHttpRequest 进行了封装，提供了一系列 Ajax 相关的函数，极大地降低了 Ajax 的使用难度。

- jQuery 中发起 Ajax 请求最常用的三个方法如下：
    1. $.get()
    2. $.post()
    3. $.ajax()

#### $.get()函数的语法  
一、语法  
- 函数的功能单一，专门用来发起 get 请求，从而将服务器上的资源请求到客户端来进行使用。
- 语法如下：`$.get(url, [data], [callback])`

其中，三个参数各自代表的含义如下：

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.wwmxd7gs0fk.webp)

二、发起不带参数的请求
```js
$.get('http://www.liulongbin.top:3006/api/getbooks', function(res) {
    console.log(res) // 这里的 res 是服务器返回的数据
})
```

三、发起带参数的请求
```js
$.get('http://www.liulongbin.top:3006/api/getbooks', { id: 1 }, function(res) {
    console.log(res)
})
```

#### $.post()函数的语法
一、语法
- jQuery 中 $.post() 函数的功能单一，专门用来发起 post 请求，从而向服务器提交数据。
- 语法如下：`$.post(url, [data], [callback])`

其中，三个参数各自代表的含义如下：

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.6fljyk25wvo0.webp)

二、向服务器提交数据

```js
$.post(
   'http://www.liulongbin.top:3006/api/addbook', // 请求的URL地址
   { bookname: '水浒传', author: '施耐庵', publisher: '上海图书出版社' }, // 提交的数据
   function(res) { // 回调函数
      console.log(res)
   }
)
```

#### $.ajax()函数的语法
一、语法

- 相比于 `$.get() 和 $.post() `函数，jQuery 中提供的` $.ajax() `函数，是一个功能比较综合的函数，它允许我们对 Ajax 请求进行更详细的配置。
- 基本语法如下：

```js
$.ajax({
   type: '', // 请求的方式，例如 GET 或 POST
   url: '',  // 请求的 URL 地址
   data: { },// 这次请求要携带的数据
   success: function(res) { } // 请求成功之后的回调函数
})
```

二、使用$.ajax()发起GET请求
- 使用 $.ajax() 发起 GET 请求时，只需要将 type 属性的值设置为 'GET' 即可：
```js
$.ajax({
   type: 'GET', // 请求的方式
   url: 'http://www.liulongbin.top:3006/api/getbooks',  // 请求的 URL 地址
   data: { id: 1 },// 这次请求要携带的数据
   success: function(res) { // 请求成功之后的回调函数
       console.log(res)
   }
})
```

三、使用$.ajax()发起POST请求
- 使用 $.ajax() 发起 POST 请求时，只需要将 type 属性的值设置为 'POST' 即可：
```js
$.ajax({
   type: 'POST', // 请求的方式
   url: 'http://www.liulongbin.top:3006/api/addbook',  // 请求的 URL 地址
   data: { // 要提交给服务器的数据
      bookname: '水浒传',
      author: '施耐庵',
      publisher: '上海图书出版社'
    },
   success: function(res) { // 请求成功之后的回调函数
       console.log(res)
   }
})
```

案例 - 图书管理  （见PPT）  
案例 – 聊天机器人  

### XMLHttpRequest的基本使用
XMLHttpRequest（简称 xhr）是浏览器提供的 Javascript 对象，通过它，可以请求服务器上的数据资源。之前所学的 jQuery 中的 Ajax 函数，就是基于 xhr 对象封装出来的。

#### 使用xhr发起GET请求

```js
// 1. 创建 xhr 对象
var xhr = new XMLHttpRequest()
// 2. 调用 xhr.open 函数，指定 请求方式 与 URL地址
xhr.open('GET', 'http://www.liulongbin.top:3006/api/getbooks')
// 3. 调用 xhr.send 函数，发起 Ajax 请求
xhr.send()
// 4. 监听 xhr.onreadystatechange 事件
xhr.onreadystatechange = function() {
    // 4.1 监听 xhr 对象的请求状态 readyState ；与服务器响应的状态 status
    if (xhr.readyState === 4 && xhr.status === 200) {
        // 4.2 打印服务器响应回来的数据
        console.log(xhr.responseText)
    }
}
```
一、关于readyState属性：  
- 用来表示当前 Ajax 请求所处的状态。每个 Ajax 请求必然处于以下状态中的一个
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.63qikt476hc0.webp)

二、使用xhr发起带参数的GET请求
- 只需在调用 xhr.open 期间，为 URL 地址指定参数即可：
```js
// ...省略不必要的代码
xhr.open('GET', 'http://www.liulongbin.top:3006/api/getbooks?id=1')
// ...省略不必要的代码
// 在 URL 地址后面拼接的参数 ?id=1 ，叫做查询字符串。
```

#### 使用xhr发起POST请求

```js
// 1. 创建 xhr 对象
var xhr = new XMLHttpRequest()
// 2. 调用 xhr.open()
xhr.open('POST', 'http://www.liulongbin.top:3006/api/addbook')
// 3. 设置 Content-Type 属性（固定写法）
xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded')
// 4. 调用 xhr.send()，同时将数据以查询字符串的形式，提交给服务器
xhr.send('bookname=水浒传&author=施耐庵&publisher=天津图书出版社')
// 5. 监听 xhr.onreadystatechange 事件
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        console.log(xhr.responseText)
    }
}
```

#### 查询字符串  
- 定义：查询字符串（URL 参数）是指在 URL 的末尾加上用于向服务器发送信息的字符串（变量）。
- 格式：将英文的 `?` 放在URL 的末尾，然后再加上 `参数＝值` ，想加上多个参数的话，使用 `&` 符号进行分隔。以这个形式，可以将想要发送给服务器的数据添加到 URL 中。

```js
//不带参数的 URL 地址
http://www.liulongbin.top:3006/api/getbooks
// 带一个参数的 URL 地址
http://www.liulongbin.top:3006/api/getbooks?id=1
// 带两个参数的 URL 地址
http://www.liulongbin.top:3006/api/getbooks?id=1&bookname=西游记
```

- 无论使用` $.ajax()，还是使用 $.get()，又或者直接使用 xhr 对象发起 GET 请求`，当需要携带参数的时候，本质上，都是直接将参数以查询字符串的形式，追加到 URL 地址的后面，发送到服务器的。

```js
$.get('url', {name: 'zs', age: 20}, function() {})
// 等价于
$.get('url?name=zs&age=20', function() {})


$.ajax({ method: 'GET', url: 'url', data: {name: 'zs', age: 20}, success: function() {} })
// 等价于
$.ajax({ method: 'GET', url: 'url?name=zs&age=20', success: function() {} })
```

#### 了解URL编码与解码

URL 地址中，只允许出现英文相关的字母、标点符号、数字，因此，在 URL 地址中不允许出现中文字符。如果 URL 中需要包含中文这样的字符，则必须对中文字符进行编码（转义）。  
- URL编码的原则：使用安全的字符（没有特殊用途或者特殊意义的可打印字符）去表示那些不安全的字符。
- URL编码原则的通俗理解：使用英文字符去表示非英文字符。
- 浏览器会自动对 URL 地址进行编码操作，因此程序员不需要关心 URL 地址的编码与解码操作。

```js
http://www.liulongbin.top:3006/api/getbooks?id=1&bookname=西游记
// 经过 URL 编码之后，URL地址变成了如下格式：
http://www.liulongbin.top:3006/api/getbooks?id=1&bookname=%E8%A5%BF%E6%B8%B8%E8%AE%B0

// encodeURI()  编码的函数
encodeURI('黑马程序员')
// 输出字符串  %E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98

// decodeURI()  解码的函数
decodeURI('%E9%BB%91%E9%A9%AC')
// 输出字符串  黑马
```

### 数据交换格式
数据交换格式，就是`服务器端与客户端之间`进行`数据传输与交换的格式`。前端领域，经常提及的两种数据交换格式分别是 XML 和 JSON。XML 用的非常少，我们重点要学习 `JSON`。

#### XML
1、概念
XML 的英文全称是 EXtensible Markup Language，即`可扩展标记语言`。

2、XML和HTML的区别
- XML 和 HTML 类似，也是一种标记语言。
- 但是，它们两者之间没有任何的关系。
- HTML 被设计用来描述网页上的内容，是网页内容的载体
- XML 被设计用来传输和存储数据，是数据的载体

3、XML的缺点  
XML 格式臃肿，和数据无关的代码多，体积大，传输效率低。在 Javascript 中解析 XML 比较麻烦

#### JSON
一、基本概念

1、概念：JSON 的英文全称是 JavaScript Object Notation，即“JavaScript 对象表示法”。简单来讲，`JSON 就是 Javascript 对象和数组的字符串表示法`，它使用文本表示一个 JS 对象或数组的信息，因此，`JSON 的本质是字符串`。

2、作用：JSON 是一种轻量级的文本数据交换格式，在作用上类似于 XML，专门用于存储和传输数据，但是 JSON 比 XML `更小、更快、更易解析`。

3、现状：JSON 是在 2001 年开始被推广和使用的数据格式，到现今为止，JSON 已经成为了主流的数据交换格式。

二、JSON的两种结构

JSON 就是用字符串来表示 Javascript 的对象和数组。所以，JSON 中包含对象和数组两种结构，通过这两种结构的相互嵌套，可以表示各种复杂的数据结构。

1、对象结构  
对象结构在 JSON 中表示为 { } 括起来的内容。数据结构为 { key: value, key: value, … } 的键值对结构。其中，key 必须是使用`英文的双引号包裹`的字符串，value 的数据类型可以是`数字、字符串、布尔值、null、数组、对象`6种类型。

```js
{
    "name": "zs",
    "age": 20,
    "gender": "男",
    "address": null,
    "hobby": ["吃饭", "睡觉", "打豆豆"]
}
```

2、数组结构  
数组结构在 JSON 中表示为 `[ ] 括起来`的内容。数据结构为 [ "java", "javascript", 30, true … ] 。数组中数据的类型可以是`数字、字符串、布尔值、null、数组、对象`6种类型。

```js
[ "java", "python", "php" ]
[ 100, 200, 300.5 ]
[ true, false, null ]
[ { "name": "zs", "age": 20}, { "name": "ls", "age": 30} ]
[ [ "苹果", "榴莲", "椰子" ], [ 4, 50, 5 ] ]
```

三、JSON语法注意事项

①属性名必须使用双引号包裹  
②字符串类型的值必须使用双引号包裹  
③JSON 中不允许使用单引号表示字符串  
④JSON 中不能写注释  
⑤JSON 的最外层必须是对象或数组格式  
⑥不能使用 undefined 或函数作为 JSON 的值 

JSON 的作用：在计算机与网络之间存储和传输数据。  
JSON 的本质：用字符串来表示 Javascript 对象数据或数组数据  

四、JSON和JS对象的关系  

JSON 是 JS 对象的字符串表示法，它使用文本表示一个 JS 对象的信息，本质是一个字符串。

JSON和JS对象的互转：
```js
// 从 JSON 字符串转换为 JS 对象，使用 JSON.parse() 方法：
var obj = JSON.parse('{"a": "Hello", "b": "World"}')
//结果是 {a: 'Hello', b: 'World'}


// 从 JS 对象转换为 JSON 字符串，使用 JSON.stringify() 方法：
var json = JSON.stringify({a: 'Hello', b: 'World'})
//结果是 '{"a": "Hello", "b": "World"}'
```

五、序列化和反序列化

把`数据对象转换为字符串`的过程，叫做`序列化`，例如：调用 JSON.stringify() 函数的操作，叫做 JSON 序列化。    
把`字符串转换为数据对象`的过程，叫做`反序列化`，例如：调用 JSON.parse() 函数的操作，叫做 JSON 反序列化。


### 封装自己的Ajax函数

```js
<!-- 1. 导入自定义的ajax函数库 -->
<script src="./itheima.js"></script>

<script>
    // 2. 调用自定义的 itheima 函数，发起 Ajax 数据请求
    itheima({
        method: '请求类型',
        url: '请求地址',
        data: { /* 请求参数对象 */ },
        success: function(res) { // 成功的回调函数
            console.log(res)     // 打印数据
        }
    })
</script>
```

一、处理data参数  
需要把 data 对象，转化成查询字符串的格式，从而提交给服务器，因此提前定义 resolveData 函数如下：

```js
/**
 * 处理 data 参数
 * @param {data} 需要发送到服务器的数据
 * @returns {string} 返回拼接好的查询字符串 name=zs&age=10
 */
function resolveData(data) {
  var arr = []
  for (var k in data) {
    arr.push(k + '=' + data[k])
  }
  return arr.join('&')
}
```

二、定义itheima函数  
在 itheima() 函数中，需要创建 xhr 对象，并监听 onreadystatechange 事件：

```js
function itheima(options) {
  var xhr = new XMLHttpRequest()
  // 拼接查询字符串
  var qs = resolveData(options.data)

  // 监听请求状态改变的事件
  xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
      var result = JSON.parse(xhr.responseText)
      options.success(result)
    }
  }
}
```

三、判断请求的类型  
不同的请求类型，对应 xhr 对象的不同操作，因此需要对请求类型进行 if … else … 的判断：

```js
  if (options.method.toUpperCase() === 'GET') {
    // 发起 GET 请求
    xhr.open(options.method, options.url + '?' + qs)
    xhr.send()
  } else if (options.method.toUpperCase() === 'POST') {
    // 发起 POST 请求
    xhr.open(options.method, options.url)
    xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded')
    xhr.send(qs)
  }
```

### XMLHttpRequest Level2的新特性
1、旧版XMLHttpRequest的缺点
- 只支持文本数据的传输，无法用来读取和上传文件
- 传送和接收数据时，没有进度信息，只能提示有没有完成

2、XMLHttpRequest Level2的新功能
- 可以设置 HTTP 请求的时限
- 可以使用 FormData 对象管理表单数据
- 可以上传文件
- 可以获得数据传输的进度信息

#### 设置HTTP请求时限

有时，Ajax 操作很耗时，而且无法预知要花多少时间。如果网速很慢，用户可能要等很久。新版本的 XMLHttpRequest 对象，增加了 timeout 属性，可以设置 HTTP 请求的时限：

```js
// 将最长等待时间设为 3000 毫秒。过了这个时限，就自动停止HTTP请求
 xhr.timeout = 3000
 // timeout 事件，用来指定回调函数
 xhr.ontimeout = function(event){
     alert('请求超时！')
 }
```

#### FormData对象管理表单数据  
Ajax 操作往往用来提交表单数据。为了方便表单处理，HTML5 新增了一个 FormData 对象，可以模拟表单操作：
```js
 // 1. 新建 FormData 对象
var fd = new FormData()
// 2. 为 FormData 添加表单项
fd.append('uname', 'zs')
fd.append('upwd', '123456')
// 3. 创建 XHR 对象
var xhr = new XMLHttpRequest()
// 4. 指定请求类型与URL地址
xhr.open('POST', 'http://www.liulongbin.top:3006/api/formdata')
// 5. 直接提交 FormData 对象，这与提交网页表单的效果，完全一样
xhr.send(fd)
```

FormData对象也可以用来获取网页表单的值，示例代码如下：

```js
 // 获取表单元素
 var form = document.querySelector('#form1')
 // 监听表单元素的 submit 事件
 form.addEventListener('submit', function(e) {
    e.preventDefault()
     // 根据 form 表单创建 FormData 对象，会自动将表单数据填充到 FormData 对象中
     var fd = new FormData(form)
     var xhr = new XMLHttpRequest()
     xhr.open('POST', 'http://www.liulongbin.top:3006/api/formdata')
     xhr.send(fd)
     xhr.onreadystatechange = function() {}
})
```

#### 上传文件

新版 XMLHttpRequest 对象，不仅可以发送文本信息，还可以上传文件。  
实现步骤：  
1、定义 UI 结构  
2、验证是否选择了文件  
3、向 FormData 中追加文件  
4、使用 xhr 发起上传文件的请求  
5、监听 onreadystatechange 事件  

```js
// 定义 UI 结构  
    <!-- 1. 文件选择框 -->
    <input type="file" id="file1" />
    <!-- 2. 上传按钮 -->
    <button id="btnUpload">上传文件</button>
    <br />
    <!-- 3. 显示上传到服务器上的图片 -->
    <img src="" alt="" id="img" width="800" />

// 验证是否选择了文件  
    // 1. 获取上传文件的按钮
    var btnUpload = document.querySelector('#btnUpload')
    // 2. 为按钮添加 click 事件监听
    btnUpload.addEventListener('click', function() {
        // 3. 获取到选择的文件列表
        var files = document.querySelector('#file1').files
        if (files.length <= 0) {
            return alert('请选择要上传的文件！')
        }
        // ...后续业务逻辑
    })

// 向 FormData 中追加文件 
    // 1. 创建 FormData 对象
    var fd = new FormData()
    // 2. 向 FormData 中追加文件
    fd.append('avatar', files[0])

// 使用 xhr 发起上传文件的请求  
    // 1. 创建 xhr 对象
    var xhr = new XMLHttpRequest()
    // 2. 调用 open 函数，指定请求类型与URL地址。其中，请求类型必须为 POST
    xhr.open('POST', 'http://www.liulongbin.top:3006/api/upload/avatar')
    // 3. 发起请求
    xhr.send(fd)

// 监听 onreadystatechange 事件 
    xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        var data = JSON.parse(xhr.responseText)
        if (data.status === 200) { // 上传文件成功
        // 将服务器返回的图片地址，设置为 <img> 标签的 src 属性
        document.querySelector('#img').src = 'http://www.liulongbin.top:3006' + data.url
        } else { // 上传文件失败
        console.log(data.message)
        }
    }
    }
```
#### 显示文件上传进度  
新版本的 XMLHttpRequest 对象中，可以通过监听 xhr.upload.onprogress 事件，来获取到文件的上传进度。语法格式如下：
```js
 // 创建 XHR 对象
 var xhr = new XMLHttpRequest()
 // 监听 xhr.upload 的 onprogress 事件
 xhr.upload.onprogress = function(e) {
    // e.lengthComputable 是一个布尔值，表示当前上传的资源是否具有可计算的长度
    if (e.lengthComputable) {
        // e.loaded 已传输的字节
        // e.total  需传输的总字节
        var percentComplete = Math.ceil((e.loaded / e.total) * 100)
    }
 }
```

### jQuery高级用法
一、jQuery实现文件上传

```js
// 定义UI结构
    <!-- 导入 jQuery -->
    <script src="./lib/jquery.js"></script>

    <!-- 文件选择框 -->
    <input type="file" id="file1" />
    <!-- 上传文件按钮 -->
    <button id="btnUpload">上传</button>

// 验证是否选择了文件
$(function(){
 $('#btnUpload').on('click', function() {
     // 1. 将 jQuery 对象转化为 DOM 对象，并获取选中的文件列表
     var files = $('#file1')[0].files
     // 2. 判断是否选择了文件
     if (files.length <= 0) {
         return alert('请选择图片后再上传！‘)
     }
    })
 })

// 向FormData中追加文件
 var fd = new FormData()
 fd.append('avatar', files[0])

// 使用jQuery发起上传文件的请求
 $.ajax({
     method: 'POST',
     url: 'http://www.liulongbin.top:3006/api/upload/avatar',
     data: fd,
     // 不修改 Content-Type 属性，使用 FormData 默认的 Content-Type 值
     contentType: false,
     // 不对 FormData 中的数据进行 url 编码，而是将 FormData 数据原样发送到服务器
     processData: false,
     success: function(res) {
         console.log(res)
     }
 })
```

二、jQuery实现loading效果  

1、ajaxStart(callback)  
Ajax 请求开始时，执行 ajaxStart 函数。可以在 ajaxStart 的 callback 中显示 loading 效果，示例代码如下：
```js
// 自 jQuery 版本 1.8 起，该方法只能被附加到文档
// 注意： $(document).ajaxStart() 函数会监听当前文档内所有的 Ajax 请求。
 $(document).ajaxStart(function() {
     $('#loading').show()
 })
```

2、 ajaxStop(callback)  
Ajax 请求结束时，执行 ajaxStop 函数。可以在 ajaxStop 的 callback 中隐藏 loading 效果，示例代码如下：
```js
// 自 jQuery 版本 1.8 起，该方法只能被附加到文档
 $(document).ajaxStop(function() {
     $('#loading').hide()
 })
```

### axios
Axios 是专注于`网络数据请求的库`。  
相比于原生的 XMLHttpRequest 对象，axios `简单易用`。  
相比于 jQuery，axios 更加`轻量化`，只专注于网络数据请求。  

#### axios发起GET请求  
语法：`axios.get('url', { params: { /*参数*/ } }).then(callback)`

```js
 // 请求的 URL 地址
 var url = 'http://www.liulongbin.top:3006/api/get'
 // 请求的参数对象
 var paramsObj = { name: 'zs', age: 20 }
 // 调用 axios.get() 发起 GET 请求
 axios.get(url, { params: paramsObj }).then(function(res) {
     // res.data 是服务器返回的数据
     var result = res.data
     console.log(res)
 })
```

#### axios发起POST请求
语法：` axios.post('url', { /*参数*/ }).then(callback)`
```js
 // 请求的 URL 地址
 var url = 'http://www.liulongbin.top:3006/api/post'
 // 要提交到服务器的数据
 var dataObj = { location: '北京', address: '顺义' }
 // 调用 axios.post() 发起 POST 请求
 axios.post(url, dataObj).then(function(res) {
     // res.data 是服务器返回的数据
     var result = res.data
     console.log(result)
 })
```

#### 直接使用axios发起请求
语法：  
```js
 axios({
     method: '请求类型',
     url: '请求的URL地址',
     data: { /* POST数据 */ },
     params: { /* GET参数 */ }
 }) .then(callback)
```

1、直接使用axios发起GET请求
```js
 axios({
     method: 'GET',
     url: 'http://www.liulongbin.top:3006/api/get',
     params: { // GET 参数要通过 params 属性提供
         name: 'zs',
         age: 20
     }
 }).then(function(res) {
     console.log(res.data)
 })
```

2、直接使用axios发起POST请求

```js
 axios({
     method: 'POST',
     url: 'http://www.liulongbin.top:3006/api/post',
     data: { // POST 数据要通过 data 属性提供
         bookname: '程序员的自我修养',
         price: 666
     }
 }).then(function(res) {
     console.log(res.data)
 })
```

## 跨域与JSONP
### 了解同源策略和跨域
一、同源策略  

1、什么是同源  
如果两个页面的协议，域名和端口都相同，则两个页面具有`相同的源`。  
例如，下表给出了相对于 http://www.test.com/index.html 页面的同源检测：  

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.r14whgvey9s.webp)

2、什么是同源策略  

同源策略（英文全称 Same origin policy）是浏览器提供的一个安全功能。

MDN 官方给定的概念：同源策略限制了从同一个源加载的文档或脚本如何与来自另一个源的资源进行交互。这是一个用于隔离潜在恶意文件的重要安全机制。

通俗的理解：浏览器规定，A 网站的 JavaScript，不允许和非同源的网站 C 之间，进行资源的交互，例如：  
- 无法读取非同源网页的 Cookie、LocalStorage 和 IndexedDB  
- 无法接触非同源网页的 DOM  
- 无法向非同源地址发送 Ajax 请求  

二、跨域  

1、什么是跨域  
同源指的是两个 URL 的协议、域名、端口一致，反之，则是跨域。  

出现跨域的根本原因：浏览器的同源策略不允许非同源的 URL 之间进行资源的交互。  
网页：http://www.test.com/index.html  
接口：http://www.api.com/userlist  

2、浏览器对跨域请求的拦截  
浏览器允许发起跨域请求，但是，跨域请求回来的数据，会被浏览器拦截，无法被页面获取到！

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.5psn7yedwi80.webp)

三、如何实现跨域数据请求

现如今，实现跨域数据请求，最主要的两种解决方案，分别是 JSONP 和 CORS。  

JSONP：出现的早，兼容性好（兼容低版本IE）。是前端程序员为了解决跨域问题，被迫想出来的一种临时解决方案。缺点是只支持 GET 请求，不支持 POST 请求。

CORS：出现的较晚，它是 W3C 标准，属于跨域 Ajax 请求的根本解决方案。支持 GET 和 POST 请求。缺点是不兼容某些低版本的浏览器。

### JSONP
1、概念  
JSONP (JSON with Padding) 是 JSON 的一种“使用模式”，可用于解决主流浏览器的跨域数据访问的问题。

2、实现原理  

由于浏览器同源策略的限制，网页中无法通过 Ajax 请求非同源的接口数据。但是 `<script>` 标签不受浏览器同源策略的影响，可以通过 src 属性，请求非同源的 js 脚本。      

因此，JSONP 的实现原理，就是通过 `<script> `标签的 src 属性，请求跨域的数据接口，并通过函数调用的形式，接收跨域接口响应回来的数据。

自己实现一个简单的JSONP：
```js
// 定义一个 success 回调函数：
 <script>
   function success(data) {
     console.log('获取到了data数据：')
     console.log(data)
   }
 </script>

// 通过 <script> 标签，请求接口数据：
<script src="http://ajax.frontend.itheima.net:3006/api/jsonp?callback=success&name=zs&age=20"></script>
```

3、JSONP的缺点  

由于 JSONP 是通过` <script>` 标签的 src 属性，来实现跨域数据获取的，所以，JSONP 只支持 GET 数据请求，不支持 POST 请求。

注意：JSONP 和 Ajax 之间没有任何关系，不能把 JSONP 请求数据的方式叫做 Ajax，因为 JSONP 没有用到 XMLHttpRequest 这个对象。

4、jQuery中的JSONP  
jQuery 提供的 $.ajax() 函数，除了可以发起真正的 Ajax 数据请求之外，还能够发起 JSONP 数据请求，例如：

默认情况下，使用 jQuery 发起 JSONP 请求，会自动携带一个 callback=jQueryxxx 的参数，jQueryxxx 是随机生成的一个回调函数名称。
```js
 $.ajax({
    url: 'http://ajax.frontend.itheima.net:3006/api/jsonp?name=zs&age=20',
    // 如果要使用 $.ajax() 发起 JSONP 请求，必须指定 datatype 为 jsonp
    dataType: 'jsonp',
    success: function(res) {
       console.log(res)
    }
 })
```

5、自定义参数及回调函数名称

在使用 jQuery 发起 JSONP 请求时，如果想要自定义 JSONP 的参数以及回调函数名称，可以通过如下两个参数来指定：

```js
 $.ajax({
    url: 'http://ajax.frontend.itheima.net:3006/api/jsonp?name=zs&age=20',
    dataType: 'jsonp',
    // 发送到服务端的参数名称，默认值为 callback
    jsonp: 'callback',
    // 自定义的回调函数名称，默认值为 jQueryxxx 格式
    jsonpCallback: 'abc',
    success: function(res) {
       console.log(res)
    }
 })
```

6、jQuery中JSONP的实现过程  

jQuery 中的 JSONP，也是通过 `<script>` 标签的 src 属性实现跨域数据访问的，只不过，jQuery 采用的是动态创建和移除 `<script>` 标签的方式，来发起 JSONP 数据请求。  

在发起 JSONP 请求的时候，动态向 `<header>` 中 append 一个 `<script> `标签；  
在 JSONP 请求成功以后，动态从 `<header> `中移除刚才 append 进去的 `<script> `标签；


案例-淘宝搜索 （见）  

### 防抖和节流  
一、什么是节流  
节流策略（throttle），顾名思义，可以减少一段时间内事件的触发频率。

二、节流的应用场景
- 鼠标连续不断地触发某事件（如点击），只在单位时间内只触发一次；
- 懒加载时要监听计算滚动条的位置，但不必每次滑动都触发，可以降低计算的频率，而不必去浪费 CPU 资源；

节流案例 – 鼠标跟随效果  （见）

三、节流阀的概念  

节流阀为`空`，表示`可以执行下次操作`；不为空，表示不能执行下次操作。  
当前操作执行完，必须将节流阀`重置`为空，表示可以执行下次操作了。  
每次执行操作前，必须`先判断节流阀是否为空`。  

四、防抖和节流的区别  
防抖：如果事件被频繁触发，防抖能保证只有最后一次触发生效！前面 N 多次的触发都会被忽略！  
节流：如果事件被频繁触发，节流能够减少事件触发的频率，因此，节流是有选择性地执行一部分事件！  


## HTTP协议
### HTTP协议简介   
一、什么是通信  
通信，就是信息的传递和交换。    
通信三要素：通信的主体、通信的内容、通信的方式  

案例：服务器把传智专修学院的简介通过响应的方式发送给客户端浏览器。  
其中，  
通信的主体是服务器和客户端浏览器；  
通信的内容是传智专修学院的简介；  
通信的方式是响应；  

二、什么是通信协议  
通信协议（Communication Protocol）是指通信的双方完成通信所`必须遵守`的`规则和约定`。    
通俗的理解：通信双方采用约定好的格式来发送和接收消息，这种事先约定好的通信格式，就叫做通信协议。  

三、HTTP协议  

客户端与服务器之间要实现网页内容的传输，则通信的双方必须遵守网页内容的传输协议。 

网页内容又叫做超文本，因此`网页内容的传输协议`又叫做`超文本传输协议`（HyperText Transfer Protocol） ，简称 HTTP 协议。  

HTTP 协议即超文本传送协议 (HyperText Transfer Protocol) ，它规定了客户端与服务器之间进行网页内容传输时，所必须遵守的传输格式。例如：     
- 客户端要以HTTP协议要求的格式把数据提交到服务器  
- 服务器要以HTTP协议要求的格式把内容响应给客户端  

四、 HTTP协议的交互模型  
HTTP 协议采用了`请求/响应`的交互模型。  

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.5jdg97b885g0.webp)

### HTTP请求

由于 HTTP 协议属于客户端浏览器和服务器之间的通信协议。因此，客户端发起的请求叫做 `HTTP 请求`，客户端发送到服务器的消息，叫做 `HTTP 请求消息`，又叫做 HTTP 请求报文。

#### HTTP请求消息的组成

HTTP 请求消息由：请求行（request line）、请求头部（ header ） 、空行 和 请求体 4 个部分组成。

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.4djxq905j5e0.webp)


一、请求行  
请求行由请求方式、URL 和 HTTP 协议版本 3 个部分组成，他们之间使用空格隔开。

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.6j0fr0y6d500.webp)


二、请求头部  
1、请求头部用来描述客户端的基本信息，从而把客户端相关的信息告知服务器。比如：User-Agent 用来说明当前是什么类型的浏览器；

2、请求头部由多行 键/值对 组成，每行的键和值之间用英文的冒号分隔。

3、最后一个请求头部字段的后面是一个空行，通知服务器请求头部至此结束。也用来分隔请求头部与请求体。


常见的请求头字段
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.4wivsp4fldo0.webp)

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.2z0tbiothog0.webp)

三、请求体  
请求体中存放的，是要通过 POST 方式提交到服务器的数据。  
只有 POST 请求才有请求体，GET 请求没有请求体！  


#### HTTP请求方法  

HTTP 请求方法，属于 HTTP 协议中的一部分。  
请求方法的作用是：用来表明要对服务器上的资源执行的操作。最常用的请求方法是 GET 和 POST。

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.17jcm7xgcay.webp)


### HTTP响应

响应消息就是`服务器响应给客户端的消息内容`，也叫作响应报文。
 
#### HTTP响应消息组成

HTTP响应消息由：状态行、响应头部、空行 和 响应体 4 个部分组成，如下图所示：

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.5b7jbamd6oc0.webp)


一、状态行  
状态行由 HTTP 协议版本、状态码和状态码的描述文本 3 个部分组成，他们之间使用空格隔开;
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.8k3yxt6fo0g.webp)

二、响应头部  
1、响应头部用来描述服务器的基本信息。响应头部由多行 键/值对 组成，每行的键和值之间用英文的冒号分隔。

2、在最后一个响应头部字段结束之后，会紧跟一个空行，用来通知客户端响应头部至此结束。用来分隔响应头部与响应体。

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.50v1p4jf5ro0.webp)


三、响应体  
响应体中存放的，是服务器响应给客户端的资源内容。

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.5lvjnra7b2o0.webp)


#### HTTP响应状态代码

HTTP 响应状态码（HTTP Status Code），也属于 HTTP 协议的一部分，用来标识响应的状态。  
响应状态码会随着响应消息一起被发送至客户端浏览器，浏览器根据服务器返回的响应状态码，就能知道这次 HTTP 请求的结果是成功还是失败了。  

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.5mdgsnqohds0.webp)

一、HTTP响应状态码的组成及分类

HTTP 状态码由三个十进制数字组成，第一个十进制数字定义了状态码的类型，后两个数字用来对状态码进行细分。

HTTP 状态码共分为 5 种类型：

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.3swqavp6ewk0.webp)

完整的 HTTP 响应状态码，可以参考 MDN 官方文档   
<https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Status>