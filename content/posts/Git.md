---
title: "Git的使用"
date: 2022-10-28T19:56:25+08:00
tags: ['Command-line Tool']
series: ['前端学习之旅']
---

## 版本控制系统
一、版本控制软件（系统）  
- 版本控制软件是一个用来记录文件变化，以便将来查阅特定版本修订情况的系统，因此有时也叫做“`版本控制系统`”。把手工管理文件版本的方式，改为由软件管理文件的版本；这个负责`管理文件版本的软件`，叫做“版本控制软件”。

- 好处：操作简便、易于对比、易于回溯、不易丢失、协作方便

二、版本控制系统的分类

1、本地版本控制系统
- 单机运行，使维护文件版本的操作工具化，不支持多人协作开发
- 版本数据库故障后，所有历史更新记录会丢失

2、集中化的版本控制系统
- 联网运行，支持多人协作开发；性能差、用户体验不好，客户端只保留最新的文件版本
- 客户端必须时刻和服务器相连
- 不支持离线提交版本更新，中心服务器崩溃后，所有人无法正常工作
- 典型代表：SVN、VCS

3、`分布式版本控制系统`
- 开源、最优的存储能力、容易做备份
- 支持离线操作，支持多人协作开发，容易定制工作流程
- 典型代表：`Git`
- Git是用C语言开发的

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

- 在Windows上使用Git，可以从Git官网直接下载安装程序，然后按默认选项安装即可。网址：<https://git-scm.com/downloads>

- 安装完成后，在开始菜单里找到 “Git Bash”，蹦出一个类似命令行窗口的东西，就说明Git安装成功！

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

一般我们总会有些文件无需纳入 Git 的管理，也不希望它们总出现在未跟踪文件列表。 在这种情况下，我们可以创建一个名为 `.gitignore 的配置文件`，列出要忽略的文件的匹配模式。

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.1ogrd69uxdkw.webp)

七、搭建Git服务器  

- GitHub就是一个免费托管开源代码的远程仓库。但是对于某些视源代码如生命的商业公司来说，既不想公开源代码，又舍不得给GitHub交保护费，那就只能自己搭建一台Git服务器作为私有仓库使用。

- 搭建Git服务器需要准备一台运行Linux的机器，强烈推荐用Ubuntu或Debian

八、使用SourceTree  

- Git有很多图形界面工具，这里我们推荐SourceTree，它是由Atlassian开发的免费Git图形界面工具（GUI工具），可以操作任何Git库。

- 首先从官网下载SourceTree并安装，然后直接运行SourceTree。

- 第一次运行SourceTree时，SourceTree并不知道我们的Git库在哪。如果本地已经有了Git库，直接从资源管理器把文件夹拖拽到SourceTree上，就添加了一个本地Git库：

- 也可以选择“New”-“Clone from URL”直接从远程克隆到本地。

九、标签管理 
- 创建标签
- 操作标签

### Git 分支操作
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


三、分支管理策略  
在实际开发中，我们应该按照几个基本原则进行分支管理：  

- 首先，master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；

- 那在哪干活呢？干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；

- 你和你的小伙伴们每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了。

四、.git文件里含有
- HEAD ：HEAD指向当前正在操作的分支或切换后的分支
- config : 配置的用户名、邮箱信息
- logs ：历史记录
- refs ：含有 heads分支内容、tags里程碑或标签内容


五、commit、tree、blob三者之间的关系
- .git里内容类型形式是：commit 已提交的、tree 文件夹或文件、blob 文件内容
- git里的存储，和文件名没有关系，内容相同的两个文件，只会当成一个进行存储，节省了空间。

六、关于分离头指针 detached HEAD
- HEAD 不仅可以指向分支，还可以指向某个commit，这时候就是叫分离头指针 detached HEAD
- 分离头指针： 是指不基于任何分支所创建的分支，就算commit了，当切换到其它分支时，git仓库很可能将其视为垃圾丢弃掉。所以当这个分支任务很重要时，一定要和其他分支绑定在一起



![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221207/image.5q42eo5mzww0.webp)


###  版本库

- 工作区就是在电脑里能看到的目录，比如我的`项目文件夹就是一个工作区`

- `工作区有一个隐藏目录.git`，这个不算工作区，而`是Git的版本库`。

- `Git的版本库里`存了很多东西，其中最重要的就是称为stage（或者叫index）的`暂存区`，还有Git为我们自动创建的第一个`分支`master，以及指向master的一个`指针叫HEAD`。HEAD指向当前正在操作的分支或切换后的分支

- Git比其他版本控制系统设计得优秀，因为`Git跟踪并管理的是修改，而非文件`

- 每次修改，如果不用git add到暂存区，那就不会加入到commit中。


git add 将工作区文件 添加到 暂存区：
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221122/image.2rotyv8hhv80.webp)

git commit 将暂存区文件 提交到 Git 仓库分支：
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221122/image.7d2y888644w0.webp)

图解：
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221207/image.7848l9yzeco0.webp)

## Git命令行

### 本地仓库管理
```js
// -----------------------
// config 的作用域 。 local优先级高于global
    git config --local 只对某个仓库有效
    git config --global 对当前用户所有仓库有效

// --------Git配置---------------

// 0、查看git版本 检查git是否安装成功
    git --version  
// 1、配置Git用户信息 
    git config --global user.name "MollyXu1995"
    git config --global user.email "MollyXu1995@gmail.com"
// 2、查看所有的全局配置项
    git config --global --list
// 3、查看指定的全局配置项
    git config user.name
    git config user.email
// 4、获得更简明的帮助 “help” 输出
    git config -h
    // 在浏览器中打开帮助手册
    git help config

// ---------建 Git仓库------------------

        pwd  // pwd命令 即显示当前工作的路径
        mkdir 文件夹名  // 创建文件夹
        cd 文件夹名  // 移动到这个文件夹
        ls   // 列出当前所在文件夹的内容
        ls -ah  // 显示 .git目录 。默认 是隐藏的

// 1. 把已有的项目代码 纳入 Git管理
    cd 项目文件夹名 // 移动到这个项目文件夹
    git init  // 纳入 Git追踪管理
    
// 2. 新建的项目直接用 Git管理
    git init 项目文件夹名  // 会在当前路径下创建项目文件夹 并纳入 Git追踪管理
    cd 项目文件夹名  // 移动到这个项目文件夹

// 3、把已建立的文件或文件夹放到 Git仓库 

    // （1）把工作区文件 放到 暂存区。 把文件或文件夹 进行Git跟踪管理。
    // 此命令是没有返回命令信息显示的。 可反复多次使用 或 全部添加 .
        git add 文件名
        git add 文件1 文件2 文件夹3
        git add .   // 全部文件

    // （2）把暂存区中的文件 提交到 Git仓库。
        git commit 
        git commit -m '提交描述'

    // （3）相当于以上两条命令的合并
        git commit -a
        git commit -a -m '提交描述'

// 4、查看各文件处于什么状态  工作树是否干净
    git status  
    // 查看文件处于什么状态 精简方式
    git status -s

// 5、告诉 Git你的 GitHub 账号。 注意是 user.username
    git config --global user.username 'MollyXu1995'

// 6、将本地仓库内容更新 推送到 远程仓库
    git push

// 7、将远程仓库内容 拉到 本地仓库
    git pull

// ---------------------------------------

// 1、查看区别
    // 查看commit和目前工作区文件的差异
    git diff
    // 查看不同分支上提交的指定文件的差异
    git diff temp master --文件名

// 2、查看提交的历史记录 从最近到最远的提交日志 下面查看形式可以组合用
    git log
    // 只查看最新的2条提交记录 数字可改
    git log -n2
    // 精简方式 展示历史记录
    git log --oneline
    git log -n3 --oneline
    // 查看所有分支 历史记录
    git log --all 
    // 查看某一分支 历史记录
    git log 分支名
    // 以图形化的方式展示历史记录
    git log --graph
    git log --oneline --all -n4 --graph

// 3、图形界面工具来查看版本历史
    gitk
    
// -------------------------------------

// 1、从暂存区中 取消对文件的暂存
git reset HEAD 要移除的文件名
// 2、从工作区中删除文件或文件夹
rm 文件名
// 3、从 Git仓库中删除文件
git rm 文件名
// 4、从 工作区 和 Git 仓库中同时删除对应的文件
git rm -f 文件名
// 5、只从 Git 仓库中移除指定的文件，但保留工作区中对应的文件
git rm --cached 文件名
// 6、 重命名文件或文件夹
git mv 原名称 新名称

// -------------------------------------

// 1、暂存区的文件更改不要了，恢复成当前HEAD的工作区内容
    git reset HEAD
    git reset HEAD --文件名

// 2、文件 回退到之前的版本 HEAD指向哪个版本号，就相当于把当前版本定位在哪。回退到了某一版本，之前的当前版本就没有了。 此命令慎用！！
    // 回退到 上一个版本 HEAD^
    git reset --hard HEAD^
    // 回退到 上上一个版本 HEAD^^
    git reset --hard HEAD^^
    // 回退到 往上100个版本 HEAD~100
    git reset --hard HEAD~100
    // 回退到 commit id 为 1094a 的版本
    git reset --hard 1094a
    
// 3、查看命令历史 以便确定要回到未来的哪个版本 即得到 commit id号 
    git reflog
    
// -----------------------

// 1、把文件在工作区的修改全部撤销。即让这个文件回到最近一次 git commit或git add时的状态。//无法恢复 慎重操作！// 
    // 场景一：改后还没有放到暂存区，现在撤销修改，就回到和版本库一模一样的状态；
    // 场景二：已经添加到暂存区后，又作了修改，现在撤销修改，就回到添加到暂存区后的状态。
    // 场景三：添加到了暂存区时，想丢弃修改，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作
    // 场景四：已经提交到版本库时，想要撤销本次提交，参考版本回退，不过前提是没有推送到远程库。
    // 用版本库里的版本替换工作区的版本
    git checkout -- 文件名

// -----------------------

// 更改已经 commit提交的 描述信息message
    // 当前分支的 最新一次 commit提交的 message修改
    git commit --amend
    // 交互式修改方式： 修改老旧的 commit提交的 message信息   r
    git rebase -i  其父亲的commit的id号

```

### 分支管理
```js
// ------------查看分支
// 1、查看当前 Git 仓库中所有的分支列表 
    // 分支名字前面的 * 号表示当前所处的分支
    git branch
    git branch --all

// ------------创建分支
// 2、基于当前分支，创建一个新的分支    switch 也可以换成 checkout
// 执行完创建分支的命令后，当前所指向的还是master分支，另需切换
    git branch 分支名称
    // 切换到指定的分支上进行开发
    git switch 分支名称 
// 创建指定名称的新分支，并立即切换到新分支上开发。相当于上面两条指令的合并 
    git switch -c 分支名称
// 基于 某分支上 创建新分支 并切换到新分支上
    git switch -b 新分支名称 某分支名

// 重新命名目前所在的 分支名
    git branch -m 原分支名 新分支名

// ------------合并分支
// 3、功能分支的代码开发测试完毕后，将完成后的代码合并到 master 主分支上
// 合并到哪，就必须先切换到哪，再运行 git merge 命令
    // 步骤1、先切换到 master 分支上
        git switch master 
    // 步骤2、运行 git merge命令，将某分支 合并到 master 分支上。Fast forward模式
        git merge 分支名称
        // 采用 --no-ff方式的 git merge 。即普通模式，合并后的历史有分支信息，能看出来曾经做过合并。而fast forward合并，就看不出来曾经做过合并，删除分支后，会丢掉分支信息。 
        git merge --no-ff -m "merge with no-ff" 分支名称

// ------------删除分支
// 4、功能分支的代码合并到 master 主分支上后，可以将对应的功能分支删除掉：
    git branch -d 分支名称

// 5、删除一个没有被合并过的分支，即强行删除命令
    git branch -D 分支名称

// 6、分支合并时 遇到代码发生冲突
// 如果在两个不同的分支中，对同一个文件进行了不同的修改，Git 就没法干净的合并它们。 此时，我们需要打开这些包含冲突的文件然后手动编辑解决冲突。
    // 步骤1
    git switch master 
    git merge 分支名称
    // 步骤2
    git add .
    git commit -m "解决了分支合并冲突的问题"

// 用带参数的 git log 命令 可以看到分支的合并情况
    git log --graph --pretty=oneline --abbrev-commit 

// 7、当手头工作还没有完成 没有提交，但现在要立刻先去修复别的 bug问题。可以先把当前工作现场 git stash “储藏”一下。修复后，再 git stash pop，恢复工作现场。
    // “储藏”下 当前工作现场
    git stash
    // 切换到 工作现场的分支
    git switch 分支名称
    // 恢复工作现场
    git stash pop

// 可查看 工作现场存到哪去了
git stash list
// 可以多次 stash，恢复之前，先用 git stash list查看，然后恢复指定的stash，用命令
git stash apply stash@{0}

// 8、bug分支 通过创建新的bug分支进行修复，然后合并，最后删除
// 首先确定要在哪个分支上修复bug，假定需要在master分支上修复，就从master创建临时分支。
// 比如 master分支上修复了bug后，但 dev分支是早期从master分支分出来的，所以，这个bug其实在当前dev分支上也存在。只需把 bug提交的修改“复制”到 dev分支
    // 切换到 dev 分支
    git switch 分支名称
    // 把 bug提交的修改“复制”到 dev分支 。比如提交修改的 commit id 为 4c805e2
    git cherry-pick 4c805e2

```

### 远程仓库管理
以下使用 SSH 协议：
```js
//-----------------------------------

// 先创建本地仓库，再将本地仓库 上传到 远程Github仓库

// 0、先创建 Github远程项目仓库 命名 和电脑上 本地仓库名一样

// 1、将已有的本地仓库 与 远程库关联。
// 本地链接远程的方式的名称 通常就叫 origin。 MollyXu1995 为 github账号名
git remote add origin git@github.com:MollyXu1995/本地项目仓库名.git

// 2、把本地库的所有内容推送到远程库上，即把当前分支master推送到远程。第一次推送时 加 -u 后面再推送就可以不用加了
git push -u origin master

// 3、只要本地作了提交，就可以通过此命令，将本地master分支的最新修改推送至GitHub
git push origin master 

// 4、可以先查看下远程库信息 有哪些远端连接
    git remote -v

// 5、解除 本地仓库 和 远程仓库 的关联关系
    // 解除  origin远程库
    git remote rm origin

// 6、完全删除远程库，需要登录到GitHub，在后台页面找到删除按钮再删除。

//-----------------------------------

// 先创建远程仓库，再将远程仓库 克隆到 本地仓库：

// 0、将别人的 github仓库，Create fork复制到自己的github账号下
        // 到别人github仓库下，页面上点击右上方的 fork 按鈕，你的账号中就会出现一份 仓库副本。右侧栏的地址就是你 fork 仓库的 GitHub地址。

// 1、将自己账号 远程仓库 克隆到 本地仓库。
// clone 到本地，会自动在本地建立一个文件夹，不需要自己建。并自动 与 自己的远端仓库相连接。
// 但注意终端命令位置路径，别移动到其它git仓库里了
git clone git@github.com:MollyXu1995/远程仓库名.git
cd 本地仓库名  // 移动到本地仓库

// 2、连接别人的 github远端仓库，这样自己的本地仓库 才会随着别人原始仓库的内容变化而更新
// 本地链接别人远程的方式的名称，通常都叫 upstream
git remote add upstream git@github.com:别人github账号名/本地项目仓库名.git

// 3、检查所有 remotes 指向地址信息，是否都设定正确 
git remote -v

// 4、可修改地址
git remote set-url 
```

下图是一个本地库连接两个远程。正常工作中，大家多个本地库，链接同一个远程库来工作。
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221207/image.3q4lc7cu12c0.webp)

本地和远端 连接正常，就是得有一个fetch，一个push。
- fetch 代表拉，从远端拉到本地
- push 代表推送，从本地推送到远端

![29d1afc08f8f526190a094fff785476](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221207/29d1afc08f8f526190a094fff785476.2qmbzmobjic0.webp)  


![248e7eb9a5596bc7076d6697c22a5d8](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221207/248e7eb9a5596bc7076d6697c22a5d8.32vxzk890zi0.webp)


## 使用Github
### 概念
一、了解开源  
- 开源即开放源代码（Open source code），代码是公开的，任何人都可以去查看，修改和使用开源代码
- 开源让学习变得容易，让开发越来越容易

二、开源项目托管平台

专门用于免费存放开源项目源代码的网站，叫做`开源项目托管平台`。  
- `Github`（`全球最牛的开源项目托管平台`，没有之一）
- `Gitlab`（对代码私有性支持较好，因此企业用户较多）
- `Gitee`（又叫做码云，是国产的开源项目托管平台。访问速度快、纯中文界面、使用友好）

注意：以上 3 个开源项目托管平台，`只能托管以 Git 管理的项目源代码`，因此，它们的名字都以 Git 开头。

三、GitHub仓库  

现在的情景是，你已经在本地创建了一个Git仓库后，又想在GitHub创建一个Git仓库，并且让这两个仓库进行远程同步，这样，GitHub上的仓库既可以作为备份，又可以让其他人通过该仓库来协作，真是一举多得。

### 注册Github账号
一、注册 Github 账号的流程   

① 访问 Github 的官网首页 https://github.com/  
② 点击“Sign up”按钮跳转到注册页面  
③ 填写可用的用户名、邮箱、密码  
④ 通过点击箭头的形式，将验证图片摆正  
⑤ 点击“Create account”按钮注册新用户  
⑥ 登录到第三步填写的邮箱中，点击激活链接，完成注册  

### 创建Github远程仓库

- 到 github.com 登入，然后按一下右上角的「+」号来新增一个仓库repository。
- 取一个名字，最好和你电脑上`本地仓库名一样`，并且给它一个简短的说明。
- 设定为「public（公开）。
- 不要勾选「initialize with a README」，因为我們已经在电脑上建立了一个，叫做「readme.txt」。
- 也不要修改 .gitignore 和 license 的设定，保留原先「none」 的设定就好。
- 按下「create repository」！

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.2un68y9vq1y0.webp)


一、远程仓库的两种访问方式  

1、你也许还注意到，GitHub给出的地址不止一个，还可以用https://github.com/michaelliao/gitskills.git这样的地址。实际上，Git支持多种协议，默认的git://使用ssh，但也可以使用https等其他协议。

2、Github 上的远程仓库，有两种访问方式，分别是 HTTPS 和 SSH。

3、Git支持多种协议，包括https，但ssh协议速度最快。

- HTTPS：`零配置`；但是每次访问仓库时，需要重复输入 Github 的账号和密码才能访问成功
- SSH：`需要进行额外的配置`；但是配置成功后，每次访问仓库时，不需重复输入 Github 的账号和密码

4、在实际开发中，`推荐使用 SSH` 的方式访问远程仓库。


### 关于 SSH key

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
④ 在 Title 文本框中任意填写一个名称，来标识这个 Key 从何而来。也可不写

4、检测 Github 的 SSH key 是否配置成功

打开 Git Bash，输入如下的命令并回车执行：
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.1caeccmd39r4.webp)
上述的命令执行成功后，可能会看到如下的提示消息：
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.3x17ps40qz60.webp)
`输入 yes 回车`之后，如果能看到类似于下面的提示消息，证明 SSH key 已经配置成功了：
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20221108/image.3e41gaunfkm0.webp)


## 参考

{{< card "https://www.liaoxuefeng.com/wiki/896043488029600" >}}   
     
{{< card "https://humble-blog.vercel.app/git/" >}}        




