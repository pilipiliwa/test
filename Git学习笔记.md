# Git学习笔记
## 起步
### 安装
#### Linux：

`sudo apt-get install git`

#### Windows：

从Git官网[下载](https://git-scm.com/downloads)安装

安装完成后，在开始菜单里找到“Git”->“Git Bash”，启动Git
## 使用Git
## 初始化Git仓库命令

```git init```

### 添加文件到git仓库暂存区（stage）

```git add <file1( , file2,file3)>```

### 提交文件到git库（可以多次添加一次提交）

```git commit -m "this is a description"```

### 查看仓库当前的状态

```git status```

查看是否有未提交修改

### 查看文件修改了什么

```git diff <file>```



#### ```HEAD``` 表示当前版本 ```HEAD^ ```上一版本 ```HEAD^^```上上版本 ```HEAD^^^``` 上上上版本 ```HEAD~100```上100版本

### 版本回退 

``` git reset --hard HEAD^```

```git reset --hard commit_ID```

用`git log`可以查看提交历史，以便确定要回退到哪个版本

要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本

### 丢弃修改

丢弃工作区文件修改

`git checkout -- file`

1、未保存至暂存区，丢弃工作区修改，撤销修改回退到与版本库一致状态

2、已保存至暂存区，丢弃工作区修改，撤销修改回退到与暂存库一致状态

##### 丢弃暂存区文件修改

`git reset HEAD <file>`

将暂存区的修改撤销

### 删除文件

```rm <file>```   // 工作区文件删除

`git rm <file> `并 `git commit` 从版本库中删除

## 远程仓库

### PC操作：

git-bash-shell

```
$ ssh-keygen -t rsa -C "youremail@example.com"
```

用户目录`.ssh`目录

`id_rsa` 和 `id_rsa.pub`两个SSH Key秘钥对

`id_rsa`私钥，不能泄露出去，

`id_rsa.pub`是公钥，可以放心地告诉任何人

### git操作：
右上角头像--`setting`--`SSH and GPG keys`-- `new SSH key`---`随意title`---`复制公钥key`---`Add SSH key`---done

### PC操作：

本地链接：本地库下运行命令：

`git remote add origin git@github.com:<github_account>/<repository_name>.git`

`origin`为远程库的名称，可自改(下同)

### 推送本地库内容至远程库

`git push -u origin master`(需输入yes确认推送上传)

`git push origin <name>`

### 删除远程库（解除本地和远程的绑定关系）

`git remote rm <name>`

使用前，建议先用`git remote -v`查看远程库信息：

真正删除远程库，需登录GitHub，后台页面删除

### 查看远程库信息

` git remote` 

`git remote -v `   //显示更详细信息

### 远程库克隆

`git clone git@github.com:<github_account>/<repository_name>.git`

git支持多种协议，包括HTTPS，但SSH最快

#### 远程库的分支克隆至本地

`git checkout -b dev origin/dev`   //创建本地dev分支

`git branch --set-upstream-to=origin/dev dev`  //将本地dev与origin/dev链接起来

### 将远程库某个分支的更新取回至本地

`git pull origin  <branch>: <local_baranch>`

## 分支管理

`git checkout -b dev`   //创建dev分支 -b表示创建并切换相当于两条命令

```
git branch <name>  //创建分支

git checkout <name> //切换分支

```

`git branch`     //查看当前分支 当前分支有*标识

`git merge <name>`  //将< name>分支合并到master分支上

`git branch -d <name>`  // 删除< name >分支

`git branch -D <name>`  //强制删除，无视Git提醒

`git switch <name>`  //切换分支

`git switch -c <name>`   //创建并切换分支

`git log --graph`   //查看分支合并图

`git merge --no-ff -m "merge with no-ff" <branch_name>`不使用快速合并(Fast forward)

## 临时存储功能

`git stash`   //将当前工作区“存储起来”，等恢复现场后继续工作

`git stash apply `  //恢复

`git  stash drop `  //删除

`git stash pop`   /恢复并删除

`git stash list`   //恢复列表

`git stash apply stash@{0}`    //恢复指定的stash

 ## 将其他分支的修改提交至当前分支

`git cherry-pick <commit>`





