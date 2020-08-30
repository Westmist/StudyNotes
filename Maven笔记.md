### <center>Maven笔记</center>
#### 一、概念
Apache Maven，是一个软件（特别是Java软件）项目管理及自动构建工具，由Apache软件基金会所提供。基于项目对象模型（缩写：POM）概念，Maven利用一个中央信息片断能管理一个项目的构建、报告和文档等步骤.  
#### 二、Maven的安装  
1.下载
> 安装Maven需要先配置Java环境
> 下载[Maven](https://maven.apache.org/download.cgi)，解压  

2.配置环境  
和配置Java环境的方式相同，系统 --> 高级系统设置 --> 环境变量 --> 系统变量
> 新建变量`MAVEN_HOME`，路径为Maven的主目录  
> 配置bin路径，在Path变量中添加值`%Maven%\bin`  

3.检查
在命令提示符中输入`mvn -v`, 输出Maven的版本信息

#### 三、Maven配置  
1.创建一个本地文件repository作为仓库用于存储jar包
2.更改Maven的配置文件conf\settings.xml
```xml
<!-- 在setting标签中添加如下标签，配置本地仓库路径 -->
<localRepository>Your_Maven_Repository_Path</localRepository>
<!-- 使用Linux的目录分割符 -->
```
3.更改镜像仓库(可选)
```xml
<!-- 将默认的镜像更改为阿里的公共镜像源 -->
<!-- 在<mirrors>标签之间添加如下配置 -->
<id>alimaven</id>
<name>aliyun maven</name>
<url>http://maven.aliyun.com/nexus/content/groups/public/</url>
<mirrorOf>central</mirrorOf>
```
#### 四、Maven集成到IntellJ IDEA
打开IDEA的设置
![Maven](./images/Maven.png)
发现IDEA有默认的Maven，遂卒！！！

#### 五、在IDEA中使用Maven
创建Maven项目，只需在创建项目时选择Maven，其余步骤和创建普通项目相同
![MavenB](./images/MavenB.png)
项目创建成功后会自动自动下载jar包和对象模型到仓库  
至此，一个标准的目录结构就建好了，导入项目依赖也只需要配置pom.xml就可以实现，可以开始快乐的编码了.
