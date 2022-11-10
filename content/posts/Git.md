---
title: "Git的使用"
date: 2022-10-28T19:56:25+08:00
tags: ['Command-line Tool']
series: ['前端学习之旅']
---

## 关于版本控制
一、版本控制软件（系统）  
- 版本控制软件是一个用来记录文件变化，以便将来查阅特定版本修订情况的系统，因此有时也叫做“`版本控制系统`”。把手工管理文件版本的方式，改为由软件管理文件的版本；这个负责`管理文件版本的软件`，叫做“版本控制软件”。

- 好处：操作简便、易于对比、易于回溯、不易丢失、协作方便

二、版本控制系统的分类

1、本地版本控制系统
- 单机运行，使维护文件版本的操作工具化，不支持多人协作开发
- 版本数据库故障后，所有历史更新记录会丢失

2、集中化的版本控制系统
- 联网运行，支持多人协作开发；性能差、用户体验不好，客户端只保留最新的文件版本
- 不支持离线提交版本更新，中心服务器崩溃后，所有人无法正常工作
- 典型代表：SVN

3、`分布式版本控制系统`
- 补足了以上两者的缺点
- 联网运行，支持多人协作开发；性能优秀、用户体验好
- 典型代表：`Git`

## Git
### Git概念
一、什么是Git  

Git 是一个`开源的分布式版本控制系统`，是目前世界上最先进、最流行的版本控制系统。可以快速高效地处理从很小到非常大的项目版本管理。

特点：项目越大越复杂，协同开发者越多，越能体现出 Git 的高性能和高可用性！  

特性：
1. 直接记录完整的文件快照，而非差异比较；
2. 近乎所有操作都是本地执行（只需要访问本地文件和资源）；

二、Git中的三个区域、三种状态  

使用 Git 管理的项目，拥有三个区域，分别是工作区、暂存区、Git 仓库。  

三种状态：  
- 已修改：表示修改了文件，但还没将修改的结果放到暂存区  
- 已暂存：表示对已修改文件的当前版本做了标记，使之包含在下次提交的列表中  
- 已提交：表示文件已经安全地保存在本地的 Git 仓库中  

三、基本的 Git 工作流程  
1. 在工作区中修改文件
2. 将你想要下次提交的更改进行暂存
3. 提交更新，找到暂存区的文件，将快照永久性存储到 Git 仓库

### Git的安装与配置
一、下载  
- 在开始使用 Git 管理项目的版本之前，需要将它安装到计算机上。  
- 网址：<https://git-scm.com/downloads>

二、配置用户信息    
- 安装完 Git 之后，要做的第一件事就是`设置自己的用户名和邮件地址`。因为通过 Git 对项目进行版本管理的时候，Git 需要使用这些基本信息，来记录是谁对项目进行了操作。  
- 注意：如果使用了 --global 选项，那么该命令只需要运行一次，即可永久生效。

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.4hyd5p092lg0.webp)

三、Git 的全局配置文件  
- 通过 git config --global user.name 和 git config --global user.email 配置的用户名和邮箱地址，会被写入到 C:/Users/用户名文件夹/.gitconfig 文件中。
- 这个文件是 Git 的全局配置文件，配置一次即可永久生效。可以使用记事本打开此文件，从而查看自己曾经对 Git 做了哪些全局性的配置。

四、检查配置信息  
除了使用记事本查看全局的配置信息之外，还可以运行如下的终端命令，快速的查看 Git 的全局配置信息：

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.pejupmzg6.webp)


### Git 的基本操作
一、获取 Git 仓库的两种方式  

① 将尚未进行版本控制的本地目录转换为 Git 仓库  
② 从其它服务器克隆一个已存在的 Git 仓库  

以上两种方式都能够在自己的电脑上得到一个可用的 Git 仓库

二、在现有目录中初始化仓库 

如果自己有一个`尚未进行版本控制的项目，用 Git 来控制它`，需要执行如下两个步骤：  
1. 在项目目录中，通过鼠标右键打开“`Git Bash`”
2. 执行 `git init 命令`将当前的目录转化为 Git 仓库

git init 命令会创建一个名为 .git 的隐藏目录，这个 .git 目录就是当前项目的 Git 仓库，里面包含了初始的必要文件，这些文件是 Git 仓库的必要组成部分。


三、工作区中文件的 4 种状态

- 未被Git 管理：未跟踪（Untracked）

- 已被Git 管理：未修改（Unmodified）、已修改（Modified）、已暂存（Staged）

Git 操作的终极结果：让工作区中的文件都处于“未修改”的状态。


四、检查文件的状态

1、使用 `git status` 输出的状态报告很详细
- Untracked files 未跟踪
- Changes to be committed 已被跟踪，并处于暂存状态
- Changes not staged for commit 已跟踪文件的内容发生了变化，但还没有放到暂存区。
- nothing to commit,working to clean 工作区中所有的文件都处于“未修改”的状态，没有任何文件需要被提交。

2、使用`git status -s`，以精简的方式显示文件的状态
- 红色的 ?? 标记。未跟踪
- 绿色的 A 标记。已被跟踪，并处于暂存状态
- 红色的 M 标记。修改过的、没有放入暂存区的文件
- 绿色的 M 标记。已修改，并处于暂存状态

五、Git工作流程

- 标准流程：工作区 → 暂存区 → Git 仓库  
- 可简化为：工作区 → Git 仓库

六、忽略文件  

一般我们总会有些文件无需纳入 Git 的管理，也不希望它们总出现在未跟踪文件列表。 在这种情况下，我们可以创建一个名为 .gitignore 的配置文件，列出要忽略的文件的匹配模式。

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.1ogrd69uxdkw.webp)


```js
// 终端命令 //

// 配置Git用户信息
git config --global user.name " MollyXu1995"
git config --global user.email "MollyXu1995@gmail.com"
// 查看所有的全局配置项
git config  --list --global
// 查看指定的全局配置项
git config user.name
git config user.email
// 在浏览器中打开帮助手册
git help config
// 获得更简明的帮助“help”输出
git config -h

// 查看文件处于什么状态
git status 
// 查看文件处于什么状态 精简方式
git status -s 

// 1.跟踪新文件；2.已跟踪的、且已修改的文件放到暂存区；3.把有冲突的文件标记为已解决状态
git add 文件名

// 提交更新 将暂存区中的文件，提交到 Git 仓库
git commit 
// 提交更新 并对提交的更新内容做进一步的描述
git commit -m "提交描述"
// 跳过暂存区，将工作区中已跟踪修改的文件 直接提交到 Git 仓库
git commit -a -m "提交描述"

// 把对工作区中的文件，还原成 Git 仓库中所保存的版本
// 工作区中文件所有的修改会丢失，且无法恢复。//慎重操作！// 
git checkout -- 文件名

// 将所有新增和修改的文件 全部加入暂存区
git add .

// 从暂存区中 取消对文件的暂存
git reset HEAD 要移除的文件名

// 从 Git 仓库和工作区中同时移除对应的文件
git rm -f 文件名
// 只从 Git 仓库中移除指定的文件，但保留工作区中对应的文件
git rm --cached 文件名

// 查看提交历史 最近的排在最上面
git log
// 查看提交历史 只展示最新的2条提交 数字可改
git log -2
```

### Git 分支  
#### Git本地分支操作
分支在实际开发中的作用：  
- 在进行多人协作开发的时候，为了防止互相干扰，提高协同开发的体验，建议每个开发者都基于分支进行项目功能的开发，例如：
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.5ew9kp6j8rw0.webp)

一、`master 主分支`

- 在初始化本地 Git 仓库的时候，Git 默认已经帮我们创建了一个名字叫做 master 的分支。通常我们把这个 master 分支叫做主分支。
- 在实际工作中，master 主分支的作用是：`用来保存和记录整个项目已完成的功能代码`。
- 因此，`不允许程序员直接在 master 分支上修改代码`，因为这样做的风险太高，容易导致整个项目崩溃。

二、功能分支
- 由于程序员不能直接在 master 分支上进行功能的开发，所以就有了功能分支的概念。
- 功能分支指的是专门`用来开发新功能的分支`，它是临时从 master 主分支上分叉出来的，当新功能开发且测试完毕后，最终需要合并到 master 主分支上。

```js
// 查看当前 Git 仓库中所有的分支列表 
// 分支名字前面的 * 号表示当前所处的分支
git branch

// 基于当前分支，创建一个新的分支
// 执行完创建分支的命令后，当前所指向的还是master分支，另需切换
git branch 分支名称

// 切换到指定的分支上进行开发
git checkout 分支名称

// 创建指定名称的新分支，并立即切换到新分支上
git checkout -b 分支名称

// 功能分支的代码开发测试完毕后，将完成后的代码合并到 master 主分支上
// 合并到哪，就必须先切换到哪，再运行 git merge 命令
    // 步骤1、先切换到 master 分支上
        git checkout master 
    // 步骤2、运行git merge命令，将某分支 合并到 master 分支上
        git merge 分支名称

// 功能分支的代码合并到 master 主分支上后，还可以删除对应的功能分支：
git branch -d 分支名称

// 分支合并时 遇到代码发生冲突
// 如果在两个不同的分支中，对同一个文件进行了不同的修改，Git 就没法干净的合并它们。 此时，我们需要打开这些包含冲突的文件然后手动解决冲突。
    // 步骤1
    git checkout master 
    git merge 分支名称
    // 步骤2
    git add .
    git commit -m "解决了分支合并冲突的问题"
```


#### Git远程分支操作

```js
// 将本地分支推送到远程仓库 只在第一次推送分支需要带 -u 参数
git push -u 远程仓库的别名 本地分支名称:远程分支名称
// 若希望 远程分支名称 和 本地分支名称 一样，可以简化命令
git push -u 远程仓库的别名 本地分支名称

// 查看远程仓库中所有的分支列表
git remote show 远程仓库名称

// 从远程仓库中，把远程分支下载到本地仓库中，保持 本地分支和远程分支 名称相同
git checkout 远程分支的名称
// 从远程仓库中，把远程分支下载到本地仓库中，并把下载的本地分支进行重命名
git checkout -b 本地分支名称 远程仓库名称/远程分支名称

// 从远程仓库，拉取远程分支最新的代码下载到本地对应的分支中 从而保持代码一致
git pull

// 删除远程仓库中指定的分支
git push 远程仓库名称 -- delete 远程分支名称
```


## Github
### 开源概念
一、了解开源  
- 开源即开放源代码（Open source code），代码是公开的，任何人都可以去查看，修改和使用开源代码
- 开源让学习变得容易，让开发越来越容易

二、开源项目托管平台

专门用于免费存放开源项目源代码的网站，叫做`开源项目托管平台`。  
- `Github`（`全球最牛的开源项目托管平台`，没有之一）
- Gitlab（对代码私有性支持较好，因此企业用户较多）
- Gitee（又叫做码云，是国产的开源项目托管平台。访问速度快、纯中文界面、使用友好）

注意：以上 3 个开源项目托管平台，`只能托管以 Git 管理的项目源代码`，因此，它们的名字都以 Git 开头。

### 注册Github账号
一、注册 Github 账号的流程   

① 访问 Github 的官网首页 https://github.com/  
② 点击“Sign up”按钮跳转到注册页面  
③ 填写可用的用户名、邮箱、密码  
④ 通过点击箭头的形式，将验证图片摆正  
⑤ 点击“Create account”按钮注册新用户  
⑥ 登录到第三步填写的邮箱中，点击激活链接，完成注册  

### Github 远程仓库的使用
一、新建空白远程仓库

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.2un68y9vq1y0.webp)

二、远程仓库的两种访问方式  

Github 上的远程仓库，有两种访问方式，分别是 HTTPS 和 SSH。  
- HTTPS：`零配置`；但是每次访问仓库时，需要重复输入 Github 的账号和密码才能访问成功
- SSH：`需要进行额外的配置`；但是配置成功后，每次访问仓库时，不需重复输入 Github 的账号和密码

注意：在实际开发中，`推荐使用 SSH` 的方式访问远程仓库。

三、基于 HTTPS 将本地仓库上传到 Github

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.3cpx754qx6w0.webp)

四、SSH key

1、关于SSH key   
配置 Github 的 SSH 访问  

SSH key 的作用：实现本地仓库和 Github 之间免登录的加密数据传输。  
SSH key 的好处：免登录身份认证、数据加密传输。  
SSH key 由两部分组成，分别是：  
- id_rsa（私钥文件，存放于客户端的电脑中即可）
- id_rsa.pub（公钥文件，需要配置到 Github 中）

2、生成 SSH key  
- 打开 Git Bash
- 粘贴如下的命令，并将 your_email@example.com 替换为注册 Github 账号时填写的邮箱：  
    - ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
- 连续敲击 3 次回车，即可在 C:\Users\用户名文件夹\.ssh 目录中生成 id_rsa 和 id_rsa.pub 两个文件

3、配置 SSH key  

① 使用记事本打开 id_rsa.pub 文件，复制里面的文本内容  
② 在浏览器中登录 Github，点击头像 -> Settings -> SSH and GPG Keys -> New SSH key  
③ 将 id_rsa.pub 文件中的内容，粘贴到 Key 对应的文本框中  
④ 在 Title 文本框中任意填写一个名称，来标识这个 Key 从何而来  

五、检测 Github 的 SSH key 是否配置成功

打开 Git Bash，输入如下的命令并回车执行：
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.1caeccmd39r4.webp)
上述的命令执行成功后，可能会看到如下的提示消息：
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.3x17ps40qz60.webp)
输入 yes 之后，如果能看到类似于下面的提示消息，证明 SSH key 已经配置成功了：
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.3e41gaunfkm0.webp)


六、基于 SSH 将本地仓库上传到 Github

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.4kjlzqybe0w0.webp)


七、将远程仓库克隆到本地  
打开 Git Bash，输入如下的命令并回车执行：

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.d5tph4hjwqo.webp)






