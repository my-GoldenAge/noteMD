# 1、微服务架构理论入门

## 什么是微服务？

> In short, the microservice architectural style is an approach to developing a single application as a suite of small services, each running in its own process and communicating with lightweight mechanisms, often an HTTP resource API. These services are built around business capabilities and independently deployable by fully automated deployment machinery. There is a bare minimum of centralized management of these services, which may be written in different programming languages and use different data storage technologies.——James Lewis and Martin Fowler (2014)

- **微服务是一种架构风格**
- 一个应用拆分为一组小型服务
- 每个服务运行在自己的进程内，也就是可独立部署和升级
- 服务之间使用轻量级HTTP交互
- 服务围绕业务功能拆分
- 可以由全自动部署机制独立部署
- 去中心化，服务自治。服务可以使用不同的语言、不同的存储技术

**分布式微服务架构-落地维度**

那微服务满足哪些维度？支撑起这些维度又有哪些具体技术？

<img src="img(SpringCloud)/cloud-diagram-1a4cad7294b4452864b5ff57175dd983.svg" alt="Spring Cloud diagram" style="zoom:80%;" />

- 服务调用
- 服务降级
- 服务注册与发先
- 服务熔断
- 负载均衡
- 服务消息队列
- 服务网关
- 配置中心管理
- 自动化构建部署
- 服务监控
- 全链路追踪
- 服务定时任务
- 调度操作

## Spring Cloud简介

是什么？符合微服务技术维度

**SpringCloud=分布式微服务架构的站式解决方案，是多种微服务架构落地技术的集合体，俗称微服务全家桶**

猜猜SpringCloud这个大集合里有多少种技术?

<img src="img(SpringCloud)/eeb48f15799b978e45ed980172c9f06e.png" alt="img" style="zoom:80%;" />

SpringCloud俨然已成为微服务开发的主流技术栈，在国内开发者社区非常火爆。

**“微”力十足，下面例举几个互联网大厂微服务架构案例：**

京东的：

<img src="img(SpringCloud)/2b9f44abea91af3c4b77c1c77eae6eb3.png" alt="京东的" style="zoom:80%;" />

阿里的：

<img src="img(SpringCloud)/ef6092b03932cb7f6f4b7e20ff370261.png" alt="阿里的" style="zoom:80%;" />

京东物流的：

<img src="img(SpringCloud)/b7f15e802845e6ecdc4c13e2685789c1.png" alt="京东物流" style="zoom:80%;" />

## Spring Cloud技术栈

<img src="img(SpringCloud)/fa347f3da197c3df86bf5d36961c8cde.png" alt="netflix" style="zoom:80%;" />

<img src="img(SpringCloud)/b39a21012bed11a837c1edff840e5024.png" alt="img" style="zoom:80%;" />

<img src="img(SpringCloud)/fc8ed10fca5f7cc56e4d4623a39245eb.png" alt="img" style="zoom:80%;" />

# 2、SpringCloud和SpringBoot的版本选型

> SpringCloud的版本命名规则：
>
> Spring Cloud采用了英国伦敦地铁站的名称来命名，并由地铁站名称字母A~Z依次类推的形式来发布迭代版本。
>
> SpringCloud是一 个由许多子项目组成的综合项目,各子项目有不同的发布节奏。为了管理SpringCloud与各子项目的版本依赖关系,发布了一个清单,其中包括了某个SpringCloud版本对应的子项目版本。 为了避免SpringCloud版本号与子项目版本号混淆，**SpringCloud版本采用了名称而非版本号的命名，这些版本的名字采用了伦敦地铁站的名字，根据字母表的顺序来对应版本时间顺序。**例如Angel是第一个版本, Brixton是第二 个版本。
>
> 当SpringCloud的发布内容积累到临界点或者一个重大BUG被解决后， 会发布一个"service releases"版本，简称SRX版本，比如Greenwich.SR2就是SpringCloud发布的Greenwich版本的第2个SRX版本。

- Spring Boot 2.X 版

  - [源码地址](https://github.com/spring-projects/spring-boot/releases/)
  - [Spring Boot 2 的新特性](https://github.com/spring-projects/spring-boot/wiki/spring-Boot-2.0-Release-Notes)
  - 通过上面官网发现，Boot官方**强烈建议**你升级到2.X以上版本

- Spring Cloud H版

  - [源码地址](https://github.com/spring-projects/spring-cloud)
  - [官网](https://spring.io/projects/spring-cloud)

- Spring Boot 与 Spring Cloud 兼容性查看

  - [文档](https://spring.io/projects/spring-cloud#adding-spring-cloud-to-an-existing-spring-boot-application)

  - [JSON接口](https://start.spring.io/actuator/info)

    > tips：json串可以用 tool.lu 里面的Json工具来格式化一下再看

- 接下来开发用到的组件版本
  - Cloud - Hoxton.SR1
  - Boot - 2.2.2.RELEASE
  - Cloud Alibaba - 2.1.0.RELEASE
  - Java - Java 8
  - Maven - 3.5及以上
  - MySQL - 5.7及以上

# 3、关于Cloud各种组件的停更/升级/替换

<img src="img(SpringCloud)/image-20220220140708478.png" alt="image-20220220140708478" style="zoom:80%;" />

[Spring Cloud官方文档](https://cloud.spring.io/spring-cloud-static/Hoxton.SR1/reference/htmlsingle/)

[Spring Cloud中文文档](https://www.bookstack.cn/read/spring-cloud-docs/docs-index.md)

[Spring Boot官方文档](https://docs.spring.io/spring-boot/docs/2.2.2.RELEASE/reference/htmlsingle/)

# 4、微服务架构编码构建

## 父工程Project空间新建

**约定 > 配置 > 编码**

创建微服务cloud整体聚合父工程Project，有8个关键步骤：

1. New Project - maven工程 - create from archetype: maven-archetype-site
2. 聚合总父工程名字
3. Maven选版本
4. 工程名字
5. 字符编码 - Settings - File encoding
6. 注解生效激活 - Settings - Annotation Processors
7. Java编译版本选8
8. File Type过滤 - Settings - File Type

> archetype 英 [ˈɑːkitaɪp] 美 [ˈɑːrkitaɪp]
> n. 典型

## 父工程pom文件

```xml
<?xml version="1.0" encoding="UTF-8"?>

<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.eagle.springcloud</groupId>
    <artifactId>SpringCloud</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>pom</packaging>
    <!--这里打包成pom，pom项目里没有java代码，也不执行任何代码，只是为了聚合工程或传递依赖用的，
    一般用于父工程的pom文件-->

    <!-- 统一管理jar包版本 -->
    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
        <junit.version>4.12</junit.version>
        <log4j.version>1.2.17</log4j.version>
        <lombok.version>1.16.18</lombok.version>
        <mysql.version>5.1.47</mysql.version>
        <druid.version>1.1.16</druid.version>
        <mybatis.spring.boot.version>1.3.0</mybatis.spring.boot.version>
    </properties>

    <!-- 子模块继承之后，提供作用：
        锁定版本+子模块不用写groupId和version -->
    <dependencyManagement>
        <dependencies>
            <!--spring boot 2.2.2-->
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-dependencies</artifactId>
                <version>2.2.2.RELEASE</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <!--spring cloud Hoxton.SR1-->
            <dependency>
                <groupId>org.springframework.cloud</groupId>
                <artifactId>spring-cloud-dependencies</artifactId>
                <version>Hoxton.SR1</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <!--spring cloud alibaba 2.1.0.RELEASE-->
            <dependency>
                <groupId>com.alibaba.cloud</groupId>
                <artifactId>spring-cloud-alibaba-dependencies</artifactId>
                <version>2.1.0.RELEASE</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <dependency>
                <groupId>mysql</groupId>
                <artifactId>mysql-connector-java</artifactId>
                <version>${mysql.version}</version>
            </dependency>
            <dependency>
                <groupId>com.alibaba</groupId>
                <artifactId>druid</artifactId>
                <version>${druid.version}</version>
            </dependency>
            <dependency>
                <groupId>org.mybatis.spring.boot</groupId>
                <artifactId>mybatis-spring-boot-starter</artifactId>
                <version>${mybatis.spring.boot.version}</version>
            </dependency>
            <dependency>
                <groupId>junit</groupId>
                <artifactId>junit</artifactId>
                <version>${junit.version}</version>
            </dependency>
            <dependency>
                <groupId>log4j</groupId>
                <artifactId>log4j</artifactId>
                <version>${log4j.version}</version>
            </dependency>
            <dependency>
                <groupId>org.projectlombok</groupId>
                <artifactId>lombok</artifactId>
                <version>${lombok.version}</version>
                <optional>true</optional>
            </dependency>
        </dependencies>
    </dependencyManagement>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <configuration>
                    <fork>true</fork>
                    <addResources>true</addResources>
                </configuration>
            </plugin>
        </plugins>
    </build>

</project>
```

> 思考：
>
> `<packaging>` 打包成pom的作用？
>
> `<dependencyManagement>` 的作用？
> 使用pom.xml中的dependencyManagement元素能让所有在子项目中引用一个依赖而不用显式的列出版本号。
> Maven会沿着父子层次向上走，直到找到一个拥有dependencyManagement元素的项目，然后它就会使用这个
> dependencyManagement元素中指定的版本号。
>
> **dependencyManagement里只是声明依赖，并不实现，因此子项目需要 显示的声明需要用的依赖。**

---

> IDEA右侧旁的Maven插件有`Toggle ' Skip Tests' Mode`按钮，这样maven可以跳过单元测试，减少时间，提高效率

## 微服务案例

**支付模块**

创建微服务模块套路：

1. 建Module
2. 改POM
3. 写YML
4. 主启动
5. 业务类

<img src="img(SpringCloud)/未命名文件.png" alt="未命名文件" style="zoom:80%;" />

**1、建名为cloud-provider-payment8001的Maven工程**

**2、该pom文件**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>SpringCloud</artifactId>
        <groupId>com.eagle.springcloud</groupId>
        <version>1.0-SNAPSHOT</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>

    <artifactId>cloud-provider-payment8001</artifactId>

    <properties>
        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
    </properties>

    <dependencies>
        <!--包含了sleuth+zipkin-->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-zipkin</artifactId>
        </dependency>
        <!--eureka-client-->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
        </dependency>
        <!-- 引入自己定义的api通用包，可以使用Payment支付Entity -->
        <!--
        <dependency>
            <groupId>com.atguigu.springcloud</groupId>
            <artifactId>cloud-api-commons</artifactId>
            <version>${project.version}</version>
        </dependency>
        -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>
        <dependency>
            <groupId>org.mybatis.spring.boot</groupId>
            <artifactId>mybatis-spring-boot-starter</artifactId>
        </dependency>
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>druid-spring-boot-starter</artifactId>
            <version>1.1.10</version>
        </dependency>
        <!--mysql-connector-java-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
        </dependency>
        <!--jdbc-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-jdbc</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
            <scope>runtime</scope>
            <optional>true</optional>
        </dependency>
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <optional>true</optional>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>

</project>
```

**3、写yml文件**

```yaml
server:
  port: 8001

spring:
  application:
    name: cloud-payment-service
  datasource:
    type: com.alibaba.druid.pool.DruidDataSource            # 当前数据源操作类型
    driver-class-name: org.gjt.mm.mysql.Driver              # mysql驱动包
    url: jdbc:mysql://localhost:3306/springcloud?useUnicode=true&characterEncoding=utf-8&useSSL=false
    username: root
    password: 1234

mybatis:
  mapperLocations: classpath:mapper/*.xml
  type-aliases-package: com.eagle.springCloud.entities    # 所有Entity别名类所在包
```

**4、主启动类**

```java
package com.eagle.springCloud;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

/**
 * @Author Maybe
 * Date on 2022/2/21  13:55
 */
@SpringBootApplication
public class PaymentMain8001 {
    public static void main(String[] args) {
        SpringApplication.run(PaymentMain8001.class, args);
    }
}
```

**5、业务**

- SQL

  ```sql
  CREATE TABLE `payment`(
  	`id` bigint(20) NOT NULL AUTO_INCREMENT COMMENT 'ID',
      `serial` varchar(200) DEFAULT '',
  	PRIMARY KEY (id)
  )ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8mb4
  ```

- Entities

  - 实体类Payment

    ```java
    package com.eagle.springCloud.entities;
    
    import lombok.AllArgsConstructor;
    import lombok.Data;
    import lombok.NoArgsConstructor;
    
    import java.io.Serializable;
    
    /**
     * @Author Maybe
     * Date on 2022/2/21  14:33
     */
    @Data
    @AllArgsConstructor
    @NoArgsConstructor
    public class Payment implements Serializable {
        private long id;
        private String serial;
    }
    ```

  - JSON封装体CommonResult：

    ```java
    package com.eagle.springCloud.entities;
    
    import lombok.AllArgsConstructor;
    import lombok.Data;
    import lombok.NoArgsConstructor;
    
    /**
     * @Author Maybe
     * Date on 2022/2/21  14:35
     */
    @Data
    @AllArgsConstructor
    @NoArgsConstructor
    public class CommonResult<T> {
        private Integer code;//响应状态码
        private String message;//响应信息
        private T data;
    
        public CommonResult(Integer code, String message) {
            this(code, message, null);
        }
    }
    ```

- Dao

  - 接口PaymentDao：

    ```java
    package com.eagle.springCloud.dao;
    
    import com.eagle.springCloud.entities.Payment;
    import org.apache.ibatis.annotations.Mapper;
    import org.apache.ibatis.annotations.Param;
    
    /**
     * @ClassName: PaymentDao
     * @author: Maybe
     * @date: 2022/2/23  20:34
     */
    @Mapper //这里尽量使用mybatis的Mapper注解
    public interface PaymentDao {
        int create(Payment payment);
    
        Payment getPaymentById(@Param("id") Long id);
    }
    ```

  - MyBatis映射文件PaymentMapper.xml，路径：resources/mapper/PaymentMapper.xml（因为在上面yaml配置里配置了该路径）

    ```xml
    <?xml version="1.0" encoding="UTF-8" ?>
    <!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd" >
    <mapper namespace="com.eagle.springCloud.dao.PaymentDao">
    
        <!--useGeneratedKeys属性（仅适用于 insert 和 update）
        会调用 JDBC 的 getGeneratedKeys 方法来取出由数据库内部生成的主键-->
        <!--keyProperty属性（仅适用于 insert 和 update）
        指定能够唯一识别对象的属性，MyBatis 会使用 getGeneratedKeys 的返回值
        或 insert 语句的 selectKey 子元素设置它的值
        这里其实就是接收前面useGeneratedKeys属性返回的主键-->
        <insert id="create" parameterType="Payment" useGeneratedKeys="true" keyProperty="id">
            insert into payment(serial) values (#{serial});
        </insert>
    
        <resultMap id="BaseResultMap" type="com.eagle.springCloud.entities.Payment">
            <id column="id" property="id" jdbcType="BIGINT"/>
            <result column="serial" property="serial" jdbcType="VARCHAR"/>
        </resultMap>
        <select id="getPaymentById" parameterType="Long" resultMap="BaseResultMap">
            select * from payment where id=#{id};
        </select>
    
    </mapper>
    ```

- Service

  - 接口PaymentService

    ```java
    package com.eagle.springCloud.service;
    
    import com.eagle.springCloud.entities.Payment;
    import org.apache.ibatis.annotations.Param;
    
    /**
     * @ClassName: PaymentService
     * @author: Maybe
     * @date: 2022/2/23  20:57
     */
    public interface PaymentService {
        int create(Payment payment);
    
        Payment getPaymentById(@Param("id") Long id);
    }
    ```

  - PaymentService实现类

    ```java
    package com.eagle.springCloud.service;
    
    import com.eagle.springCloud.dao.PaymentDao;
    import com.eagle.springCloud.entities.Payment;
    import org.springframework.stereotype.Service;
    
    import javax.annotation.Resource;
    
    /**
     * @ClassName: PaymentServiceImpl
     * @author: Maybe
     * @date: 2022/2/23  20:58
     */
    @Service
    public class PaymentServiceImpl implements PaymentService{
    
        /*
        因为 PaymentDao 用的mybatis提供的@Mapper注解，所以并不在spring容器中，
        只能使用java提供的@Resource进行注入
         */
        @Resource
        private PaymentDao paymentDao;
    
        @Override
        public int create(Payment payment) {
            return paymentDao.create(payment);
        }
    
        @Override
        public Payment getPaymentById(Long id) {
            return paymentDao.getPaymentById(id);
        }
    }
    ```

- Controller

  ```java
  package com.eagle.springCloud.controller;
  
  import com.eagle.springCloud.entities.CommonResult;
  import com.eagle.springCloud.entities.Payment;
  import com.eagle.springCloud.service.PaymentService;
  import lombok.extern.slf4j.Slf4j;
  import org.springframework.web.bind.annotation.GetMapping;
  import org.springframework.web.bind.annotation.PathVariable;
  import org.springframework.web.bind.annotation.PostMapping;
  import org.springframework.web.bind.annotation.RestController;
  
  import javax.annotation.Resource;
  
  /**
   * @ClassName: PaymentController
   * @author: Maybe
   * @date: 2022/2/23  21:24
   */
  @RestController
  @Slf4j
  public class PaymentController {
      @Resource
      private PaymentService paymentService;
  
      @PostMapping("/payment/create")
      public CommonResult crete(@RequestBody Payment payment) {
          int result = paymentService.create(payment);
          log.info("***插入成功" + result);
          if (result > 0) {
              return new CommonResult(200, "插入数据库成功", result);
          } else {
              return new CommonResult(444, "插入数据库失败", null);
          }
      }
  
      @GetMapping("/payment/get/{id}")
      public CommonResult<Payment> getPaymentById(@PathVariable("id") Long id) {
          Payment payment = paymentService.getPaymentById(id);
          if (payment != null) {
              return new CommonResult(200, "查询成功", payment);
          } else {
              return new CommonResult(444, "查询失败", null);
          }
      }
  }
  ```


## 热部署Devtools

**开发时使用，生产环境关闭**

**1、Adding devtools to your project**（加在具体的模块中）

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
    <scope>runtime</scope>
    <optional>true</optional>
</dependency>
```

**2、Adding plugin to your pom.xml**

下段配置复制到聚合父类总工程的pom.xml

```xml
<build>
    <!--
	<finalName>你的工程名</finalName>（单一工程时添加）
    -->
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
            <configuration>
                <fork>true</fork>
                <addResources>true</addResources>
            </configuration>
        </plugin>
    </plugins>
</build>
```

**3、Enabling automatic build**

File -> Settings(New Project Settings->Settings for New Projects) ->Complier

下面项勾选

- Automatically show first error in editor
- Display notification on build completion
- Build project automatically
- Compile independent modules in parallel

**4、Update the value of**

键入Ctrl + Shift + Alt + / ，打开Registry，勾选：

- compiler.automake.allow.when.app.running

- actionSystem.assertFocusAccessFromEdt

**5、重启IDEA**

## 消费者订单模块

**1、建Module**

创建名为cloud-consumer-order80的maven工程。

**2、改POM**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>SpringCloud</artifactId>
        <groupId>com.eagle.springcloud</groupId>
        <version>1.0-SNAPSHOT</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>

    <artifactId>cloud-consumer-order80</artifactId>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
            <scope>runtime</scope>
            <optional>true</optional>
        </dependency>
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <optional>true</optional>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>

</project>
```

**3、写YML**

```yaml
server:
  port: 80
```

**4、主启动**

```java
package com.eagle.springCloud;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

/**
 * @ClassName: Order80Main
 * @author: Maybe
 * @date: 2022/2/24  16:32
 */
@SpringBootApplication
public class Order80Main {
    public static void main(String[] args) {
        SpringApplication.run(Order80Main.class, args);
    }
}
```

**5、业务类**

实体类

```java
import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;

import java.io.Serializable;

@Data
@AllArgsConstructor
@NoArgsConstructor
public class Payment implements Serializable {
    private Long id;
    private String serial;
}
```

```java
import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;

@Data
@AllArgsConstructor
@NoArgsConstructor
public class CommonResult<T>{
    private Integer code;
    private String message;
    private T data;

    public CommonResult(Integer code, String message){
        this(code, message, null);
    }
}
```

控制层

```java
package com.eagle.springCloud.controller;

import com.eagle.springCloud.entities.CommonResult;
import com.eagle.springCloud.entities.Payment;
import lombok.extern.slf4j.Slf4j;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.client.RestTemplate;

import javax.annotation.Resource;

/**
 * @ClassName: OrderController
 * @author: Maybe
 * @date: 2022/2/24  16:58
 */
@RestController
@Slf4j
public class OrderController {
    public static final String PAYMENT_URL = "http://localhost:8001";

    /*
    RestTemplate提供了多种便捷访问远程Http服务的方法,
    是一种简单便捷的访问restful服务模板类，是Spring提供的用于访问Rest服务的客户端模板工具集
     */
    @Resource
    private RestTemplate restTemplate;

    @GetMapping("/consumer/payment/create")
    public CommonResult create(Payment payment) {
        /*
        使用restTemplate访问restful接口非常的简单粗暴无脑。
        (url, requestMap, ResponseBean.class)这三个参数分别代表
        REST请求地址、请求参数、HTTP响应转换被转换成的对象类型。
         */
        return restTemplate.postForObject(PAYMENT_URL + "/payment/create", payment, CommonResult.class);
    }

    @GetMapping("/consumer/payment/get/{id}")
    public CommonResult<Payment> getPayment(@PathVariable("id") Long id) {
        return restTemplate.getForObject(PAYMENT_URL + "/payment/get/" + id, CommonResult.class);
    }
}
```

配置类

```java
package com.eagle.springCloud.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.client.RestTemplate;

/**
 * @ClassName: ApplicationContextConfig
 * @author: Maybe
 * @date: 2022/2/24  17:10
 */
@Configuration
public class ApplicationContextConfig {
    @Bean
    public RestTemplate getRestTemplate() {
        return new RestTemplate();
    }
}
```

**6、测试**

## RunDashboard 窗口

如果直接有该窗口就没问题，否则可以进行如下操作：

通过修改idea的workspace.xml的方式来**快速打开Run Dashboard窗口**（这个用来显示哪些Spring Boot工程运行，停止等信息。我idea 2020.1版本在名为Services窗口就可以显示哪些Spring Boot工程运行，停止等信息出来，所以这仅作记录参考）。

**开启Run DashBoard：**

1. 打开工程路径下的.idea文件夹的workspace.xml

2. 在`<component name="RunDashboard">`中修改或添加以下代码：

   ```xml
   <option name="configurationTypes">
   	<set>
   		<option value="SpringBootApplicationConfigurationType"/>
       </set>
   </option>
   ```

3. 由于idea版本差异，可能需要关闭重启。

## 工程重构（抽离出通用的）

观察cloud-consumer-order80与cloud-provider-payment8001两工程有重复代码（entities包下的实体），重构。

1. 新建 cloud-api-commons 模块

2. pom

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <project xmlns="http://maven.apache.org/POM/4.0.0"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
       <parent>
           <artifactId>SpringCloud</artifactId>
           <groupId>com.eagle.springcloud</groupId>
           <version>1.0-SNAPSHOT</version>
       </parent>
       <modelVersion>4.0.0</modelVersion>
   
       <artifactId>cloud-api-commons</artifactId>
   
       <dependencies>
           <dependency>
               <groupId>org.springframework.boot</groupId>
               <artifactId>spring-boot-devtools</artifactId>
               <scope>runtime</scope>
               <optional>true</optional>
           </dependency>
           <dependency>
               <groupId>org.projectlombok</groupId>
               <artifactId>lombok</artifactId>
               <optional>true</optional>
           </dependency>
           <dependency>
               <groupId>cn.hutool</groupId>
               <artifactId>hutool-all</artifactId>
               <version>5.1.0</version>
           </dependency>
       </dependencies>
   
   </project>
   ```

3. 将通用的类cv到 cloud-api-commons 模块中
   <img src="img(SpringCloud)/image-20220226173422397.png" alt="image-20220226173422397" style="zoom:80%;" />

4. maven **clean、install** cloud-api-commons工程，以供其他工程调用

5. 在其他过程中的pom文件引入该模块（别忘了将已经抽离出来的删掉）

   ```xml
   <dependency>
       <groupId>com.lun.springcloud</groupId>
       <artifactId>cloud-api-commons</artifactId>
       <version>${project.version}</version>
   </dependency>
   ```

   
