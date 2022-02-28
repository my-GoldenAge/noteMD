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

<img src="img(SpringCloud)/image-20220226220754972.png" alt="image-20220226220754972" style="zoom:80%;" />

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




# 5、Eureka服务注册与发现

## Eureka 基本知识

**什么是服务治理**

Spring Cloud封装了Netflix 公司开发的Eureka模块来实现服务治理

在传统的RPC远程调用框架中，管理每个服务与服务之间依赖关系比较复杂，管理比较复杂，所以需要使用服务治理，管理服务于服务之间依赖关系，可以实现服务调用、负载均衡、容错等，实现服务发现与注册。

**什么是服务注册与发现**

Eureka采用了CS的设计架构，Eureka Sever作为服务注册功能的服务器，它是服务注册中心。而系统中的其他微服务，使用Eureka的客户端连接到 Eureka Server并维持心跳连接。这样系统的维护人员就可以通过Eureka Server来监控系统中各个微服务是否正常运行。

在服务注册与发现中，有一个注册中心。当服务器启动的时候，会把当前自己服务器的信息比如服务地址通讯地址等以别名方式注册到注册中心上。另一方(消费者服务提供者)，以该别名的方式去注册中心上获取到实际的服务通讯地址，然后再实现本地RPC调用RPC远程调用框架核心设计思想:在于注册中心，因为使用注册中心管理每个服务与服务之间的一个依赖关系(服务治理概念)。在任何RPC远程框架中，都会有一个注册中心存放服务地址相关信息(接口地址)

<img src="img(SpringCloud)/3956561052b9dc3909f16f1ff26d01bb.png" alt="img" style="zoom:80%;" />

**Eureka包含两个组件:Eureka Server和Eureka Client**

- **Eureka Server提供服务注册服务**
  各个微服务节点通过配置启动后，会在EurekaServer中进行注册，这样EurekaServer中的服务注册表中将会存储所有可用服务节点的信息，服务节点的信息可以在界面中直观看到。

- **EurekaClient通过注册中心进行访问**
  它是一个Java客户端，用于简化Eureka Server的交互，客户端同时也具备一个内置的、使用轮询(round-robin)负载算法的负载均衡器。在应用启动后，将会向Eureka Server发送心跳(默认周期为30秒)。如果Eureka Server在多个心跳周期内没有接收到某个节点的心跳，EurekaServer将会从服务注册表中把这个服务节点移除（默认90秒)

## EurekaServer 服务端安装

1. 建module （cloud-eureka-server7001）
2. 改pom
3. 写yml
4. 主启动

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

    <artifactId>cloud-eureka-server7001</artifactId>

    <dependencies>
        <!-- eureka-server -->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
        </dependency>

        <!--引入自己定义的api通用包，可以使用Payment支付Entity-->
        <dependency>
            <groupId>com.eagle.springcloud</groupId>
            <artifactId>cloud-api-commons</artifactId>
            <version>${project.version}</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-web -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-web  -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>

        <!-- 一般通用配置 -->
        <!-- https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-devtools -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
            <scope>runtime</scope>
            <optional>true</optional>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.projectlombok/lombok -->
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-test -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
        </dependency>

    </dependencies>
</project>
```

```yaml
server:
  port: 7001

eureka:
  instance:
    hostname: locathost #eureka服务端的实例名称
  client:
    #false表示不向注册中心注册自己。
    register-with-eureka: false
    #false表示自己端就是注册中心，我的职责就是维护服务实例，并不需要去检索服务
    fetch-registry: false
    service-url:
      #设置与Eureka server交互的地址查询服务和注册服务都需要依赖这个地址。
      defaultZone: http://${eureka.instance.hostname}:${server.port}/eureka/
```

5. 测试 http://localhost:7001/ 
   <img src="img(SpringCloud)/image-20220227153054135.png" alt="image-20220227153054135" style="zoom:80%;" />

## 支付微服务8001入驻进EurekaServer

1. pom文件中加入Eureka-Client依赖

   ```xml
   <dependency>
       <groupId>org.springframework.cloud</groupId>
       <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
   </dependency>
   ```

2. 写yaml中对eureka的配置

   ```yaml
   eureka:
     client:
       #表示是否将自己注册进Eurekaserver默认为true。
       register-with-eureka: true
       #是否从EurekaServer抓取已有的注册信息，默认为true。单节点无所谓，集群必须设置为true才能配合ribbon使用负载均衡
       fetchRegistry: true
       service-url:
         defaultZone: http://localhost:7001/eureka
   ```

3. 在主启动类上面添加Eureka客户端的注解

   ```java
   package com.eagle.springCloud;
   
   import org.springframework.boot.SpringApplication;
   import org.springframework.boot.autoconfigure.SpringBootApplication;
   import org.springframework.cloud.netflix.eureka.EnableEurekaClient;
   
   /**
    * @Author Maybe
    * Date on 2022/2/21  13:55
    */
   @SpringBootApplication
   @EnableEurekaClient
   public class PaymentMain8001 {
       public static void main(String[] args) {
           SpringApplication.run(PaymentMain8001.class, args);
       }
   }
   ```

4. 测试刷新
   <img src="img(SpringCloud)/image-20220227154823129.png" alt="image-20220227154823129" style="zoom:80%;" />

## 订单微服务80入驻进EurekaServer

步骤和上面一样，唯有要在yaml中加上服务的名字

```yaml
server:
  port: 80

spring:
  application:
    name: cloud-order-service

eureka:
  client:
    #表示是否将自己注册进EurekaServer默认为true。
    register-with-eureka: true
    #是否从EurekaServer抓取已有的注册信息，默认为true。单节点无所谓，集群必须设置为true才能配合ribbon使用负载均衡
    fetchRegistry: true
    service-url:
      defaultZone: http://localhost:7001/eureka
```

测试：

<img src="img(SpringCloud)/image-20220227155341491.png" alt="image-20220227155341491" style="zoom:80%;" />

## Eureka集群原理

1. Eureka集群原理说明
   <img src="img(SpringCloud)/14570c4b7c4dd8653be6211da2675e45.png" alt="img" style="zoom:80%;" />

   > 服务注册：将服务信息注册进注册中心
   >
   > 服务发现：从注册中心上获取服务信息
   >
   > 实质：存key服务命取value闭用地址
   >
   > 1. 先启动eureka注主册中心
   >
   > 2. 启动服务提供者payment支付服务
   >
   > 3. 支付服务启动后会把自身信息(比服务地址L以别名方式注朋进eureka
   >
   > 4. 消费者order服务在需要调用接口时，使用服务别名去注册中心获取实际的RPC远程调用地址
   >
   > 5. 消去者导调用地址后，底屋实际是利用HttpClient技术实现远程调用
   >
   > 6. 消费者实癸导服务地址后会缓存在本地jvm内存中，默认每间隔30秒更新—次服务调用地址

2. **试问**：微服务RPC远程服务调用最核心的是什么

   **高可用**，试想你的注册中心只有一个only one，万一它出故障了，会导致整个为服务环境不可用。

   解决办法：搭建Eureka注册中心集群，实现负载均衡+故障容错。

## Eureka集群环境构建

再建一个Eureka服务模块

然后主要就是在两个模块的yaml中要区分一下名字，并且在service-url中相互设置集群中其他Eureka的URL

> 由于我们测试都是在一台Windows系统上测试，所以可以修改一下C:\Windows\System32\drivers\etc路径下的hosts文件，修改映射配置添加进hosts文件，使得可以直接通过Eureka服务的名字进行访问
>
> ```
> 127.0.0.1 eureka7001.com
> 127.0.0.1 eureka7002.com
> ```

- 修改cloud-eureka-server7001配置文件

  ```yaml
  server:
    port: 7001
  
  eureka:
    instance:
      hostname: eureka7001.com #eureka服务端的实例名称
    client:
      register-with-eureka: false     #false表示不向注册中心注册自己。
      fetch-registry: false     #false表示自己端就是注册中心，我的职责就是维护服务实例，并不需要去检索服务
      service-url:
        #集群指向其它eureka
        defaultZone: http://eureka7002.com:7002/eureka/
        #单机就是7001自己
        #defaultZone: http://eureka7001.com:7001/eureka/
  ```

- 修改cloud-eureka-server7001配置文件

  ```yaml
  server:
    port: 7002
  
  eureka:
    instance:
      hostname: eureka7002.com #eureka服务端的实例名称
    client:
      register-with-eureka: false     #false表示不向注册中心注册自己。
      fetch-registry: false     #false表示自己端就是注册中心，我的职责就是维护服务实例，并不需要去检索服务
      service-url:
        #集群指向其它eureka
        defaultZone: http://eureka7001.com:7001/eureka/
        #单机就是7002自己
        #defaultZone: http://eureka7002.com:7002/eureka/
  ```

## 订单支付两微服务注册进Eureka集群

将它们的配置文件的eureka.client.service-url.defaultZone进行修改

```yaml
eureka:
  client:
    #表示是否将自己注册进EurekaServer默认为true。
    register-with-eureka: true
    #是否从EurekaServer抓取已有的注册信息，默认为true。单节点无所谓，集群必须设置为true才能配合ribbon使用负载均衡
    fetchRegistry: true
    service-url:
      #defaultZone: http://localhost:7001/eureka
      defaultZone: http://eureka7001.com:7001/eureka, http://eureka7002.com:7002/eureka #集群版
```

<img src="img(SpringCloud)/image-20220227174249114.png" alt="image-20220227174249114" style="zoom:80%;" />



## 支付微服务集群配置

参考cloud-provicer-payment8001 创建一个 cloud-provicer-payment8002

1. 新建cloud-provider-payment8002

2. 改POM

3. 写YML - 端口8002

4. 主启动

5. 业务类

6. 修改8001/8002的Controller，添加serverPort（由于现在订单服务端是集群，所以要在controller层以不同的端口号进行标识）

   ```java
   package com.eagle.springCloud.controller;
   
   import com.eagle.springCloud.entities.CommonResult;
   import com.eagle.springCloud.entities.Payment;
   import com.eagle.springCloud.service.PaymentService;
   import lombok.extern.slf4j.Slf4j;
   import org.springframework.beans.factory.annotation.Value;
   import org.springframework.web.bind.annotation.*;
   
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
   
       @Value("${server.port}")
       private String serverPort; //为集群里不同端口的服务添加标识
   
       @PostMapping("/payment/create")
       public CommonResult crete(@RequestBody Payment payment) {
           int result = paymentService.create(payment);
           log.info("***插入成功" + result);
           if (result > 0) {
               return new CommonResult(200, "插入数据库成功，serverPort：" + serverPort, result);
           } else {
               return new CommonResult(444, "插入数据库失败", null);
           }
       }
   
       @GetMapping("/payment/get/{id}")
       public CommonResult<Payment> getPaymentById(@PathVariable("id") Long id) {
           Payment payment = paymentService.getPaymentById(id);
           if (payment != null) {
               return new CommonResult(200, "查询成功，serverPort：" + serverPort, payment);
           } else {
               return new CommonResult(444, "查询失败", null);
           }
       }
   }
   ```

7. **负载均衡**
   cloud-consumer-order80订单服务访问地址不能写死

   ```java
   @RestController
   @Slf4j
   public class OrderController {
       //地址不能写死，因为现在该服务是集群
       //public static final String PAYMENT_URL = "http://localhost:8001";
       public static final String PAYMENT_URL = "http://CLOUD-PAYMENT-SERVICE";//直接通过微服务的名称进行访问
       ...
   }
   ```

   使用@LoadBalanced注解赋予RestTemplate负载均衡的能力

   ```java
   package com.eagle.springCloud.config;
   
   import org.springframework.cloud.client.loadbalancer.LoadBalanced;
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
       @LoadBalanced//使用@LoadBalanced注解赋予RestTemplate负载均衡的能力
       public RestTemplate getRestTemplate() {
           return new RestTemplate();
       }
   }
   ```

8. 测试
   先要启动EurekaServer，7001/7002服务，再启动其他访问，通过http://localhost/consumer/payment/get/2客户端进行访问多次：
   <img src="img(SpringCloud)/image-20220227184018417.png" alt="image-20220227184018417" style="zoom:80%;" />
   负载均衡成功（默认是使用轮询算法）

## actuator微服务信息完善

主机名称：服务名称修改（也就是将IP地址，换成可读性高的名字）

修改cloud-provider-payment8001，cloud-provider-payment8002

修改部分 - YML - eureka.instance.instance-id

```yaml
eureka:
  ...
  instance:
    instance-id: payment8001 #添加此处
```

```yaml
eureka:
  ...
  instance:
    instance-id: payment8002 #添加此处
```

修改之后

eureka主页将显示payment8001，payment8002代替原来显示的IP地址。

---

访问信息有IP信息提示，（就是将鼠标指针移至payment8001，payment8002名下，会有IP地址提示）

修改部分 - YML - eureka.instance.prefer-ip-address

```yaml
eureka:
  ...
  instance:
    instance-id: payment8001 
    prefer-ip-address: true #添加此处
```

```yaml
eureka:
  ...
  instance:
    instance-id: payment8002 
    prefer-ip-address: true #添加此处
```

## 服务发现Discovery

对于注册进eureka里面的微服务，可以通过服务发现来获得该服务的信息

- 修改cloud-provider-payment8001的Controller

  ```java
  @RestController
  @Slf4j
  public class PaymentController{
  	...
      
      @Resource
      private DiscoveryClient discoveryClient;
  
      ...
  
      @GetMapping(value = "/payment/discovery")
      public Object discovery() {
          List<String> services = discoveryClient.getServices();
          // 获取所有微服务的名称
          for (String service : services) {
              log.info("***service:" + service);
          }
  
          List<ServiceInstance> instances = discoveryClient.getInstances("CLOUD-PAYMENT-SERVICE");
          // 获取具体某个微服务的所有实例（集群）
          for (ServiceInstance instance : instances) {
              log.info(instance.getServiceId() + "\t" + instance.getHost() + "\t"
                      + instance.getPort() + "\t" + instance.getUri());
          }
          return discoveryClient;
      }
  }
  ```

- 8001主启动类

  ```java
  package com.eagle.springCloud;
  
  import org.springframework.boot.SpringApplication;
  import org.springframework.boot.autoconfigure.SpringBootApplication;
  import org.springframework.cloud.client.discovery.EnableDiscoveryClient;
  import org.springframework.cloud.netflix.eureka.EnableEurekaClient;
  
  /**
   * @Author Maybe
   * Date on 2022/2/21  13:55
   */
  @SpringBootApplication
  @EnableEurekaClient
  @EnableDiscoveryClient
  public class PaymentMain8001 {
      public static void main(String[] args) {
          SpringApplication.run(PaymentMain8001.class, args);
      }
  }
  ```

- <img src="img(SpringCloud)/image-20220228145014415.png" alt="image-20220228145014415" style="zoom:80%;" />

## Eureka自我保护机制

**概述：**

保护模式主要用于一组客户端和Eureka Server之间存在网络分区场景下的保护。一旦进入保护模式，Eureka Server将会尝试保护其服务注册表中的信息，不再删除服务注册表中的数据，也就是不会注销任何微服务。

如果在Eureka Server的首页看到以下这段提示，则说明Eureka进入了保护模式:

> EMERGENCY! EUREKA MAY BE INCORRECTLY CLAIMING INSTANCES ARE UP WHEN THEY’RE NOT. RENEWALS ARE LESSER THANTHRESHOLD AND HENCE THE INSTANCES ARE NOT BEING EXPIRED JUSTTO BE SAFE

**导致原因**

一句话：某时刻某一个微服务不可用了，Eureka不会立刻清理，依旧会对该微服务的信息进行保存。

属于CAP里面的AP分支。

**为什么会产生Eureka自我保护机制?**

为了EurekaClient可以正常运行，防止与EurekaServer网络不通情况下，EurekaServer不会立刻将EurekaClient服务剔除

**什么是自我保护模式?**

如果Eureka在server端在一定时间内(默认90秒)没有收到EurekaClient发送心跳包，便会直接从服务注册列表中剔除该服务，但是在短时间( 90秒中)内丢失了大量的服务实例心跳，这时候Eurekaserver会开启自我保护机制，不会剔除该服务（该现象可能出现在如果网络不通但是EurekaClient为出现宕机，此时如果换做别的注册中心如果一定时间内没有收到心跳会将剔除该服务，这样就出现了严重失误，因为客户端还能正常发送心跳，只是网络延迟问题，而保护机制是为了解决此问题而产生的)。

**在自我保护模式中，Eureka Server会保护服务注册表中的信息，不再注销任何服务实例。**

它的设计哲学就是宁可保留错误的服务注册信息，也不盲目注销任何可能健康的服务实例。一句话讲解：好死不如赖活着。

综上，自我保护模式是一种应对网络异常的安全保护措施。它的架构哲学是宁可同时保留所有微服务（健康的微服务和不健康的微服务都会保留）也不盲目注销任何健康的微服务。使用自我保护模式，可以让Eureka集群更加的健壮、稳定。

**禁用自我保护**

```yaml
eureka:
  ...
  server:
    #关闭自我保护机制，保证不可用服务被及时踢除
    enable-self-preservation: false
    eviction-interval-timer-in-ms: 2000
```

## Eureka停更说明

https://github.com/Netflix/eureka/wiki

> **Eureka 2.0 (Discontinued)**
>
> The existing open source work on eureka 2.0 is discontinued. The code base and artifacts that were released as part of the existing repository of work on the 2.x branch is considered use at your own risk.
>
> Eureka 1.x is a core part of Netflix’s service discovery system and is still an active project.

# 6、Zookeeper服务注册与发现

[Zookeeper](https://blog.csdn.net/java_66666/article/details/81015302?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522164603694716781683977954%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=164603694716781683977954&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-81015302.pc_search_result_cache&utm_term=zookeeper&spm=1018.2226.3001.4187)相关操作

## zookeeper代替Eureka

zookeeper是一个分布式协调工具，可以实现注册中心功能

关闭Linux服务器防火墙后，启动zookeeper服务器

用到的Linux命令行：

- systemctl stop firewalld关闭防火墙
- systemctl status firewalld查看防火墙状态
- ipconfig查看IP地址
- ping查验结果

zookeeper服务器取代Eureka服务器，zk作为服务注册中心

1. 新建名为cloud-provider-payment8004的Maven工程。

2. POM

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
   
       <artifactId>cloud-provider-payment8004</artifactId>
   
       <properties>
           <maven.compiler.source>8</maven.compiler.source>
           <maven.compiler.target>8</maven.compiler.target>
       </properties>
   
       <dependencies>
           <!-- SpringBoot整合Web组件 -->
           <dependency>
               <groupId>org.springframework.boot</groupId>
               <artifactId>spring-boot-starter-web</artifactId>
           </dependency>
           <dependency>
               <groupId>org.springframework.boot</groupId>
               <artifactId>spring-boot-starter-actuator</artifactId>
           </dependency>
           <dependency><!-- 引入自己定义的api通用包，可以使用Payment支付Entity -->
               <groupId>com.eagle.springcloud</groupId>
               <artifactId>cloud-api-commons</artifactId>
               <version>${project.version}</version>
           </dependency>
           <!-- SpringBoot整合zookeeper客户端 -->
           <dependency>
               <groupId>org.springframework.cloud</groupId>
               <artifactId>spring-cloud-starter-zookeeper-discovery</artifactId>
               <!--先排除自带的zookeeper3.5.3 防止与3.4.9起冲突-->
               <exclusions>
                   <exclusion>
                       <groupId>org.apache.zookeeper</groupId>
                       <artifactId>zookeeper</artifactId>
                   </exclusion>
               </exclusions>
           </dependency>
           <!--添加zookeeper3.5.6版本-->
           <dependency>
               <groupId>org.apache.zookeeper</groupId>
               <artifactId>zookeeper</artifactId>
               <version>3.5.6</version>
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

   **注意：**spring-cloud-starter-zookeeper-discovery里的zookeeper可能会与你添加的zookeeper有冲突导致项目启动失败，所以可以在spring-cloud-starter-zookeeper-discovery中将冲突的部分排除在外

3. yaml

   ```yaml
   #8004表示注册到zookeeper服务器的支付服务提供者端口号
   server:
     port: 8004
   
   #服务别名----注册zookeeper到注册中心名称
   spring:
     application:
       name: cloud-provider-payment
     cloud:
       zookeeper:
         connect-string: 192.168.200.128:2181 #Linux上Zookeeper的ip端口
   ```

4. 主启动类

   ```java
   package com.eagle.springcloud;
   
   import org.springframework.boot.SpringApplication;
   import org.springframework.boot.autoconfigure.SpringBootApplication;
   import org.springframework.cloud.client.discovery.EnableDiscoveryClient;
   
   /**
    * @ClassName: PaymentMain8004
    * @author: Maybe
    * @date: 2022/2/28  15:57
    */
   @SpringBootApplication
   @EnableDiscoveryClient//该注解用于向使用consul或者zookeeper作为注册中心时注册服务
   public class PaymentMain8004 {
       public static void main(String[] args) {
           SpringApplication.run(PaymentMain8004.class, args);
       }
   }
   ```

5. controller测试

   ```java
   package com.eagle.springcloud.controller;
   
   import lombok.extern.slf4j.Slf4j;
   import org.springframework.beans.factory.annotation.Value;
   import org.springframework.web.bind.annotation.GetMapping;
   import org.springframework.web.bind.annotation.RestController;
   
   import java.util.UUID;
   
   /**
    * @ClassName: PaymentController
    * @author: Maybe
    * @date: 2022/2/28  15:59
    */
   @RestController
   @Slf4j
   public class PaymentController {
       @Value("${server.port}")
       private String serverPort;
   
       @GetMapping("/payment/zk")
       public Object paymentzk() {
           return "springCloud with zookeeper: " + serverPort + "\t" + UUID.randomUUID().toString();
       }
   }
   ```

   浏览器测试成功：http://localhost:8004/payment/zk
   接着用zookeeper客户端操作：
   <img src="img(SpringCloud)/image-20220228164931083.png" alt="image-20220228164931083" style="zoom:80%;" />
   将json串格式化看一下：

   ```json
   {
     "name": "cloud-provider-payment",
     "id": "a4d21ee1-b276-4f2b-af05-0eaa8ced8b07",
     "address": "LAPTOP-5DN4I3UA",
     "port": 8004,
     "payload": {
       "@class": "org.springframework.cloud.zookeeper.discovery.ZookeeperInstance",
       "id": "application-1",
       "name": "cloud-provider-payment",
       "metadata": {}
     },
     "registrationTimeUTC": 1646037743876,
     "serviceType": "DYNAMIC",
     "uriSpec": {
       "parts": [
         {
           "value": "scheme",
           "variable": true
         },
         {
           "value": "://",
           "variable": false
         },
         {
           "value": "address",
           "variable": true
         },
         {
           "value": ":",
           "variable": false
         },
         {
           "value": "port",
           "variable": true
         }
       ]
     }
   }
   ```

   ZooKeeper的服务节点是**临时节点**

## 订单服务注册进zookeeper

1. 新建cloud-consumerzk-order80

2. POM

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
   
       <artifactId>cloud-consumerzk-order80</artifactId>
   
       <dependencies>
           <!-- SpringBoot整合Web组件 -->
           <dependency>
               <groupId>org.springframework.boot</groupId>
               <artifactId>spring-boot-starter-web</artifactId>
           </dependency>
           <!-- SpringBoot整合zookeeper客户端 -->
           <dependency>
               <groupId>org.springframework.cloud</groupId>
               <artifactId>spring-cloud-starter-zookeeper-discovery</artifactId>
               <!--先排除自带的zookeeper3.5.3 防止与3.4.9起冲突-->
               <exclusions>
                   <exclusion>
                       <groupId>org.apache.zookeeper</groupId>
                       <artifactId>zookeeper</artifactId>
                   </exclusion>
               </exclusions>
           </dependency>
           <!--添加zookeeper3.5.6版本-->
           <dependency>
               <groupId>org.apache.zookeeper</groupId>
               <artifactId>zookeeper</artifactId>
               <version>3.5.6</version>
               <exclusions>
                   <exclusion>
                       <groupId>org.slf4j</groupId>
                       <artifactId>slf4j-log4j12</artifactId>
                   </exclusion>
               </exclusions>
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

3. YAML

   ```yaml
   server:
     port: 80
   
   #服务别名----注册zookeeper到注册中心名称
   spring:
     application:
       name: cloud-consumer-order
     cloud:
       zookeeper:
         connect-string: 192.168.200.128:2181 #Linux上Zookeeper的ip端口
   ```

4. 主启动

   ```java
   package com.eagle.springcloud;
   
   import org.springframework.boot.SpringApplication;
   import org.springframework.boot.autoconfigure.SpringBootApplication;
   import org.springframework.cloud.client.discovery.EnableDiscoveryClient;
   
   /**
    * @ClassName: OrderZKMain80
    * @author: Maybe
    * @date: 2022/2/28  20:17
    */
   @SpringBootApplication
   @EnableDiscoveryClient
   public class OrderZKMain80 {
       public static void main(String[] args) {
           SpringApplication.run(OrderZKMain80.class, args);
       }
   }
   ```

5. Bean

   ```java
   package com.eagle.config;
   
   import org.springframework.cloud.client.loadbalancer.LoadBalanced;
   import org.springframework.context.annotation.Bean;
   import org.springframework.context.annotation.Configuration;
   import org.springframework.web.client.RestTemplate;
   
   /**
    * @ClassName: ApplicationContextConfig
    * @author: Maybe
    * @date: 2022/2/28  20:20
    */
   @Configuration
   public class ApplicationContextConfig {
       @Bean
       @LoadBalanced
       public RestTemplate getRestTemplate(){
           return new RestTemplate();
       }
   }
   ```

6. controller

   ```java
   package com.eagle.controller;
   
   import lombok.extern.slf4j.Slf4j;
   import org.springframework.web.bind.annotation.GetMapping;
   import org.springframework.web.bind.annotation.RestController;
   import org.springframework.web.client.RestTemplate;
   
   import javax.annotation.Resource;
   
   /**
    * @ClassName: OrderZKController
    * @author: Maybe
    * @date: 2022/2/28  20:26
    */
   @RestController
   @Slf4j
   public class OrderZKController {
       public static final String INVOKE_URL = "http://cloud-provider-payment";
   
       @Resource
       private RestTemplate restTemplate;
   
       @GetMapping(value = "/consumer/payment/zk")
       public String paymentInfo() {
           log.info("111");
           String result = restTemplate.getForObject(INVOKE_URL + "/payment/zk", String.class);
           return result;
       }
   }
   ```

7. 测试

   ```sh
   [zk: localhost:2181(CONNECTED) 0] ls /
   [services, zookeeper]
   [zk: localhost:2181(CONNECTED) 1] ls /services
   [cloud-consumer-order, cloud-provider-payment]
   [zk: localhost:2181(CONNECTED) 2]
   ```

