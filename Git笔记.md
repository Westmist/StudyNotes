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
------------------------------
 * 图片
------------------------------

