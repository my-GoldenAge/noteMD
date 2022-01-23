# 分布式系统中的相关概念

## 1、大型互联网项目架构目标

**传统项目和互联网项目**

<img src="img(dubbo)/image-20220123100652377.png" alt="image-20220123100652377" style="zoom:80%;" />

**互联网项目特点：**

- 用户多
- 流量大，并发高
- 海量数据
- 易受攻击
- 功能繁琐
- 变更快

### 衡量网站的性能指标

> 响应时间：指执行一个请求从开始到最后收到响应数据所花费的总体时间。
>
> 并发数：指系统同时能处理的请求数量。
>
> - 并发连接数：指的是客户端向服务器发起请求，并建立了TCP连接。每秒钟服务器连接的总TCP数量
> - 请求数：也称为QPS(Query Per Second) 指每秒多少请求.
> - 并发用户数：单位时间内有多少用户
>
> 吞吐量：指单位时间内系统能处理的请求数量。
>
> - QPS：Query Per Second 每秒查询数。 
> - TPS：Transactions Per Second 每秒事务数。 
> - 一个事务是指一个客户机向服务器发送请求然后服务器做出反应的过程。客户机在发送请求时开始计时，收到服务器响应后结束计时，以此来计算使用的时间和完成的事务个数。
> - 一个页面的一次访问，只会形成一个TPS；但一次页面请求，可能产生多次对服务器的请求，就会有多个QPS（**QPS >= 并发连接数 >= TPS**）
>
> 高性能：提供快速的访问体验。
>
> 高可用：网站服务一直可以正常访问。
>
> 可伸缩：通过硬件增加/减少，提高/降低处理能力。
>
> 高可扩展：系统间耦合低，方便的通过新增/移除方式，增加/减少新的功能/模块。 
>
> 安全性：提供网站安全访问和数据加密，安全存储等策略。
>
> 敏捷性：随需应变，快速响应。



## 2、集群和分布式

- 集群：很多“人”一起 ，干一样的事。（一个业务模块，部署在多台服务器上）
- 分布式：很多“人”一起，干不一样的事。这些不一样的事，合起来是一件大事。（一个大的业务系统，拆分为小的业务模块，分别部署在不同的机器上）

<img src="img(dubbo)/image-20220123102728169.png" alt="image-20220123102728169" style="zoom:80%;" />

**发展模拟图**

<img src="img(dubbo)/image-20220123103011004.png" alt="image-20220123103011004" style="zoom:80%;" />

<img src="img(dubbo)/image-20220123103038426.png" alt="image-20220123103038426" style="zoom:80%;" />

<img src="img(dubbo)/image-20220123103124168.png" alt="image-20220123103124168" style="zoom:80%;" />



## 3、架构演进

<img src="img(dubbo)/image-20220123103320853.png" alt="image-20220123103320853" style="zoom:80%;" />

<img src="img(dubbo)/image-20220123103342913.png" alt="image-20220123103342913" style="zoom:80%;" />



<img src="img(dubbo)/image-20220123103425582.png" alt="image-20220123103425582" style="zoom:80%;" />

<img src="img(dubbo)/image-20220123103523107.png" alt="image-20220123103523107" style="zoom:80%;" />

<img src="img(dubbo)/image-20220123103542451.png" alt="image-20220123103542451" style="zoom:80%;" />

<img src="img(dubbo)/image-20220123103605184.png" alt="image-20220123103605184" style="zoom:80%;" />



# Dubbo 概述

## 1、Dubbo概念

- Dubbo是阿里巴巴公司开源的一个高性能、轻量级的 Java RPC 框架。
- 致力于提供高性能和透明化的 RPC 远程服务调用方案，以及 SOA 服务治理方案。
- 官网：http://dubbo.apache.org

## 2、Dubbo框架

<img src="img(dubbo)/image-20220123160903371.png" alt="image-20220123160903371" style="zoom:80%;" />

**节点角色说明：**

- Provider：暴露服务的服务提供方
- Container：服务运行容器
- Consumer：调用远程服务的服务消费方
- Registry：服务注册与发现的注册中心
- Monitor：统计服务的调用次数和调用时间的监控中心

**实际上就是将每个服务（service、controller等）模块化（在注册中心进行注册），使其单独运行，然后其他模块想调用另一个模块就通过注册中心进行寻找调用**

# Dubbo 快速入门

## 1、Zookeeper安装

### 1.1 下载安装

**1、环境准备**

ZooKeeper服务器是用Java创建的，它运行在JVM之上。需要安装JDK 7或更高版本。

**2、上传**

将下载的ZooKeeper放到/opt/ZooKeeper目录下

```shell
#上传zookeeper alt+p
put f:/setup/apache-zookeeper-3.5.6-bin.tar.gz
#打开 opt目录
cd /opt
#创建zooKeeper目录
mkdir  zooKeeper
#将zookeeper安装包移动到 /opt/zooKeeper
mv apache-zookeeper-3.5.6-bin.tar.gz /opt/zookeeper/
```

**3、解压**

将tar包解压到/opt/zookeeper目录下

```shell
tar -zxvf apache-ZooKeeper-3.5.6-bin.tar.gz 
```

### 1.2 配置启动

**1、配置zoo.cfg**

进入到conf目录拷贝一个zoo_sample.cfg并完成配置

```shell
#进入到conf目录
cd /opt/zooKeeper/apache-zooKeeper-3.5.6-bin/conf/
#拷贝
cp  zoo_sample.cfg  zoo.cfg
```



修改zoo.cfg

```shell
#打开目录
cd /opt/zooKeeper/
#创建zooKeeper存储目录
mkdir  zkdata
#修改zoo.cfg
vim /opt/zooKeeper/apache-zooKeeper-3.5.6-bin/conf/zoo.cfg
```

 <img src="img(dubbo)/1577548250377-16429258510371.png" alt="1577548250377" style="zoom:80%;" />

修改存储目录：dataDir=/opt/zookeeper/zkdata

**2、启动ZooKeeper**

```shell
cd /opt/zooKeeper/apache-zooKeeper-3.5.6-bin/bin/
#启动
 ./zkServer.sh  start
```

 <img src="img(dubbo)/1577548052037.png" alt="1577548052037" style="zoom:80%;" />

看到上图表示ZooKeeper成功启动

**3、查看ZooKeeper状态**

```shell
./zkServer.sh status
```

zookeeper启动成功。standalone代表zk没有搭建集群，现在是单节点

 <img src="img(dubbo)/1577548175232.png" alt="1577548175232" style="zoom:80%;" />

zookeeper没有启动

 <img src="img(dubbo)/image-20220123161814413.png" alt="image-20220123161814413" style="zoom:80%;" />

## 2、Spring和SpringMVC整合

**实现步骤：**

1. 创建服务提供者Provider模块
2. 创建服务消费者Consumer模块
3. 在服务提供者模块编写 UserServiceImpl 提供服务
4. 在服务消费者中的 UserController 远程调用UserServiceImpl 提供的服务
5. 分别启动两个服务，测试

<img src="img(dubbo)/image-20220123162150556.png" alt="image-20220123162150556" style="zoom:80%;" />

### Provider

这里写两个模块，分别是service模块和web模块，将来web模块依赖于service模块，通过maven的tomcat插件直接启动

**Dubbo以及Zookeeper的pom文件**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.eagle</groupId>
    <artifactId>dubbo-web</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>war</packaging>

    <properties>
        <spring.version>5.1.9.RELEASE</spring.version>
        <dubbo.version>2.7.4.1</dubbo.version>
        <zookeeper.version>4.0.0</zookeeper.version>

    </properties>

    <dependencies>
        <!-- servlet3.0规范的坐标 -->
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>javax.servlet-api</artifactId>
            <version>3.1.0</version>
            <scope>provided</scope>
        </dependency>
        <!--spring的坐标-->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>${spring.version}</version>
        </dependency>
        <!--springmvc的坐标-->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>${spring.version}</version>
        </dependency>
     
        <!--日志-->
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>slf4j-api</artifactId>
            <version>1.7.21</version>
        </dependency>
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>slf4j-log4j12</artifactId>
            <version>1.7.21</version>
        </dependency>

        <!--Dubbo的起步依赖，版本2.7之后统一为rg.apache.dubb -->
        <dependency>
            <groupId>org.apache.dubbo</groupId>
            <artifactId>dubbo</artifactId>
            <version>${dubbo.version}</version>
        </dependency>
        <!--ZooKeeper客户端实现 -->
        <dependency>
            <groupId>org.apache.curator</groupId>
            <artifactId>curator-framework</artifactId>
            <version>${zookeeper.version}</version>
        </dependency>
        <!--ZooKeeper客户端实现 -->
        <dependency>
            <groupId>org.apache.curator</groupId>
            <artifactId>curator-recipes</artifactId>
            <version>${zookeeper.version}</version>
        </dependency>

        <!--公共接口模块-->
        <dependency>
            <groupId>com.eagle</groupId>
            <artifactId>dubbo-interface</artifactId>
            <version>1.0-SNAPSHOT</version>
        </dependency>

    </dependencies>

    <build>
        <plugins>
            <!--tomcat插件-->
            <plugin>
                <groupId>org.apache.tomcat.maven</groupId>
                <artifactId>tomcat7-maven-plugin</artifactId>
                <version>2.1</version>
                <configuration>
                    <port>8000</port>
                    <path>/</path>
                </configuration>
            </plugin>
        </plugins>
    </build>

</project>
```

Service模块然后是Spring配置文件的编写

web模块需要加入一个webapp目录，里面有个WEB-INF目录，在该目录里面再加一个web.xml配置文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns="http://java.sun.com/xml/ns/javaee"
         xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd"
         version="2.5">

	<!-- spring -->
    <context-param>
        <param-name>contextConfigLocation</param-name>
        <param-value>classpath*:spring/applicationContext*.xml</param-value>
        <!-- 这里的spring配置文件直接引用service模块里的即可，只要在web模块的pom文件引入service模块 -->
    </context-param>
    <listener>
        <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
    </listener>
		 
	<!-- Springmvc -->	 
	<servlet>
        <servlet-name>springmvc</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <!-- 指定加载的配置文件 ，通过参数contextConfigLocation加载-->
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>classpath:spring/springmvc.xml</param-value>
        </init-param>
    </servlet>

    <servlet-mapping>
        <servlet-name>springmvc</servlet-name>
        <url-pattern>*.do</url-pattern>
    </servlet-mapping>

</web-app>
```

在web模块的source目录下加入springmvc.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:dubbo="http://dubbo.apache.org/schema/dubbo"
       xmlns:mvc="http://www.springframework.org/schema/mvc"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/mvc http://www.springframework.org/schema/mvc/spring-mvc.xsd
         http://dubbo.apache.org/schema/dubbo http://dubbo.apache.org/schema/dubbo/dubbo.xsd http://www.springframework.org/schema/context https://www.springframework.org/schema/context/spring-context.xsd">

	<mvc:annotation-driven/>
    <context:component-scan base-package="com.eagle.controller"/>

</beans>
```

service模块也要pom文件的打包改为war文件，并加入Tomcat插件（注意端口）

Service代码编写，在使用 `@Service` 时使用dubbo的 `@Service` 来标注，不要使用spring的，还要在service模块的spring配置文件中配置dubbo的配置（**注意要先导入dubbo的约束**）

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:dubbo="http://dubbo.apache.org/schema/dubbo"
       xmlns:mvc="http://www.springframework.org/schema/mvc"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/mvc http://www.springframework.org/schema/mvc/spring-mvc.xsd
         http://dubbo.apache.org/schema/dubbo http://dubbo.apache.org/schema/dubbo/dubbo.xsd http://www.springframework.org/schema/context https://www.springframework.org/schema/context/spring-context.xsd">

	<!--dubbo的配置-->
	<!--1.配置项目的名称,唯一 -->
	<dubbo:application name= "dubbo- service"/>
	<!--2.配置注册中心的地址-->
	<dubbo:registry address="zookeeper://192.168.149.135:2181"/>
	<!--3.配置dubbo包扫描-->
	<dubbo:annotation package="com.eagle.service.impl" />

</beans>
```

最后想要启动service模块还要完善目录结构，将web模块的webapp复制过来，然后删除web.xml中对springmvc的配置即可

# Dubbo 高级特性


