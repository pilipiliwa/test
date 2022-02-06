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

```rm <file>``` 工作区文件删除

`git rm <file> `并 `git commit` 从版本库中删除

### 远程仓库

#### PC操作：

git-bash-shell

```
$ ssh-keygen -t rsa -C "youremail@example.com"
```

用户目录`.ssh`目录

`id_rsa` 和 `id_rsa.pub`两个SSH Key秘钥对

`id_rsa`私钥，不能泄露出去，

`id_rsa.pub`是公钥，可以放心地告诉任何人

#### git操作：
右上角头像--`setting`--`SSH and GPG keys`-- `new SSH key`---`随意title`---`复制公钥key`---`Add SSH key`---done

#### PC操作：

本地链接：本地库下运行命令：

`git remote add origin git@github.com:<github_account>/<repository_name>.git`

`origin`为远程库的名称，可自改

#### 推送本地库内容至远程库

`git push -u origin master`(需输入yes确认推送上传)

### 删除远程库（解除本地和远程的绑定关系）

`git remote rm <name>`

使用前，建议先用`git remote -v`查看远程库信息：

真正删除远程库，需登录GitHub，后台页面删除