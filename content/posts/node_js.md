---
title: "Node.js的使用"
date: 2022-11-17T12:06:29+08:00
tags: ['Support']
series: ['前端学习之旅']
---

## 初识Node.js
### 简介
一、为什么 JavaScript 可以在浏览器中被执行  
- 不同的浏览器使用不同的 JavaScript 解析引擎。其中，Chrome 浏览器的 V8 解析引擎性能最好！
- 每个浏览器都内置了 DOM、BOM 这样的 API 函数，因此，浏览器中的 JavaScript 才可以调用它们。

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221122/image.3za1x2l4cek0.webp)

二、什么是 Node.js
- `Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境`。
- Node.js 的官网地址： <https://nodejs.org/zh-cn/>

三、Node.js 中的 JavaScript 运行环境  

① 浏览器是 JavaScript 的前端运行环境。  
② Node.js 是 JavaScript 的后端运行环境。  
③ Node.js 中无法调用 DOM 和 BOM 等的浏览器内置 API。   

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221122/image.2j0wcg85k3a0.webp)

四、在Node上运行的JavaScript相比其他后端开发语言有何优势？

- 最大的优势是借助JavaScript天生的事件驱动机制加V8高性能引擎，使编写高性能Web服务轻而易举。

- 其次，JavaScript语言本身是完善的函数式语言，在前端开发时，开发人员往往写得比较随意，让人感觉JavaScript就是个“玩具语言”。但是，在Node环境下，通过模块化的JavaScript代码，加上函数式编程，并且无需考虑浏览器兼容性问题，直接使用最新的ECMAScript 6标准，可以完全满足工程上的需求。

五、Node.js 怎么学  

1、浏览器中的 JavaScript 学习路径：
- JavaScript 基础语法 + 浏览器内置 API（DOM + BOM） + 第三方库（jQuery、art-template 等）

2、Node.js 的学习路径：  
- JavaScript 基础语法 + Node.js 内置 API 模块（fs、path、http等）+ 第三方 API 模块（express、mysql 等）

### Node.js 环境的下载安装

一、安装  

1、希望通过 Node.js 来运行 Javascript 代码，则必须在计算机上安装 Node.js 环境才行。  

2、官网首页 <https://nodejs.org/en/>。点击绿色按钮 下载所需的版本 双击直接安装即可。

3、在Windows上安装时务必选择全部组件，包括勾选Add to Path。

4、打开终端，在终端输入命令 `node –v`后，按下回车键，即可查看已安装的 Node.js 的版本号。

5、继续在命令提示符输入node，此刻你将进入Node.js的交互环境。在交互环境下，你可以输入任意JavaScript语句，例如100+200，回车后将得到输出结果。要退出Node.js环境，连按两次Ctrl+C。

二、区分 LTS 版本和 Current 版本的不同

- LTS 为长期稳定版，对于追求稳定性的企业级项目来说，推荐安装 LTS 版本的 Node.js。
- Current 为新特性尝鲜版，对热衷于尝试新特性的用户来说，推荐安装 Current 版本的 Node.js。但是，Current 版本中可能存在隐藏的 Bug 或安全性漏洞，因此不推荐在企业级项目中使用 Current 版本的 Node.js。

### 基本模块（略）
一、fs 文件系统模块
- fs 模块是 Node.js 官方提供的、用来操作文件的模块。它提供了一系列的方法和属性，用来满足用户对文件的操作需求。  
- 例如：
    - fs.readFile() 方法，用来读取指定文件中的内容
    - fs.writeFile() 方法，用来向指定的文件中写入内容

二、path 路径模块
- path 模块是 Node.js 官方提供的、用来处理路径的模块。它提供了一系列的方法和属性，用来满足用户对路径的处理需求。
- 例如：  
    - path.join() 方法，用来将多个路径片段拼接成一个完整的路径字符串
    - path.basename() 方法，用来从路径字符串中，将文件名解析出来

三、http 模块
- http 模块是 Node.js 官方提供的、用来创建 web 服务器的模块。
- 通过 http 模块提供的 http.createServer() 方法，就能方便的把一台普通的电脑，变成一台 Web 服务器，从而对外提供 Web 资源服务。

四、Node.js 中的模块化

五、Express

六、MySQL数据库与身份认证

## npm与包
### 概念
#### 什么是包、npm
- `Node.js 中的第三方模块又叫做包`。就像电脑和计算机指的是相同的东西，第三方模块和包指的是同一个概念，只不过叫法不同。包是由第三方个人或团队开发出来的，免费供所有人使用。包是基于内置模块封装出来的，提供了更高级、更方便的 API，极大的提高了开发效率。

- `npm其实是Node.js的包管理工具`（Node Package Manager）。是国外有一家叫 npm, Inc.公司提供的，它是全球最大的包共享平台

- 其实npm包管理工具，已经在Node.js安装的时候顺带装好了。我们在终端输入`npm -v`，即可查看已安装的 npm 包管理工具的版本号。

#### 包的分类

使用 npm 包管理工具下载的包，共分为两大类：

一、项目包
- 那些被安装到项目的 node_modules 目录中的包，都是项目包。
- 项目包又分为两类：
    - 开发依赖包（被记录到 devDependencies 节点中的包，只在开发期间会用到）
    - 核心依赖包（被记录到 dependencies 节点中的包，在开发期间和项目上线之后都会用到）

二、全局包
- 在执行 npm install 命令时，如果提供了 -g 参数，则会把包安装为全局包。
- 全局包会被安装到 C:\Users\用户目录\AppData\Roaming\npm\node_modules 目录下。
- 注意：
    - 只有工具性质的包，才有全局安装的必要性。因为它们提供了好用的终端命令。
    - 判断某个包是否需要全局安装后才能使用，可以参考官方提供的使用说明即可。

#### 规范的包结构

1、一个规范的包，它的组成结构，必须符合以下 3 点要求：
- 包必须以单独的目录而存在
- 包的顶级目录下要必须包含 package.json 这个包管理配置文件
- package.json 中必须包含 name，version，main 这三个属性，分别代表包的名字、版本号、包的入口。

2、以上三点要求是一个规范的包结构必须遵守的格式，关于更多的格式约束，可参考：  
- <https://yarnpkg.com/zh-Hans/docs/package-json>


### 装包  
一、可以使用npm包管理工具，从服务器把需要的包下载到本地使用。    
- 从 <https://www.npmjs.com/> 网站上搜索自己所需要的包  
- 从 <https://registry.npmjs.org/> 服务器上下载自己需要的包

二、在项目中安装 包 的命令

```bash
# 1、一次性安装所有的包
    npm install
    # 可简写为：
    npm i

# 2、在项目中安装指定名称的包。 默认会自动安装最新版本的包
    npm install 包的完整名称
    # 可简写为：
    npm i 包的完整名称 

# 3、安装指定版本号的包
    npm i 包的完整名称@版本号
    # 比如：npm i moment@2.22.2 

# 4、卸载指定的包
npm uninstall 包的完整名称
```

三、初次装包后多了哪些文件

- 初次装包完成后，在项目文件夹下多一个叫做 `node_modules 的文件夹`和 `package-lock.json 的配置文件`。

- 其中：  
    - node_modules 文件夹用来存放所有已安装到项目中的包。require() 导入第三方包时，就是从这个目录中查找并加载包。
    - package-lock.json 配置文件用来记录 node_modules 目录下的每一个包的下载信息，例如包的名字、版本号、下载地址等。

- 注意：程序员不要手动修改 node_modules 或 package-lock.json 文件中的任何代码，npm 包管理工具会自动维护它们。


四、 npm 初体验

案例：格式化时间
```js
// 使用 npm 包管理工具，在项目中安装 格式化时间的包 moment
// 使用 require() 导入包。导入的名称，就是装包时候的名称
const moment = require('moment')
// 参考 moment 的官方 API 文档，调用对应的方法，对时间进行格式化
const dt = moment().format('YYYY-MM-DD HH:mm:ss')
console.log(dt) // 输出 2020-01-12 17：23：48
```

### 包管理配置文件

1、npm 规定，在`包的顶级目录中`，必须提供一个叫做 `package.json 的包管理配置文件`。用来记录与项目有关的一些配置信息。例如：  

- 项目的名称、版本号、描述等  
- `记录项目中安装了哪些包`  
- 哪些包只在开发期间会用到  
- 那些包在开发和部署时都需要用到  
 
2、第三方包的体积过大，不方便团队成员之间共享项目源代码。所以共享时要剔除node_modules

- 在项目根目录中，创建一个叫做 package.json 的配置文件，即可用来记录项目中安装了哪些包。从而方便剔除 node_modules 目录之后，在团队成员之间共享项目的源代码。

- 注意：今后在项目开发中，一定要`把 node_modules 文件夹`，`添加到 .gitignore 忽略文件中`。

3、`快速创建 package.json`

```bash
# 在执行命令时所处的目录中，快速创建 package.json 这个包管理配置文件
npm init -y

# 运行 npm install 命令安装包的时候，npm 包管理工具会自动把包的名称和版本号，记录到 package.json 中
# package.json 文件中，有一个 dependencies 节点，专门用来记录您使用 npm install 命令安装了哪些包。
```

4、devDependencies 节点

- 如果某些包只在项目开发阶段会用到，在项目上线之后不会用到，则建议把这些包记录到 devDependencies 节点中。

- 与之对应的，如果某些包在开发和项目上线之后都需要用到，则建议把这些包记录到 dependencies 节点中。

```bash
# 安装指定的包，并记录到 devDependencies 节点中
npm install 包的完整名称 --save-dev
# 简写形式：
npm i 包的完整名称 -D
```

### 解决下包速度慢的问题
一、速度慢的原因  
- 在使用 npm 下包的时候，默认从国外的服务器进行下载，此时，网络数据的传输需要经过漫长的海底光缆，因此下包速度会很慢。

二、解决办法

- `国内淘宝 NPM 镜像服务器`。淘宝在国内搭建了一个服务器，专门把国外官方服务器上的包同步到国内的服务器，然后在国内提供下包的服务。从而极大的提高了下包的速度。

- 切换 npm 的下包镜像源（服务器地址）：  

- 为了更方便的切换下包的镜像源，我们可以安装 nrm 这个小工具，利用 nrm 提供的终端命令，可以快速查看和切换下包的镜像源。

```bash
# 查看当前的下包镜像源
npm config get registry
# 将下包的镜像源 切换为 淘宝镜像源
npm config set registry = https://registry.npm.taobao.org/
# 检查镜像源是否下载成功
npm config get registry

# ---------------------------

# 利用 nrm 工具，快速查看和切换下包的镜像源
# 通过 npm 包管理器，将 nrm 安装为全局可用的工具
npm i nrm -g
# 查看所有可用的镜像源
nrm ls
# 将下包的镜像源 切换为 淘宝镜像
nrm use taobao
```



