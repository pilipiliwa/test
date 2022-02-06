## 前言
写过毕业论文的都知道，一篇文章需要经过反复修改，往往我们通过复制文件对其进行重命名进行版本的标识。这样不仅浪费存储空间，同时，文件管理起来也相当不便。Git作为常用的版本分布式管理软件有效地解决了这一问题，让我们可以对每次改动进行有效的管理；Pandoc是常用的标记语言转换工具，可实现不同标记语言间的转换（HTML、Word、Ebooks、PDF、TeX…）。下面介绍使用Git+Pandoc的搭建过程。

## 准备工作
### 系统环境

win + git  + pandoc 

### 软件安装

[Git](https://github.com/jgm/pandoc/releases/tag/2.7.3)官网下载，一路next，记住安装路径
[Pandoc](https://github.com/jgm/pandoc/releases)安装同上，一路next，记住自己的安装路径。
配置环境变量

找到pandoc的安装路径，我的是 C:\Users\user_name\AppData\Local\Pandoc
我的电脑→属性→高级系统设置→环境变量→Path→编辑（将上述路径加入即可）
配置文件

找到git的安装路径，打开配置文件 .config （*\Git\mingw64\etc)

**或**加入以下内容（在公盘里加也可以，C:\Users\user_name，找到.gitconfig文件，对其进行修改
```
[diff "pandoc"]
    textconv=pandoc --to=markdown
    prompt = false
[alias]
    wdiff = diff --word-diff=color --unified=1
```

在工程目录下（就是你写word的文件）新建一个文本，后缀改成.gitattributes，里面内容写入
`*.docx diff=pandoc   //doc也行`
至此，全部准备工作已就绪，下面开始写作

### 配置git

#### Git配置用户名，邮箱

你想放置doc文件的目录下右击→Git Bash Here **或** 打开powershell
    `git config --global user.name  "username" ` 英语标点
    `git config --global user.email  "email"` 
#### 新建文档
目录下新建一个测试doc，命名为test.docx,内容随便敲点上去；保存，退出。

该目录下右击→Git Bash Here

`git init`      //目录初始化

`git add . `    //将该目录下所有文件添加至暂存区（相当于把目录下的文件加入一个仓库方便你管理）

`git add <file>`  //添加一个文件至暂存区

`git commit -m "新建一个文件"`    //提交至Git库 " "中为本次提交的简要描述

修改文档保存后退出，再次打开命令行工具

`git wdiff`     //查看修改的地方


可以看到，白字是之前的版本，绿色字体是新增的改动，要是觉得这一版本已经OK，我们同样可以对其进行标识：

`git commit -am "这是第二次改动"`
想要查看历史版本号，我们可以输入
`git log file.docx`   //查看历史版本/日志
commit后面的版本号就是我们要用到的东西，下面进行版本回退：
`git reset --hard version`   //version就是刚刚commit后面的版本号

打开Word，发现内容已经回退到最初的版本：


### 常用Git语法
`git init `                   //初始化
`git add file.doc  `          //加入指定文件，全部添加请直接 git add .
`git commit -am` "版本标识符"  //版本标号
`git wdiff  `                 //查看当前改动
`git log   `                  //查看历史版本
`git reset --hard vesion`     //版本回退
`git status`                  //查看当前数据
`pandoc -s file.docx -t markdown -o file.md `  //pandoc可直接进行文件转换；这里是将.docx转换为.md文件，在相应的工程目录下会多出一个markdown文件

**end.**