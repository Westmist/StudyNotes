### <center>初识 AOP</center>

#### 一、概念
面向切面的程序设计（Aspect-oriented programming，AOP，又译作面向切面编程、剖面导向程序设计）是计算机科学中的一种程序设计思想，旨在将横切关注点与业务主体进行进一步分离，以提高程序代码的模块化程度.

#### 二、Spring 中基于 AOP 的 XML 架构 Demo

##### 1. 要使用 aop 命名空间标签，需要导入 spring-aop j 架构.
Spring 配置文件<code>ApplicationContext.xml</code>内容如下:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:aop="http://www.springframework.org/schema/aop"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
    http://www.springframework.org/schema/beans/spring-beans-3.0.xsd
    http://www.springframework.org/schema/aop
    http://www.springframework.org/schema/aop/spring-aop-3.0.xsd ">

    <aop:config>
        <aop:aspect id="log" ref="AOPdemo">
            <aop:pointcut id="selectAll"
                          expression="execution(* com.springdemo.*.*(..))"/>
            <aop:before pointcut-ref="selectAll" method="beforeAdvice"/>
            <aop:after pointcut-ref="selectAll" method="afterAdvice"/>
            <aop:after-returning pointcut-ref="selectAll"
                                 returning="retVal"
                                 method="afterReturningAdvice"/>
            <aop:after-throwing pointcut-ref="selectAll"
                                throwing="ex"
                                method="AfterThrowingAdvice"/>
        </aop:aspect>
    </aop:config>

    <!-- 配置 id为'student'的 bean -->
    <bean id="student" class="com.springdemo.Student">
        <property name="name"  value="明轩" />
        <property name="age"  value="18"/>
    </bean>

    <!-- 配置切面类 AOPdemo -->
    <bean id="AOPdemo" class="com.springdemo.AOPdemo"/>
</beans>
```

##### 2. 定义各个切点(Pointcut)的调用方法，AOPdemo.java 的内容如下:

```java
package com.springdemo;

public class AOPdemo {
    // 该方法在被选择的方法(selectAll)执行之前执行
    public void beforeAdvice(){
        System.out.println("开始执行");
    }

    // 该方法在被选择的方法(selectAll)执行之后执行
    public void afterAdvice(){
        System.out.println("执行完成！");
    }

    // 当方法 return 返回值时执行该方法
    public void afterReturningAdvice(Object retVal){
        System.out.println("正在返回：" + retVal.toString() );
    }

    // 抛出异常时执行该方法
    public void AfterThrowingAdvice(IllegalArgumentException ex){
        System.out.println("出现异常: " + ex.toString());
    }
}
```

##### 3.Bean 文件 Student.java 中的内容为：

```java
package com.springdemo;

public class Student {
    private Integer age;
    private String name;
    public void setAge(Integer age) {
        this.age = age;
    }
    public Integer getAge() {
        System.out.println("Age : " + age );
        return age;
    }
    public void setName(String name) {
        this.name = name;
    }
    public String getName() {
        System.out.println("Name : " + name );
        return name;
    }
    public void printThrowException(){
        System.out.println("执行打印异常方法");
        throw new IllegalArgumentException();
    }
}
```

##### 4. 在 Main 方法中执行 demo

```java
package com.springdemo;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class Main {
    public static void main(String[] args) {
        ApplicationContext context =
                new ClassPathXmlApplicationContext("ApplicationContext.xml");
        Student student = (Student) context.getBean("student");
        student.getName();
        student.getAge();
        student.printThrowException();
    }
}
```

##### 5. Demo 运行成功则在终端输出如下信息:

```log
开始执行
Name : 明轩
执行完成！
正在返回：明轩
······
开始执行
执行打印异常方法
执行完成！
出现异常: java.lang.IllegalArgumentException
更多异常信息·····
```

#### 三、通知类型

| 通知 | 描述 |
| -------- | -------------------------------------------- |
| 前置通知  | 在一个方法执行之前，执行通知 |
| 后置通知  | 在一个方法执行之后，不考虑其结果，执行通知 |
|返回后通知| 在一个方法执行之后，只有在方法成功完成时，才能执行通知 |
|抛出异常后通知| 在一个方法执行之后，只有在方法退出抛出异常时，才能执行通知 |
|环绕通知| 在建议方法调用之前和之后，执行通知 |