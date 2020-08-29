### <center>Git学习笔记</center>
#### 一、概念
Git是著名的分布式版本控制软件，Linux内核的开发中用的版本控制软件就是Git  
#### 二、Git的安装与准备
1.安装Git
Git依赖Node,js环境，需先安装[Node.js](https://nodejs.org/zh-cn/download/)  
安装[Git](https://git-scm.com/downloads)，只需要一路Next  

2.安装检查  
在任意路径右键鼠标打开'Git Bash'
```shell
$ node -v
$ git --version
```
两行命令都分别显示正确的Node版本号和Git版本号，即表明Git安装成功  

3.Git初始化
首次使用Git需要设置用户名和邮箱，否则无法进行`commit`等操作
```shell
$ git config --global user.name "yourname"
$ git config --global user.email youremail@example.com
```
4.初始化一个本地仓库
创建或选择一个本地文件夹作为git仓库，初始化仓库
```shell
$ git init
```
#### 三、Git的基础操作
[Git结构](./Images/git.jpg)

* workspace：工作区
* Index/staging area：暂存区/缓存区
* local repository：本地仓库
* remote repository：远程仓库


```shell
$ git add filepath     #将文件filepath添加到缓存区，进行追踪
$ git status -s      #查看仓库当前的状态，显示有变更的文件
$ git commit -m "提交备注" filepath    #将暂存区的文件filepath提交到仓库，必须有提交备注
$ git log             #查看历史提交记录
$ git checkout  ID    #回退到指定ID的commit版本，ID使用git status命令查看    

#1.SSH到Github
#2.在本地的/c/user/user_name/.ssh中添加密钥对
#3.将公钥添加到Github账户中
$ ssh -T git@github.com     #检查确认

$ git remote add origin master  Git_URL  #添加远程仓库Git_URL
$ git pull origin master     #从远程仓库拉取文件并合并
$ git push origin master     #将本地仓库推送到远程库并合并
```
#### 四、Git分支管理
Git的分支功能可以支持同时进行多个功能的开发和版本管理
```shell
$ git branch branchname     #创建名为branchname的分支
$ git branch                #列出所有分支
$ git checkout branchname   #切换到branchname分支
$ git merge branchname      #将branchname分支合并到主分支中，合并完后就可以删除分支
$ git branch -d branchname  #删除branchname分支
```