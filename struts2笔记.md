### <center>Strut2笔记</center>
#### 概念
* strut2 遵循 MVC 规范
* 侵入性：如果必须要去继承框架的类或实现框架的接口，则表明该框架具有侵入性
#### 配置
* struts的表单需要添加对象名，形如：`user.name`
* Maven项目中加载多个Struts配置文件，还需要在项目结构中手动添加配置文件
* 包含规则如下：
`<include file="struts-configure/system.xml"></include>`

#### 校验
* 校验配置文件必须和Action类在同一包下，命名规则为: action类名+`-validation.xml`
* 如果配置校验器需要在struts配置文件的action标签中配置input结果集

#### 文件上传
* 文件上传表单必须是post方式提交且带enctype属性
* struts2自带文件上传过滤器，在action类的文件字段属性中
```java
    // 与表单字段名相同
    private File file;
    // 文件类型，命名规则固定为File对象+ContextType
    private String fileContextType;
    // 文件名，命名规则固定为File对象+FileName
    private String fileFileName;
```

#### 要使用注解需要额外的依赖
`struts2-convention-plugin`

#### 踩坑
* struts报错
需要引入配置文件到项目，且主配置文件的名称必须为`struts.xml`
![struts引入配置](F:/Git/StudyNotes/Images/strut-config.png)
* 删除项目后还需要注意Tomcat的缓存