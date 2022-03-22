# SpringCloud Alibaba 简介

**为什么会出现SpringCloud alibaba**

[Spring Cloud Netflix项目进入维护模式](https://spring.io/blog/2018/12/12/spring-cloud-greenwich-rc1-available-now)

> The following Spring Cloud Netflix modules and corresponding starters will be placed into maintenance mode:
>
> 1. spring-cloud-netflix-archaius
> 2. spring-cloud-netflix-hystrix-contract
> 3. spring-cloud-netflix-hystrix-dashboard
> 4. spring-cloud-netflix-hystrix-stream
> 5. spring-cloud-netflix-hystrix
> 6. spring-cloud-netflix-ribbon
> 7. spring-cloud-netflix-turbine-stream
> 8. spring-cloud-netflix-turbine
> 9. spring-cloud-netflix-zuul
>
> This does not include the Eureka or concurrency-limits modules.

其实这其中的爱恨情仇大概是这样的：先是阿里的Dubbo进入维护，然后Netflix（spring）看准时机把dubbo给吞了，并推出springcloud最初的一站式解决方案，后来也不知是何原因，Netflix内部也出现一些矛盾导致，springcloud最初一些技术（Eureka、Zuul...）进入维护，然后阿里就乘机推出自己的 springcloud Alibaba ，最终spring这里也看不下去了，在2018.10.31，Spring Cloud Alibaba 正式入驻了Spring Cloud官方孵化器，并在Maven 中央库发布了第一个版本。

至于介绍，直接看官网（反正是中文）

[SpringCloud Alibaba 官网](https://github.com/alibaba/spring-cloud-alibaba/blob/2.2.x/README-zh.md)

> ## 主要功能
>
> - **服务限流降级**：默认支持 WebServlet、WebFlux、OpenFeign、RestTemplate、Spring Cloud Gateway、Zuul、Dubbo 和 RocketMQ 限流降级功能的接入，可以在运行时通过控制台实时修改限流降级规则，还支持查看限流降级 Metrics 监控。
> - **服务注册与发现**：适配 Spring Cloud 服务注册与发现标准，默认集成了 Ribbon 的支持。
> - **分布式配置管理**：支持分布式系统中的外部化配置，配置更改时自动刷新。
> - **消息驱动能力**：基于 Spring Cloud Stream 为微服务应用构建消息驱动能力。
> - **分布式事务**：使用 @GlobalTransactional 注解， 高效并且对业务零侵入地解决分布式事务问题。
> - **阿里云对象存储**：阿里云提供的海量、安全、低成本、高可靠的云存储服务。支持在任何应用、任何时间、任何地点存储和访问任意类型的数据。
> - **分布式任务调度**：提供秒级、精准、高可靠、高可用的定时（基于 Cron 表达式）任务调度服务。同时提供分布式的任务执行模型，如网格任务。网格任务支持海量子任务均匀分配到所有 Worker（schedulerx-client）上执行。
> - **阿里云短信服务**：覆盖全球的短信服务，友好、高效、智能的互联化通讯能力，帮助企业迅速搭建客户触达通道。
>
> 除了上述所具有的功能外，针对企业级用户的场景，Spring Cloud Alibaba 配套的企业版微服务治理方案 [微服务引擎MSE](https://www.aliyun.com/product/aliware/mse?spm=github.spring.com.topbar) 还提供了企业级微服务治理中心，包括全链路灰度、服务预热、无损上下线和离群实例摘除等更多更强大的治理能力，同时还提供了企业级 Nacos 注册配置中心，企业级云原生网关等多种产品及解决方案。
>
> ## 组件
>
> **[Sentinel](https://github.com/alibaba/Sentinel)**：把流量作为切入点，从流量控制、熔断降级、系统负载保护等多个维度保护服务的稳定性。
>
> **[Nacos](https://github.com/alibaba/Nacos)**：一个更易于构建云原生应用的动态服务发现、配置管理和服务管理平台。
>
> **[RocketMQ](https://rocketmq.apache.org/)**：一款开源的分布式消息系统，基于高可用分布式集群技术，提供低延时的、高可靠的消息发布与订阅服务。
>
> **[Dubbo](https://github.com/apache/dubbo)**：Apache Dubbo™ 是一款高性能 Java RPC 框架。
>
> **[Seata](https://github.com/seata/seata)**：阿里巴巴开源产品，一个易于使用的高性能微服务分布式事务解决方案。
>
> **[Alibaba Cloud OSS](https://www.aliyun.com/product/oss)**: 阿里云对象存储服务（Object Storage Service，简称 OSS），是阿里云提供的海量、安全、低成本、高可靠的云存储服务。您可以在任何应用、任何时间、任何地点存储和访问任意类型的数据。
>
> **[Alibaba Cloud SchedulerX](https://cn.aliyun.com/aliware/schedulerx)**: 阿里中间件团队开发的一款分布式任务调度产品，提供秒级、精准、高可靠、高可用的定时（基于 Cron 表达式）任务调度服务。
>
> **[Alibaba Cloud SMS](https://www.aliyun.com/product/sms)**: 覆盖全球的短信服务，友好、高效、智能的互联化通讯能力，帮助企业迅速搭建客户触达通道。
>
> ## 如何使用
>
> ### 如何引入依赖
>
> 如果需要使用已发布的版本，在 `dependencyManagement` 中添加如下配置。
>
> ```xml
> <dependencyManagement>
>     <dependencies>
>         <dependency>
>             <groupId>com.alibaba.cloud</groupId>
>             <artifactId>spring-cloud-alibaba-dependencies</artifactId>
>             <version>2.2.7.RELEASE</version>
>             <type>pom</type>
>             <scope>import</scope>
>         </dependency>
>     </dependencies>
> </dependencyManagement>
> ```
>
> 
>
> 然后在 `dependencies` 中添加自己所需使用的依赖即可使用。



**Spring Cloud Alibaba学习资料获取**

- [spring官网介绍](https://spring.io/projects/spring-cloud-alibaba#overview)
- [GitHub官网](https://github.com/alibaba/spring-cloud-alibaba)（里面有中文的README）
- [官方文档](https://spring-cloud-alibaba-group.github.io/github-pages/greenwich/spring-cloud-alibaba.html)



# Nacos服务注册和配置中心

## Nacos简介

**为什么叫Nacos**

前四个字母分别为Naming和Configuration的前两个字母，最后的s为Service。

**是什么**

- 一个更易于构建云原生应用的动态服务发现、配置管理和服务管理平台。
- Nacos: Dynamic Naming and Configuration Service
- Nacos就是注册中心＋配置中心的组合 -> **Nacos = Eureka+Config+Bus**

[Nacos官网](https://nacos.io/zh-cn/)

[GitHub下载](https://github.com/alibaba/nacos/releases)

**各中注册中心比较**

| 服务注册与发现框架 | CAP模型 | 控制台管理 | 社区活跃度      |
| ------------------ | ------- | ---------- | --------------- |
| Eureka             | AP      | 支持       | 低(2.x版本闭源) |
| Zookeeper          | CP      | 不支持     | 中              |
| consul             | CP      | 支持       | 高              |
| Nacos              | AP+CP   | 支持       | 高              |

据说Nacos在阿里巴巴内部有超过10万的实例运行，已经过了类似双十一等各种大型流量的考验。

## Nacos安装

- 本地Java8+Maven环境已经OK先

- 从上面的GitHub官网下载Nacos压缩包

- 解压安装包，直接运行bin目录下的`startup.cmd -m standalone`（防止集群模式启动失败）

- 命令运行成功后直接访问http://localhost:8848/nacos，默认账号密码都是nacos

- 结果页面

  <img src="img(SpringCloud Alibaba)/image-20220313214533430.png" alt="image-20220313214533430" style="zoom:80%;" />

## Nacos作为服务注册中心

[官方文档](https://spring-cloud-alibaba-group.github.io/github-pages/greenwich/spring-cloud-alibaba.html#_spring_cloud_alibaba_nacos_discovery)

新建Module - cloudalibaba-provider-payment9001

父pom

```xml
<!--spring cloud alibaba 2.1.0.RELEASE-->
<dependency>
    <groupId>com.alibaba.cloud</groupId>
    <artifactId>spring-cloud-alibaba-dependencies</artifactId>
    <version>2.1.0.RELEASE</version>
    <type>pom</type>
    <scope>import</scope>
</dependency>
```

子pom

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

    <artifactId>cloudalibaba-provider-payment9001</artifactId>

    <dependencies>
        <!--SpringCloud ailibaba nacos -->
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
        </dependency>
        <!-- SpringBoot整合Web组件 -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>
        <!--日常通用jar包配置-->
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

yaml

```yaml
server:
  port: 9001

spring:
  application:
    name: nacos-payment-provider
  cloud:
    nacos:
      discovery:
        server-addr: localhost:8848 #配置Nacos地址

management:
  endpoints:
    web:
      exposure:
        include: '*'
```

```java
package com.eagle.springcloud;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.client.discovery.EnableDiscoveryClient;

/**
 * @ClassName: PaymentMain9001
 * @author: Maybe
 * @date: 2022/3/14  15:17
 */
@SpringBootApplication
@EnableDiscoveryClient
public class PaymentMain9001 {
    public static void main(String[] args) {
        SpringApplication.run(PaymentMain9001.class, args);
    }
}
```

```java
package com.eagle.springcloud.controller;

import org.springframework.beans.factory.annotation.Value;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RestController;

/**
 * @ClassName: PaymentController
 * @author: Maybe
 * @date: 2022/3/14  15:19
 */
@RestController
public class PaymentController {
    @Value("${server.port}")
    private String serverPort;

    @GetMapping(value = "/payment/nacos/{id}")
    public String getPayment(@PathVariable("id") Integer id) {
        return "nacos registry, serverPort: "+ serverPort+"\t id"+id;
    }
}
```

测试

- http://localhost:9001/payment/nacos/1
- nacos控制台
- nacos服务注册中心+服务提供者9001都OK了

<u>参照9001新建9002</u>

## Nacos服务消费者注册和负载

新建Module - cloudalibaba-consumer-nacos-order83

pom

```java
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

    <artifactId>cloudalibaba-consumer-nacos-order83</artifactId>

    <dependencies>
        <!--SpringCloud ailibaba nacos -->
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
        </dependency>
        <dependency>
            <groupId>com.eagle.springcloud</groupId>
            <artifactId>cloud-api-commons</artifactId>
            <version>1.0-SNAPSHOT</version>
        </dependency>
        <!-- SpringBoot整合Web组件 -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>
        <!--日常通用jar包配置-->
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

yaml

```yaml
server:
  port: 83

spring:
  application:
    name: nacos-order-consumer
  cloud:
    nacos:
      discovery:
        server-addr: localhost:8848

#消费者将要去访问的微服务名称，写在配置里马上要调用的话就直接value注入就行
service-url:
  nacos-user-service: http://nacos-payment-provider
```

```java
package com.eagle.springcloud;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.client.discovery.EnableDiscoveryClient;

/**
 * @ClassName: OrderNacosMain83
 * @author: Maybe
 * @date: 2022/3/14  16:13
 */
@SpringBootApplication
@EnableDiscoveryClient
public class OrderNacosMain83 {
    public static void main(String[] args) {
        SpringApplication.run(OrderNacosMain83.class, args);
    }
}
```

```java
package com.eagle.springcloud.config;

import org.springframework.cloud.client.loadbalancer.LoadBalanced;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.client.RestTemplate;

/**
 * @ClassName: ApplicationContextConfig
 * @author: Maybe
 * @date: 2022/3/14  16:14
 */
@Configuration
public class ApplicationContextConfig {
    @Bean
    @LoadBalanced
    public RestTemplate getRestTemplate() {
        return new RestTemplate();
    }
}
```

```java
package com.eagle.springcloud.controller;

import lombok.extern.slf4j.Slf4j;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.client.RestTemplate;

import javax.annotation.Resource;

/**
 * @ClassName: OrderNacosController
 * @author: Maybe
 * @date: 2022/3/14  16:16
 */
@RestController
@Slf4j
public class OrderNacosController {
    @Resource
    private RestTemplate restTemplate;

    @Value("${service-url.nacos-user-service}")
    private String serverURL;

    @GetMapping("/consumer/payment/nacos/{id}")
    public String paymentInfo(@PathVariable("id") Long id) {
        return restTemplate.getForObject(serverURL + "/payment/nacos/" + id, String.class);
    }
}
```

测试

- 启动nacos控制台
- http://localhost:83/Eonsumer/payment/nacos/13
  - 83访问9001/9002，轮询负载OK

为什么nacos支持负载均衡？因为spring-cloud-starter-alibaba-nacos-discovery内含netflix-ribbon包。

 <img src="img(SpringCloud Alibaba)/image-20220314181122765.png" alt="image-20220314181122765" style="zoom:80%;" />

## Nacos服务注册中心对比提升

**Nacos全景图**

<img src="img(SpringCloud Alibaba)/a9c35ea022a95aa76bfec990d6b73d8a.png" alt="nacos全景图" style="zoom:80%;" />

**Nacos和CAP**

Nacos与其他注册中心特性对比

 <img src="img(SpringCloud Alibaba)/62d5a8566a2dc588a5ed52346049a054.png" alt="Nacos与其他注册中心特性对比" style="zoom:80%;" />

**Nacos服务发现实例模型**

 <img src="img(SpringCloud Alibaba)/6578e36df056a995a39034045c36fc40.png" alt="Nacos服务发现实例模型" style="zoom:80%;" />

**Nacos支持AP和CP模式的切换**

- C是所有节点在同一时间看到的数据是一致的
- A的定义是所有的请求都会收到响应。

—般来说，如果不需要存储服务级别的信息且服务实例是通过nacos-client注册，并能够保持心跳上报，那么就可以选择AP模式。当前主流的服务如Spring cloud和Dubbo服务，都适用于AP模式，AP模式为了服务的可能性而减弱了一致性，因此AP模式下只支持注册临时实例。

如果需要在服务级别编辑或者存储配置信息，那么CP是必须，K8S服务和DNS服务则适用于CP模式。CP模式下则支持注册持久化实例，此时则是以Raft协议为集群运行模式，该模式下注册实例之前必须先注册服务，如果服务不存在，则会返回错误。

切换命令：

```shell
curl -X PUT '$NACOS_SERVER:8848/nacos/v1/ns/operator/switches?entry=serverMode&value=CP
```

## Nacos服务配置中心

cloudalibaba-config-nacos-client3377

pom

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

    <artifactId>cloudalibaba-config-nacos-client3377</artifactId>

    <dependencies>
        <!--nacos-config-->
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-nacos-config</artifactId>
        </dependency>
        <!--nacos-discovery-->
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
        </dependency>
        <!--web + actuator-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>
        <!--一般基础配置-->
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

yaml

Nacos 同 springcloud-config 一样，在项目初始化时，**要保证先从配置中心进行配置拉取，拉取配置之后，才能保证项目的正常启动。**

springboot中配置文件的加载是存在优先级顺序的，bootstrap优先级高于application，和springcloud config一样

同时建两个yaml

 <img src="img(SpringCloud Alibaba)/image-20220314210547853.png" alt="image-20220314210547853" style="zoom:80%;" />

**bootstrap.yaml**

```yaml
# nacos配置
server:
  port: 3377

spring:
  application:
    name: nacos-config-client
  cloud:
    nacos:
      discovery:
        server-addr: localhost:8848 #Nacos服务注册中心地址
      config:
        server-addr: localhost:8848 #Nacos作为配置中心地址
        file-extension: yaml #指定yaml格式的配置
#        group: DEV_GROUP
#        namespace: 7d8f0f5a-6a53-4785-9686-dd460158e5d4

# ${spring.application.name}-${spring.profile.active}.${spring.cloud.nacos.config.file-extension}
# nacos-config-client-dev.yaml

# nacos-config-client-test.yaml   ----> config.info
```

**aplication.yaml**

```yaml
spring:
  profiles:
    active: dev # 表示开发环境
    #active: test # 表示测试环境
    #active: info
```

```java
package com.eagle.springcloud;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.client.discovery.EnableDiscoveryClient;

/**
 * @ClassName: NacosConfigClientMain3377
 * @author: Maybe
 * @date: 2022/3/14  20:51
 */
@SpringBootApplication
@EnableDiscoveryClient
public class NacosConfigClientMain3377 {
    public static void main(String[] args) {
        SpringApplication.run(NacosConfigClientMain3377.class, args);
    }
}
```

```java
package com.eagle.springcloud.controller;

import org.springframework.beans.factory.annotation.Value;
import org.springframework.cloud.context.config.annotation.RefreshScope;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

/**
 * @ClassName: ConfigClientController
 * @author: Maybe
 * @date: 2022/3/14  20:56
 */
@RestController
@RefreshScope//支持Nacos的动态刷新功能。
public class ConfigClientController {
    @Value("${config.info}")
    private String configInfo;

    @GetMapping("/config/info")
    public String getConfigInfo() {
        return configInfo;
    }
}
```

**在Nacos中添加配置信息**

Nacos中的dataid的组成格式及与SpringBoot配置文件中的匹配规则

[官方文档](https://nacos.io/zh-cn/docs/quick-start-spring-cloud.html)

> 说明：之所以需要配置 `spring.application.name` ，是因为它是构成 Nacos 配置管理 `dataId`字段的一部分。
>
> 在 Nacos Spring Cloud 中，`dataId` 的完整格式如下：
>
> ```plain
> ${prefix}-${spring.profiles.active}.${file-extension}
> ```
>
> - `prefix` 默认为 `spring.application.name` 的值，也可以通过配置项 `spring.cloud.nacos.config.prefix`来配置。
> - `spring.profiles.active` 即为当前环境对应的 profile，详情可以参考 [Spring Boot文档](https://docs.spring.io/spring-boot/docs/current/reference/html/boot-features-profiles.html#boot-features-profiles)。 **注意：当 `spring.profiles.active` 为空时，对应的连接符 `-` 也将不存在，dataId 的拼接格式变成 `${prefix}.${file-extension}`**
> - `file-exetension` 为配置内容的数据格式，可以通过配置项 `spring.cloud.nacos.config.file-extension` 来配置。目前只支持 `properties` 和 `yaml` 类型。

<img src="img(SpringCloud Alibaba)/image-20220314211345178.png" alt="image-20220314211345178" style="zoom:80%;" />

**测试**

- 启动前需要在nacos客户端-配置管理-配置管理栏目下有对应的yaml配置文件
- 运行cloud-config-nacos-client3377的主启动类
- 调用接口查看配置信息 - http://localhost:3377/config/info

**自带动态刷新**

修改下Nacos中的yaml配置文件，再次调用查看配置的接口，就会发现配置已经刷新。

## Nacos namespace Group和DataID三者关系

**Namespace+Group+Data lD三者关系？为什么这么设计？**

类似Java里面的package名和类名最外层的namespace是可以用于区分部署环境的，Group和DatalD逻辑上区分两个目标对象。

 <img src="img(SpringCloud Alibaba)/60712abd615dd86ac6c119bf132a28d6.png" alt="img" style="zoom:80%;" />

默认情况：Namespace=public，Group=DEFAULT_GROUP，默认Cluster是DEFAULT

- Nacos默认的Namespace是public，Namespace主要用来实现隔离。
  - 比方说我们现在有三个环境：开发、测试、生产环境，我们就可以创建三个Namespace，不同的Namespace之间是隔离的。
- Group默认是DEFAULT_GROUP，Group可以把不同的微服务划分到同一个分组里面去
- Service就是微服务：一个Service可以包含多个Cluster (集群)，Nacos默认Cluster是DEFAULT，Cluster是对指定微服务的一个虚拟划分。
  - 比方说为了容灾，将Service微服务分别部署在了杭州机房和广州机房，这时就可以给杭州机房的Service微服务起一个集群名称(HZ) ，给广州机房的Service微服务起一个集群名称(GZ)，还可以尽量让同一个机房的微服务互相调用，以提升性能。
- 最后是Instance，就是微服务的实例。

## Nacos DataID配置

指定spring.profile.active和配置文件的DatalD来使不同环境下读取不同的配置

默认空间+默认分组+新建dev和test两个DatalD

通过spring.profile.active属性就能进行多环境下配置文件的读取

## Nacos Group分组方案

通过Group实现环境区分 - 新建Group

 <img src="img(SpringCloud Alibaba)/image-20220315132341809.png" alt="image-20220315132341809" style="zoom:80%;" />

<img src="img(SpringCloud Alibaba)/image-20220315132409800.png" alt="image-20220315132409800" style="zoom:80%;" />

bootstrap+application

在config下增加一条group的配置即可。可配置为DEV_GROUP或TEST_GROUP

<img src="img(SpringCloud Alibaba)/image-20220315132609774.png" alt="image-20220315132609774" style="zoom:80%;" />

> - 通过 `spring.cloud.nacos.config.extension-configs[n].data-id` 的配置方式来支持多个 Data Id 的配置。
> - 通过 `spring.cloud.nacos.config.extension-configs[n].group` 的配置方式自定义 Data Id 所在的组，不明确配置的话，默认是 DEFAULT_GROUP。
> - 通过 `spring.cloud.nacos.config.extension-configs[n].refresh` 的配置方式来控制该 Data Id 在配置变更时，是否支持应用中可动态刷新， 感知到最新的配置值。默认是不支持的。
>
> | Note | 多个 Data Id 同时配置时，他的优先级关系是 `spring.cloud.nacos.config.extension-configs[n].data-id` 其中 n 的值越大，优先级越高。 |
> | ---- | ------------------------------------------------------------ |
>
> | Note | `spring.cloud.nacos.config.extension-configs[n].data-id` 的值必须带文件扩展名，文件扩展名既可支持 properties，又可以支持 yaml/yml。 此时 `spring.cloud.nacos.config.file-extension` 的配置对自定义扩展配置的 Data Id 文件扩展名没有影响。 |
> | ---- | ------------------------------------------------------------ |

## Nacos Namespace命名空间方案

> 用于进行租户粒度的配置隔离。不同的命名空间下，可以存在相同的 Group 或 Data ID 的配置。Namespace 的常用场景之一是不同环境的配置的区分隔离，例如开发测试环境和生产环境的资源（如配置、服务）隔离等。
>
> 在没有明确指定 `${spring.cloud.nacos.config.namespace}` 配置的情况下， 默认使用的是 Nacos 上 Public 这个namespae。如果需要使用自定义的命名空间，可以通过以下配置来实现：
>
> ```
> spring.cloud.nacos.config.namespace=b3404bc0-d7dc-4855-b519-570ed34b62d7
> ```
>
> | Note | 该配置必须放在 bootstrap.properties 文件中。此外 `spring.cloud.nacos.config.namespace` 的值是 namespace 对应的 id，id 值可以在 Nacos 的控制台获取。并且在添加配置时注意不要选择其他的 namespae，否则将会导致读取不到正确的配置。 |
> | ---- | ------------------------------------------------------------ |

<img src="img(SpringCloud Alibaba)/image-20220315134140329.png" alt="image-20220315134140329" style="zoom:80%;" />

<img src="img(SpringCloud Alibaba)/image-20220315134230065.png" alt="image-20220315134230065" style="zoom:80%;" />

<img src="img(SpringCloud Alibaba)/image-20220315134514221.png" alt="image-20220315134514221" style="zoom:80%;" />

<img src="img(SpringCloud Alibaba)/image-20220315134653035.png" alt="image-20220315134653035" style="zoom:80%;" />

## Nacos集群的架构说明

> **集群部署架构图**
>
> 因此开源的时候推荐用户把所有服务列表放到一个vip下面，然后挂到一个域名下面
>
> [http://ip1](http://ip1/):port/openAPI 直连ip模式，机器挂则需要修改ip才可以使用。
>
> [http://SLB](http://slb/):port/openAPI 挂载SLB模式(内网SLB，不可暴露到公网，以免带来安全风险)，直连SLB即可，下面挂server真实ip，可读性不好。
>
> [http://nacos.com](http://nacos.com/):port/openAPI 域名 + SLB模式(内网SLB，不可暴露到公网，以免带来安全风险)，可读性好，而且换ip方便，推荐模式
>
>  <img src="img(SpringCloud Alibaba)/deployDnsVipMode.jpg" alt="deployDnsVipMode" style="zoom:80%;" />

上面这张图翻译过来就是：

 <img src="img(SpringCloud Alibaba)/681c3dc16a69f197896cbff482f2298e.png" alt="img" style="zoom:80%;" />

**需要mysql数据库相关说明**

> 默认Nacos使用嵌入式数据库实现数据的存储。所以，如果启动多个默认配置下的Nacos节点，数据存储是存在一致性问题的。为了解决这个问题，**Nacos采用了集中式存储的方式来支持集群化部署，目前只支持MySQL的存储**。
>
> **Nacos支持三种部署模式**
>
> - 单机模式-用于测试和单机试用。
> - 集群模式-用于生产环境，确保高可用。
> - 多集群模式-用于多数据中心场景。
>
> **单机模式支持mysql**
>
> 在0.7版本之前，在单机模式时nacos使用嵌入式数据库实现数据的存储，不方便观察数据存储的基本情况。0.7版本增加了支持mysql数据源能力，具体的操作步骤：
>
> 1. 安装数据库，版本要求:5.6.5+
> 2. 初始化mysq数据库，数据库初始化文件: nacos-mysql.sql
> 3. 修改conf/application.properties文件，增加支持mysql数据源配置（目前只支持mysql)，添加mysql数据源的url、用户名和密码。
>
> ```plain
> spring.datasource.platform=mysql
> 
> db.num=1
> db.url.0=jdbc:mysql://11.162.196.16:3306/nacos_devtest?characterEncoding=utf8&connectTimeout=1000&socketTimeout=3000&autoReconnect=true
> db.user=nacos_devtest
> db.password=youdontknow
> ```
>
> 再以单机模式启动nacos，nacos所有写嵌入式数据库的数据都写到了mysql。

## Nacos持久化切换配置

Nacos默认自带的是嵌入式数据库derby，[nacos的pom.xml](https://github.com/alibaba/nacos/blob/develop/config/pom.xml)中可以看出。

 <img src="img(SpringCloud Alibaba)/image-20220315141630663.png" alt="image-20220315141630663" style="zoom:80%;" />

derby到mysql切换配置步骤：

1. nacos-server-1.1.4\nacos\conf录下找到nacos-mysql.sql文件，执行脚本。（就是在mysql数据库执行即可）
2. nacos-server-1.1.4\nacos\conf目录下找到application.properties，添加以下配置（按需修改对应值）。

```plain
##############mysql集中存储###################
spring.datasource.platform=mysql

db.num=1
db.url.0=jdbc:mysql://localhost:3306/nacos_config?characterEncoding=utf8&connectTimeout=1000&socketTimeout=3000&autoReconnect=true&serverTimezone=GMT
db.user=nacos_config
db.password=123456
```

启动Nacos，可以看到是个全新的空记录界面，以前是记录进derby。

## Linux上配置Nacos集群

先去[下载Linux版本的Nacos](https://github.com/alibaba/nacos/releases)

tar命令解压后安装

**注意**：Linux上修改配置建议复制一份出来（复制出来的加个后缀.bk），不过有的有备份如：以.example结尾的

**Linux服务器上mysql数据库配置**

步骤和上面Windows的差不多，只不过执行mysql也在linux上面

SQL脚本在哪里 - 目录nacos/conf/nacos-mysql.sql

**application.properties配置**

将application.properties.example复制为application.properties追加以下内容，设置数据源

```plain
##############mysql集中存储###################
spring.datasource.platform=mysql

db.num=1
db.url.0=jdbc:mysql://localhost:3306/nacos_config?characterEncoding=utf8&connectTimeout=1000&socketTimeout=3000&autoReconnect=true&serverTimezone=GMT
db.user=nacos_config
db.password=123456
```

**Linux服务器上nacos的集群配置cluster.conf**

梳理出3台nacos集器的不同服务端口号，设置3个端口：

- 3333
- 4444
- 5555

复制cluster.conf.example为cluster.conf写上nacos集群的ip端口

**注意**，这个IP不能写127.0.0.1，必须是Linux命令`hostname -i`能够识别的IP

**编辑Nacos的启动脚本startup.sh，使它能够接受不同的启动端口**

/mynacos/nacos/bin目录下有startup.sh

平时单机版的启动，都是./startup.sh即可

但是，集群启动，我们希望可以类似其它软件的shell命令，传递不同的端口号启动不同的nacos实例。
命令: ./startup.sh -po 3333表示启动端口号为3333的nacos服务器实例，和上一步的cluster.conf配置的一致。

因为这里的参数p被占用了，所以用的 po （大概是版本更新了）

修改的内容：

 <img src="img(SpringCloud Alibaba)/image-20220315185031620.png" alt="image-20220315185031620" style="zoom:80%;" />

<img src="img(SpringCloud Alibaba)/image-20220315185128201.png" alt="image-20220315185128201" style="zoom:80%;" />

执行方式 - `startup.sh - po 端口号`

**Nginx的配置，由它作为负载均衡器**

修改nginx的配置文件 - nginx.conf（这里我先备份了：nginx.conf.example）

 <img src="img(SpringCloud Alibaba)/image-20220316173827115.png" alt="image-20220316173827115" style="zoom:80%;" />

```shell
    upstream cluster{
        server 192.168.200.128:3333;
        server 192.168.200.128:4444;
        server 192.168.200.128:5555;
    }

    server {
        listen 1111;
        server_name localhost;

        location /{
            proxy_pass http://cluster;
        }
    }

```

 <img src="img(SpringCloud Alibaba)/image-20220316174631501.png" alt="image-20220316174631501" style="zoom:80%;" />

指定该配置启动

**截止到此处，1个Nginx+3个nacos注册中心+1个mysql**

- 启动3个nacos注册中心
  - `startup.sh - p 3333`
  - `startup.sh - p 4444`
  - `startup.sh - p 5555`
  - 查看nacos进程启动数`ps -ef | grep nacos | grep -v grep | wc -l`

- 启动nginx
  - `./nginx -c /usr/local/nginx/conf/nginx.conf`
  - 查看nginx进程`ps - ef| grep nginx`

- 测试通过nginx，访问nacos - http://192.168.111.144:1111/nacos/#/login
- 新建一个配置测试

 <img src="img(SpringCloud Alibaba)/a550718db79bd46ee21031e36cb3be00.png" alt="img" style="zoom:80%;" />

- 新建后，可在linux服务器的mysql新插入一条记录

  ```sql
  select * from config;
  ```

  <img src="img(SpringCloud Alibaba)/acc1d20f83d539d0e7943a11859328f5.png" alt="img" style="zoom:80%;" />

- 让微服务cloudalibaba-provider-payment9002启动注册进nacos集群 - 修改配置文件

  ```yaml
  server:
    port: 9002
  
  spring:
    application:
      name: nacos-payment-provider
    c1oud:
      nacos:
        discovery:
          #配置Nacos地址
          #server-addr: Localhost:8848
          #换成nginx的1111端口，做集群
          server-addr: 192.168.200.128:1111
  
  management:
    endpoints:
      web:
        exposure:
          inc1ude: '*'
  ```

- 启动微服务cloudalibaba-provider-payment9002

- 访问nacos，查看注册结果

  <img src="img(SpringCloud Alibaba)/b463fc3b4e9796fa7d98fb72a3c421b6.png" alt="img" style="zoom:80%;" />

**高可用小总结**

 <img src="img(SpringCloud Alibaba)/42ff7ef670012437b046f099192d7484.png" alt="img" style="zoom:80%;" />

# Sentinel实现熔断与限流

## Sentinel是什么

[Sentinel官方文档](https://sentinelguard.io/zh-cn/docs/introduction.html)

[SpringCloud官方文档](https://spring-cloud-alibaba-group.github.io/github-pages/greenwich/spring-cloud-alibaba.html#_spring_cloud_alibaba_sentinel)

[Github官方中文文档](https://github.com/alibaba/Sentinel/wiki/%E4%BB%8B%E7%BB%8D)

> 随着微服务的流行，服务和服务之间的稳定性变得越来越重要。Sentinel 以流量为切入点，从流量控制、熔断降级、系统负载保护等多个维度保护服务的稳定性。
>
> Sentinel 具有以下特征:
>
> - **丰富的应用场景**：Sentinel 承接了阿里巴巴近 10 年的双十一大促流量的核心场景，例如秒杀（即突发流量控制在系统容量可以承受的范围）、消息削峰填谷、集群流量控制、实时熔断下游不可用应用等。
> - **完备的实时监控**：Sentinel 同时提供实时的监控功能。您可以在控制台中看到接入应用的单台机器秒级数据，甚至 500 台以下规模的集群的汇总运行情况。
> - **广泛的开源生态**：Sentinel 提供开箱即用的与其它开源框架/库的整合模块，例如与 Spring Cloud、Apache Dubbo、gRPC、Quarkus 的整合。您只需要引入相应的依赖并进行简单的配置即可快速地接入 Sentinel。同时 Sentinel 提供 Java/Go/C++ 等多语言的原生实现。
> - **完善的 SPI 扩展机制**：Sentinel 提供简单易用、完善的 SPI 扩展接口。您可以通过实现扩展接口来快速地定制逻辑。例如定制规则管理、适配动态数据源等。
>
> Sentinel 的主要特性：
>
> <img src="img(SpringCloud Alibaba)/50505538-2c484880-0aaf-11e9-9ffc-cbaaef20be2b.png" alt="Sentinel-features-overview" style="zoom:80%;" />
>
> Sentinel 的开源生态：
>
> <img src="img(SpringCloud Alibaba)/84338449-a9497e00-abce-11ea-8c6a-473fe477b9a1.png" alt="Sentinel-opensource-eco" style="zoom:80%;" />
>
> Sentinel 分为两个部分:
>
> - 核心库（Java 客户端）不依赖任何框架/库，能够运行于所有 Java 运行时环境，同时对 Dubbo / Spring Cloud 等框架也有较好的支持。
> - 控制台（Dashboard）基于 Spring Boot 开发，打包后可以直接运行，不需要额外的 Tomcat 等应用容器。

## Sentinel下载安装运行

[GitHub下载](https://github.com/alibaba/Sentinel/releases)

下载的是个jar包，直接 -jar 运行即可

```shell
java -jar sentinel-dashboard-1.7.0.jar
```

访问Sentinel管理界面

- localhost:8080
- 登录账号密码均为sentinel

## Sentinel初始化监控

**新建工程 - cloudalibaba-sentinel-service8401**

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

    <artifactId>cloudalibaba-sentinel-service8401</artifactId>

    <dependencies>
        <!--SpringCloud ailibaba nacos -->
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
        </dependency>
        <!--SpringCloud ailibaba sentinel-datasource-nacos 后续做持久化用到-->
        <dependency>
            <groupId>com.alibaba.csp</groupId>
            <artifactId>sentinel-datasource-nacos</artifactId>
        </dependency>
        <!--SpringCloud ailibaba sentinel -->
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-sentinel</artifactId>
        </dependency>
        <!-- SpringBoot整合Web组件+actuator -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>
        <!--commons-->
        <dependency>
            <groupId>com.eagle.springcloud</groupId>
            <artifactId>cloud-api-commons</artifactId>
            <version>1.0-SNAPSHOT</version>
        </dependency>
        <!--日常通用jar包配置-->
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

```yaml
server:
  port: 8401

spring:
  application:
    name: cloudalibaba-sentinel-service
  cloud:
    nacos:
      discovery:
        server-addr: localhost:8848
    sentinel:
      transport:
        dashboard: localhost:8080
        port: 8719  #默认8719，假如被占用了会自动从8719开始依次+1扫描。直至找到未被占用的端口

management:
  endpoints:
    web:
      exposure:
        include: '*'
```

```java
package com.eagle.springcloud;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.client.discovery.EnableDiscoveryClient;

/**
 * @ClassName: MainApp8401
 * @author: Maybe
 * @date: 2022/3/17  14:51
 */
@SpringBootApplication
@EnableDiscoveryClient
public class MainApp8401 {
    public static void main(String[] args) {
        SpringApplication.run(MainApp8401.class, args);
    }
}
```

```java
package com.eagle.springcloud.controller;

import lombok.extern.slf4j.Slf4j;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

/**
 * @ClassName: FlowLimitController
 * @author: Maybe
 * @date: 2022/3/17  14:52
 */
@RestController
@Slf4j
public class FlowLimitController {
    @GetMapping("/testA")
    public String testA() {
        return "------testA";
    }

    @GetMapping("/testB")
    public String testB() {
        log.info(Thread.currentThread().getName() + "\t" + "...testB");
        return "------testB";
    }
}
```

启动微服务8401

启动nacos8848

启动sentinel8080

**查看sentienl控制台**

刚启动，空空如也，啥都没有

因为Sentinel采用的懒加载

- 只要执行一次访问即可
  - http://localhost:8401/testA
  - http://localhost:8401/testB

![image-20220317155703565](img(SpringCloud Alibaba)/image-20220317155703565.png)

## Sentinel流控规则简介

<img src="img(SpringCloud Alibaba)/image-20220317160414507.png" alt="image-20220317160414507" style="zoom:80%;" />

进一步解释说明：

- 资源名：唯一名称，默认请求路径。
- 针对来源：Sentinel可以针对调用者进行限流，填写微服务名，默认default（不区分来源）。

- 阈值类型/单机阈值：
  - QPS(每秒钟的请求数量)︰当调用该API的QPS达到阈值的时候，进行限流。
  - 线程数：当调用该API的线程数达到阈值的时候，进行限流。（**就类似TPS**）

- 是否集群：不需要集群。
- 流控模式：
  - 直接：API达到限流条件时，直接限流。
  - 关联：当关联的资源达到阈值时，就限流自己。
  - 链路：只记录指定链路上的流量（指定资源从入口资源进来的流量，如果达到阈值，就进行限流)【API级别的针对来源】。

- 流控效果：
  - 快速失败：直接失败，抛异常。
  - Warm up：根据Code Factor（冷加载因子，默认3）的值，从阈值/codeFactor，经过预热时长，才达到设置的QPS阈值。
  - 排队等待：匀速排队，让请求以匀速的速度通过，阈值类型必须设置为QPS，否则无效。

## Sentinel流控-直接失败（系统默认）

有关QPS和TPS的区别，可参考 [博客](https://blog.csdn.net/qq_29347295/article/details/85116229)

### QPS

**配置及说明**

这里阈值类型选的是QPS类型

表示1秒钟内查询1次就是OK，若超过次数1，就直接->快速失败，报默认错误

 <img src="img(SpringCloud Alibaba)/image-20220317161152542.png" alt="image-20220317161152542" style="zoom:80%;" />

**测试**

快速多次点击访问http://localhost:8401/testA

**结果**

返回页面 Blocked by Sentinel (flow limiting)

**思考**

直接调用默认报错信息，技术方面OK，但是，是否应该有我们自己的后续处理？类似有个fallback的兜底方法?

### TPS（线程数）

其实所谓线程数就是你一个请求过来我来一个线程给你办事，然后给你响应（这整个过程术语就叫一个事务），如果在这一个线程办事的时候又有一个请求过来就需要再来一个线程处理。而TPS就是指一秒钟内处理事务的件数。

改为线程数

 <img src="img(SpringCloud Alibaba)/image-20220317161631530.png" alt="image-20220317161631530" style="zoom:80%;" />

当调用该API的线程数达到阈值的时候，进行限流。

## Sentinel流控-关联

**是什么？**

- 当自己关联的资源达到阈值时，就限流自己
- 当与A关联的资源B达到阀值后，就限流A自己（B惹事，A挂了）

这个设定乍一看好像很奇怪呀，为什么别人达到阈值了要限流我呀？其实设定是没问题的，可以应用的场景比如我支付模块到阈值了，蚌埠住了，我触发这个关联，限流我上面下订单的模块，从而解决燃眉之急

**设置testA**

当关联资源/testB的QPS阀值超过1时，就限流/testA的Rest访问地址，**当关联资源到阈值后限制配置好的资源名**。

 <img src="img(SpringCloud Alibaba)/image-20220317163127529.png" alt="image-20220317163127529" style="zoom:80%;" />

**Postman模拟并发密集访问testB**

<img src="img(SpringCloud Alibaba)/image-20220317163914058.png" alt="image-20220317163914058" style="zoom:80%;" />

Run - 大批量线程高并发访问B，postman的操作相关 [博客](https://blog.csdn.net/zbj18314469395/article/details/106693615?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522164748530116782184627158%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=164748530116782184627158&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-106693615.142^v2^pc_search_quality_down,143^v4^register&utm_term=postman&spm=1018.2226.3001.4187)

运行后随机访问/testA，发现：

 <img src="img(SpringCloud Alibaba)/image-20220317164021371.png" alt="image-20220317164021371" style="zoom:80%;" />

这就是流量监控里面的关联策略

## Sentinel流控-预热

> **Warm Up**
>
> Warm Up（`RuleConstant.CONTROL_BEHAVIOR_WARM_UP`）方式，即预热/冷启动方式。当系统长期处于低水位的情况下，当流量突然增加时，直接把系统拉升到高水位可能瞬间把系统压垮。通过"冷启动"，让通过的流量缓慢增加，在一定时间内逐渐增加到阈值上限，给冷系统一个预热的时间，避免冷系统被压垮。详细文档可以参考 [流量控制 - Warm Up 文档](https://github.com/alibaba/Sentinel/wiki/限流---冷启动)，具体的例子可以参见 [WarmUpFlowDemo](https://github.com/alibaba/Sentinel/blob/master/sentinel-demo/sentinel-demo-basic/src/main/java/com/alibaba/csp/sentinel/demo/flow/WarmUpFlowDemo.java)。
>
> 通常冷启动的过程系统允许通过的 QPS 曲线如下图所示：
>
>  <img src="img(SpringCloud Alibaba)/68292392-b5b0aa00-00c6-11ea-86e1-ecacff8aab51.png" alt="image" style="zoom:80%;" />

**默认coldFactor为3**，即请求QPS 从 threshold / 3开始，经预热时长逐渐升至设定的QPS阈值。

**WarmUp配置**

案例，阀值为10+预热时长设置5秒。

系统初始化的阀值为10/ 3约等于3，即阀值刚开始为3，然后过了5秒后阀值才慢慢升高恢复到10

 <img src="img(SpringCloud Alibaba)/image-20220317194835316.png" alt="image-20220317194835316" style="zoom:80%;" />

**测试**

多次快速点击http://localhost:8401/testA - 刚开始不行，后续慢慢OK

**应用场景**

如：秒杀系统在开启的瞬间，会有很多流量上来，很有可能把系统打死，预热方式就是把为了保护系统，可慢慢的把流量放进来,慢慢的把阀值增长到设置的阀值。

## Sentinel流控-排队等待

> **匀速排队**
>
> 匀速排队（`RuleConstant.CONTROL_BEHAVIOR_RATE_LIMITER`）方式会严格控制请求通过的间隔时间，也即是让请求以均匀的速度通过，对应的是漏桶算法。详细文档可以参考 [流量控制 - 匀速器模式](https://github.com/alibaba/Sentinel/wiki/流量控制-匀速排队模式)，具体的例子可以参见 [PaceFlowDemo](https://github.com/alibaba/Sentinel/blob/master/sentinel-demo/sentinel-demo-basic/src/main/java/com/alibaba/csp/sentinel/demo/flow/PaceFlowDemo.java)。
>
> 该方式的作用如下图所示：
>
>  <img src="img(SpringCloud Alibaba)/68292442-d4af3c00-00c6-11ea-8251-d0977366d9b4.png" alt="image" style="zoom:80%;" />
>
> 这种方式主要用于处理间隔性突发的流量，例如消息队列。想象一下这样的场景，在某一秒有大量的请求到来，而接下来的几秒则处于空闲状态，我们希望系统能够在接下来的空闲期间逐渐处理这些请求，而不是在第一秒直接拒绝多余的请求。
>
> **注意**：匀速排队模式暂时不支持 QPS > 1000 的场景。

匀速排队，让请求以均匀的速度通过，阀值类型必须设成QPS，否则无效。

**例如**：/testA每秒处理一个请求，超过的话就排队等待，等待的超时时间为10000毫秒。

 <img src="img(SpringCloud Alibaba)/image-20220317200848101.png" alt="image-20220317200848101" style="zoom:80%;" />

**测试**

添加日志记录代码到FlowLimitController的testA方法

```java
@RestController
@Slf4j
public class FlowLimitController {
    @GetMapping("/testA")
    public String testA() {
        log.info(Thread.currentThread().getName()+"\t"+"...testA");
        return "------testA";
    }

    @GetMapping("/testB")
    public String testB() {
        log.info(Thread.currentThread().getName() + "\t" + "...testB");
        return "------testB";
    }
}
```

Postman模拟并发密集访问testA

<img src="img(SpringCloud Alibaba)/image-20220317201728084.png" alt="image-20220317201728084" style="zoom:80%;" />

后台结果

<img src="img(SpringCloud Alibaba)/image-20220317201853172.png" alt="image-20220317201853172" style="zoom:80%;" />

可以看到，尽管请求是一秒五个，后台处理还是一秒一个的处理了二十次，并让还未来得及处理的请求先去排队，只要还没有超出等待时间就先排队

## Sentinel服务熔断降级

> **概述**
>
> 除了流量控制以外，对调用链路中不稳定的资源进行熔断降级也是保障高可用的重要措施之一。一个服务常常会调用别的模块，可能是另外的一个远程服务、数据库，或者第三方 API 等。例如，支付的时候，可能需要远程调用银联提供的 API；查询某个商品的价格，可能需要进行数据库查询。然而，这个被依赖服务的稳定性是不能保证的。如果依赖的服务出现了不稳定的情况，请求的响应时间变长，那么调用服务的方法的响应时间也会变长，线程会产生堆积，最终可能耗尽业务自身的线程池，服务本身也变得不可用。
>
> <img src="img(SpringCloud Alibaba)/62410811-cd871680-b61d-11e9-9df7-3ee41c618644.png" alt="chain" style="zoom:80%;" />
>
> 现代微服务架构都是分布式的，由非常多的服务组成。不同服务之间相互调用，组成复杂的调用链路。以上的问题在链路调用中会产生放大的效果。复杂链路上的某一环不稳定，就可能会层层级联，最终导致整个链路都不可用。因此我们需要对不稳定的**弱依赖服务调用**进行熔断降级，暂时切断不稳定调用，避免局部不稳定因素导致整体的雪崩。熔断降级作为保护自身的手段，通常在客户端（调用端）进行配置。

## Sentinel服务熔断降级-RT

> 慢调用比例 (`SLOW_REQUEST_RATIO`)：选择以慢调用比例作为阈值，需要设置允许的慢调用 RT（即最大的响应时间），请求的响应时间大于该值则统计为慢调用。当单位统计时长（`statIntervalMs`）内请求数目大于设置的最小请求数目，并且慢调用的比例大于阈值，则接下来的熔断时长内请求会自动被熔断。经过熔断时长后熔断器会进入探测恢复状态（HALF-OPEN 状态），若接下来的一个请求响应时间小于设置的慢调用 RT 则结束熔断，若大于设置的慢调用 RT 则会再次被熔断。

添加一个/testD

```java
@RestController
@Slf4j
public class FlowLimitController {

    ...

    @GetMapping("/testD")
    public String testD() {
        try {
            TimeUnit.SECONDS.sleep(1);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        log.info("testD 测试RT");
        return "------testD";
    }

}
```

 <img src="img(SpringCloud Alibaba)/image-20220317210029486.png" alt="image-20220317210029486" style="zoom:80%;" />

表示处理响应的时长超过200毫秒就是慢调用，当慢调用的比例大于阈值时，则接下来的一秒内该请求会自动被熔断，经过熔断时长后熔断器会进入探测恢复状态，若接下来的一个请求响应时间小于设置的慢调用 RT 则结束熔断，若大于设置的慢调用 RT 则会再次被熔断。

因为我们加了线程睡一秒钟，所以很明显所有的 /testD 连接都属于慢调用

jmeter压测

 <img src="img(SpringCloud Alibaba)/6dcaee9f62bfd3c8334560df34f6aaa6.png" alt="img" style="zoom:80%;" />

结论

按照上述配置，永远一秒钟打进来10个线程（大于5个了）调用testD，我们希望200毫秒处理完本次任务，如果超过200毫秒还没处理完，在未来1秒钟的时间窗口内，断路器打开（保险丝跳闸）微服务不可用，保险丝跳闸断电了后续我停止jmeter，没有这么大的访问量了，断路器关闭（保险丝恢复），微服务恢复OK。

## Sentinel服务熔断降级-异常比例

> 异常比例 (`ERROR_RATIO`)：当单位统计时长（`statIntervalMs`）内请求数目大于设置的最小请求数目，并且异常的比例大于阈值，则接下来的熔断时长内请求会自动被熔断。经过熔断时长后熔断器会进入探测恢复状态（HALF-OPEN 状态），若接下来的一个请求成功完成（没有错误）则结束熔断，否则会再次被熔断。异常比率的阈值范围是 `[0.0, 1.0]`，代表 0% - 100%。

```java
@RestController
@Slf4j
public class FlowLimitController {

    ...

    @GetMapping("/testE")
    public String testE() {
        log.info("testE 异常比例");
        int age = 10 / 0;
        return "------testE";
    }

}
```

 <img src="img(SpringCloud Alibaba)/image-20220318145910628.png" alt="image-20220318145910628" style="zoom:80%;" />

jmeter

 <img src="img(SpringCloud Alibaba)/6b4fd3cb04118ae77181fe8bf2019176.png" alt="img" style="zoom:80%;" />

按照上述配置，单独访问一次，必然来一次报错一次(int age = 10/0)，调一次错一次。

开启jmeter后，直接高并发发送请求，多次调用达到我们的配置条件了。断路器开启(保险丝跳闸)，微服务不可用了，不再报错error而是服务降级了。

## Sentinel服务熔断降级-异常数

> 异常数 (`ERROR_COUNT`)：当单位统计时长内的异常数目超过阈值之后会自动进行熔断。经过熔断时长后熔断器会进入探测恢复状态（HALF-OPEN 状态），若接下来的一个请求成功完成（没有错误）则结束熔断，否则会再次被熔断。

依然使用上面的 /testE 进行测试

 <img src="img(SpringCloud Alibaba)/image-20220318150710876.png" alt="image-20220318150710876" style="zoom:80%;" />

访问http://localhost:8401/testE，第一次访问绝对报错，因为除数不能为零，我们看到error窗口，但是达到3次报错后，进入熔断后降级。

## Sentinel服务熔断降级总结

> 注意异常降级**仅针对业务异常**，对 Sentinel 限流降级本身的异常（`BlockException`）不生效。

- RT 是在一定的时间内响应时间过长（慢调用）达到阈值而对服务进行降级
- 异常比例 是单位时间内发生异常的比例达到阈值而对服务进行降级
- 异常数 是单位时间内发生异常的个数达到阈值而对服务进行降级

## Sentinel热点key

> 何为热点？热点即经常访问的数据。很多时候我们希望统计某个热点数据中访问频次最高的 Top K 数据，并对其访问进行限制。比如：
>
> - 商品 ID 为参数，统计一段时间内最常购买的商品 ID 并进行限制
> - 用户 ID 为参数，针对一段时间内频繁访问的用户 ID 进行限制
>
> 热点参数限流会统计传入参数中的热点参数，并根据配置的限流阈值与模式，对包含热点参数的资源调用进行限流。热点参数限流可以看做是一种特殊的流量控制，仅对包含热点参数的资源调用生效。
>
>  <img src="img(SpringCloud Alibaba)/sentinel-hot-param-overview-1.png" alt="Sentinel Parameter Flow Control" style="zoom:80%;" />
>
> Sentinel 利用 LRU 策略统计最近最常访问的热点参数，结合令牌桶算法来进行参数级别的流控。热点参数限流支持集群模式。

- 所谓热点就是精确到某个方法的某个参数，如果访问该方法时带有某个参数并且QPS（热点只能是QPS限流）到达阈值就进行限流降级，并且还可以有独有的该方法的fallback来兜底。
- 热点还可以对该参数的特定值进行另外配置，例如：我访问了该方法，带了热点里的参数并且我刚好该参数的值就是热点里对该参数额外配置的值，那么就会按照该参数配置的值的QPS阈值算

```java
@RestController
@Slf4j
public class FlowLimitController
{

    ...

    @GetMapping("/testHotKey")
    //@SentinelResource的value就是个唯一的标识，sentinel的界面就是按照这个标识进行热点配置
    @SentinelResource(value = "testHotKey", blockHandler/*兜底方法*/ = "deal_testHotKey")
    public String testHotKey(@RequestParam(value = "p1", required = false) String p1,
                             @RequestParam(value = "p2", required = false) String p2) {
        //int age = 10/0;
        return "------testHotKey";
    }

    /*兜底方法*/
    public String deal_testHotKey(String p1, String p2, BlockException exception) {
        return "------deal_testHotKey,o(╥﹏╥)o";  //sentinel系统默认的提示：Blocked by Sentinel (flow limiting)
    }

}
```

 <img src="img(SpringCloud Alibaba)/image-20220318154728369.png" alt="image-20220318154728369" style="zoom:80%;" />

测试：

- 方法testHotKey里面只要带上第一个参数并且QPS超过每秒1次，马上降级处理（不带就没事）
- 异常用了我们自己定义的兜底方法
- 但只要第一个参数的值为3，那么你狂点也不会降级（因为阈值是10）



**注意**：这里@SentinelResource里面blockHandler指定的降级方法仅仅针对发生BlockException异常（这个异常是 com.alibaba.csp.sentinel.slots.block 包下的）的fallback方法，而不是说我们这个方法本身出现了异常（运行时异常）的fallback方法

**有关 BlockException 异常**：

```java
package com.alibaba.csp.sentinel.slots.block;

/**
 * Abstract exception indicating blocked by Sentinel due to flow control,
 * circuit breaking or system protection triggered.
 *
 * @author youji.zj
 */
public abstract class BlockException extends Exception {
    ...
}
```

上面的文档翻译过来（很重要）：

> **抽象异常指示由于触发流控制、断路或系统保护而被 Sentinel 阻塞。**

## Sentinel系统规则

> Sentinel 系统自适应限流从整体维度对应用入口流量进行控制，结合应用的 Load、CPU 使用率、总体平均 RT、入口 QPS 和并发线程数等几个维度的监控指标，通过自适应的流控策略，让系统的入口流量和系统的负载达到一个平衡，让系统尽可能跑在最大吞吐量的同时保证系统整体的稳定性。

> **系统规则**
>
> 系统保护规则是从应用级别的入口流量进行控制，从单台机器的 load、CPU 使用率、平均 RT、入口 QPS 和并发线程数等几个维度监控应用指标，让系统尽可能跑在最大吞吐量的同时保证系统整体的稳定性。
>
> 系统保护规则是应用整体维度的，而不是资源维度的，并且**仅对入口流量生效**。入口流量指的是进入应用的流量（`EntryType.IN`），比如 Web 服务或 Dubbo 服务端接收的请求，都属于入口流量。
>
> 系统规则支持以下的模式：
>
> - **Load 自适应**（仅对 Linux/Unix-like 机器生效）：系统的 load1 作为启发指标，进行自适应系统保护。当系统 load1 超过设定的启发值，且系统当前的并发线程数超过估算的系统容量时才会触发系统保护（BBR 阶段）。系统容量由系统的 `maxQps * minRt` 估算得出。设定参考值一般是 `CPU cores * 2.5`。
> - **CPU usage**（1.5.0+ 版本）：当系统 CPU 使用率超过阈值即触发系统保护（取值范围 0.0-1.0），比较灵敏。
> - **平均 RT**：当单台机器上所有入口流量的平均 RT 达到阈值即触发系统保护，单位是毫秒。
> - **并发线程数**：当单台机器上所有入口流量的并发线程数达到阈值即触发系统保护。
> - **入口 QPS**：当单台机器上所有入口流量的 QPS 达到阈值即触发系统保护。

## @SentinelResource配置

> **@SentinelResource 注解**
>
> > 注意：注解方式埋点不支持 private 方法。
>
> `@SentinelResource` 用于定义资源，并提供可选的异常处理和 fallback 配置项。 `@SentinelResource` 注解包含以下属性：
>
> - `value`：资源名称，必需项（不能为空）
> - `entryType`：entry 类型，可选项（默认为 `EntryType.OUT`）
> - `blockHandler` / `blockHandlerClass`: `blockHandler` 对应处理 `BlockException` 的函数名称，可选项。blockHandler 函数访问范围需要是 `public`，返回类型需要与原方法相匹配，参数类型需要和原方法相匹配并且最后加一个额外的参数，类型为 `BlockException`。blockHandler 函数默认需要和原方法在同一个类中。若希望使用其他类的函数，则可以指定 `blockHandlerClass` 为对应的类的 `Class` 对象，注意对应的函数必需为 static 函数，否则无法解析。
> - `fallback` / `fallbackClass`：fallback 函数名称，可选项，用于在抛出异常的时候提供 fallback 处理逻辑。fallback 函数可以针对所有类型的异常（除了 `exceptionsToIgnore` 里面排除掉的异常类型）进行处理。fallback 函数签名和位置要求：
>   - 返回值类型必须与原函数返回值类型一致；
>   - 方法参数列表需要和原函数一致，或者可以额外多一个 `Throwable` 类型的参数用于接收对应的异常。
>   - fallback 函数默认需要和原方法在同一个类中。若希望使用其他类的函数，则可以指定 `fallbackClass` 为对应的类的 `Class` 对象，注意对应的函数必需为 static 函数，否则无法解析。
> - `defaultFallback`（since 1.6.0）：默认的 fallback 函数名称，可选项，通常用于通用的 fallback 逻辑（即可以用于很多服务或方法）。默认 fallback 函数可以针对所有类型的异常（除了 `exceptionsToIgnore` 里面排除掉的异常类型）进行处理。若同时配置了 fallback 和 defaultFallback，则只有 fallback 会生效。defaultFallback 函数签名要求：
>   - 返回值类型必须与原函数返回值类型一致；
>   - 方法参数列表需要为空，或者可以额外多一个 `Throwable` 类型的参数用于接收对应的异常。
>   - defaultFallback 函数默认需要和原方法在同一个类中。若希望使用其他类的函数，则可以指定 `fallbackClass` 为对应的类的 `Class` 对象，注意对应的函数必需为 static 函数，否则无法解析。
> - `exceptionsToIgnore`（since 1.6.0）：用于指定哪些异常被排除掉，不会计入异常统计中，也不会进入 fallback 逻辑中，而是会原样抛出。
>
> 1.8.0 版本开始，`defaultFallback` 支持在类级别进行配置。
>
> > 注：1.6.0 之前的版本 fallback 函数只针对降级异常（`DegradeException`）进行处理，**不能针对业务异常进行处理**。
>
> 特别地，若 blockHandler 和 fallback 都进行了配置，则被限流降级而抛出 `BlockException` 时只会进入 `blockHandler` 处理逻辑。若未配置 `blockHandler`、`fallback` 和 `defaultFallback`，则被限流降级时会将 `BlockException` **直接抛出**（若方法本身未定义 throws BlockException 则会被 JVM 包装一层 `UndeclaredThrowableException`）。



主要试一下 blockHandlerClass 和 fallbackClass 这两个在外定义成类的兜底方法：

```java
package com.eagle.springcloud.controller;

import com.alibaba.csp.sentinel.annotation.SentinelResource;
import com.eagle.springCloud.entities.CommonResult;
import com.eagle.springcloud.myhandler.CustomerBlockHandler;
import com.eagle.springcloud.myhandler.CustomerFallBack;
import lombok.extern.slf4j.Slf4j;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RestController;

/**
 * @ClassName: RateLimitController
 * @author: Maybe
 * @date: 2022/3/18  17:03
 */
@RestController
@Slf4j
public class RateLimitController {
    @GetMapping("/byValue/fallback/{id}")
    @SentinelResource(value = "byValueFallback",
            blockHandlerClass = CustomerBlockHandler.class,
            blockHandler = "handlerException1",
            fallbackClass = CustomerFallBack.class,
            fallback = "fallBack1")
    public CommonResult byValueFallback(@PathVariable Long id) {
        if (id == 4) {
            throw new IllegalArgumentException("IllegalArgumentException,非法参数异常....");
        } else if (id == 5) {
            throw new NullPointerException("NullPointerException,该ID没有对应记录,空指针异常");
        }
        return new CommonResult(200, "ok");
    }

}
```

```java
package com.eagle.springcloud.myhandler;

import com.alibaba.csp.sentinel.slots.block.BlockException;
import com.eagle.springCloud.entities.CommonResult;
import org.springframework.web.bind.annotation.PathVariable;

/**
 * @ClassName: CustomerBlockHandler
 * @author: Maybe
 * @date: 2022/3/18  17:24
 */
public class CustomerBlockHandler {
    private static CommonResult handlerException1(@PathVariable Long id, BlockException blockException) {
        return new CommonResult(444, "按客戶自定义,global handlerException----1");
    }

    private static CommonResult handlerException2(@PathVariable Long id, BlockException blockException) {
        return new CommonResult(444, "按客戶自定义,global handlerException----2");
    }
}
```

```java
package com.eagle.springcloud.myhandler;

import com.eagle.springCloud.entities.CommonResult;
import org.springframework.web.bind.annotation.PathVariable;

/**
 * @ClassName: CustomerFallBack
 * @author: Maybe
 * @date: 2022/3/18  17:30
 */
public class CustomerFallBack {
    public static CommonResult fallBack1(@PathVariable Long id, Throwable throwable) {
        return new CommonResult(444, "按客戶自定义,global fallback----1");
    }

    public static CommonResult fallBack2(@PathVariable Long id, Throwable throwable) {
        return new CommonResult(444, "按客戶自定义,global fallback----2");
    }
}
```

再用sentinel限制一下byValueFallback

 <img src="img(SpringCloud Alibaba)/image-20220319135710885.png" alt="image-20220319135710885" style="zoom:80%;" />

可以看到一直刷新 /byValue/fallback/1 ，正确的页面和BlockException兜底的页面交替出现

而一直刷新 /byValue/fallback/4或/byValue/fallback/5 ，就是fallback兜底的方法页面和lockException兜底的页面交替出现

Sentinel主要有三个核心Api：

1. SphU定义资源
2. Tracer定义统计
3. ContextUtil定义了上下文

## Sentinel集成Ribbon和OpenFeign的服务熔断

集成Ribbon没什么好说的，就在消费方直接写就行（因为Nacos已经包含了Ribbon）

集成OpenFeign就要**引入OpenFeign的坐标以及yaml里激活Sentinel对Feign的支持**，其他的照旧（这里复习一下OpenFeign远程调用时的服务降级FeignFallback）

```xml
<!--SpringCloud openfeign -->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-openfeign</artifactId>
</dependency>
```

```yaml
# 激活Sentinel对Feign的支持
feign:
  sentinel:
    enabled: true
```

**熔断框架比较**

|                |                          Sentinel                          |        Hystrix         |           resilience4j           |
| :------------: | :--------------------------------------------------------: | :--------------------: | :------------------------------: |
|    隔离策略    |                信号量隔离（并发线程数限流）                | 线程池隔商/信号量隔离  |            信号量隔离            |
|  熔断降级策略  |               基于响应时间、异常比率、异常数               |      基于异常比率      |      基于异常比率、响应时间      |
|  实时统计实现  |                   滑动窗口（LeapArray）                    | 滑动窗口（基于RxJava） |         Ring Bit Buffer          |
|  动态规则配置  |                       支持多种数据源                       |     支持多种数据源     |             有限支持             |
|     扩展性     |                         多个扩展点                         |       插件的形式       |            接口的形式            |
| 基于注解的支持 |                            支持                            |          支持          |               支持               |
|      限流      |              基于QPS，支持基于调用关系的限流               |       有限的支持       |           Rate Limiter           |
|    流量整形    |            支持预热模式匀速器模式、预热排队模式            |         不支持         |      简单的Rate Limiter模式      |
| 系统自适应保护 |                            支持                            |         不支持         |              不支持              |
|     控制台     | 提供开箱即用的控制台，可配置规则、查看秒级监控，机器发观等 |     简单的监控查看     | 不提供控制台，可对接其它监控系统 |

## Sentinel配置持久化

一旦我们重启应用，sentinel规则将消失，生产环境需要将配置规则进行持久化。

将限流配置规则持久化进Nacos保存，只要刷新8401某个rest地址，sentinel控制台的流控规则就能看到，只要Nacos里面的配置不删除，针对8401上sentinel上的流控规则持续有效。

比如将8401的sentinel规则进行持久化

pom

```xml
<!--SpringCloud ailibaba sentinel-datasource-nacos sentinel规则持久化用到-->
<dependency>
    <groupId>com.alibaba.csp</groupId>
    <artifactId>sentinel-datasource-nacos</artifactId>
</dependency>
```

yaml

```yaml
...

spring:
  application:
    name: cloudalibaba-sentinel-service
  cloud:
    nacos:
      discovery:
        server-addr: localhost:8848
    sentinel:
      transport:
        dashboard: localhost:8080
        port: 8719  #默认8719，假如被占用了会自动从8719开始依次+1扫描。直至找到未被占用的端口
      datasource: #添加Nacos数据源配置
        ds1:
          nacos:
            server-addr: localhost:8848
            dataId: cloudalibaba-sentinel-service
            groupId: DEFAULT_GROUP
            data-type: json
            rule-type: flow
            
...            
```

解析：

```yaml
spring:
  cloud:
    sentinel:
      datasource: #添加Nacos数据源配置
        ds1:
          nacos:
            server-addr: nacos的IP端口号
            dataId: ${spring.application.name}
            groupId: DEFAULT_GROUP
            data-type: json
            rule-type: flow
```

nacos新建配置

<img src="img(SpringCloud Alibaba)/image-20220319150729526.png" alt="image-20220319150729526" style="zoom:80%;" />

注意到这里是按照资源名来进行配置的，当然可以配置多个

```json
[
    {
        "resource": "/retaLimit/byUrl",
        "limitApp": "default",
        "grade":   1,
        "count":   1,
        "strategy": 0,
        "controlBehavior": 0,
        "clusterMode": false    
    }
]
```

- resource：资源名称；
- limitApp：来源应用；
- grade：阈值类型，0表示线程数, 1表示QPS；
- count：单机阈值；
- strategy：流控模式，0表示直接，1表示关联，2表示链路；
- controlBehavior：流控效果，0表示快速失败，1表示Warm Up，2表示排队等待；
- clusterMode：是否集群。

这样一来用Nacos发布了配置就可以对Sentinel配置进行持久化（当然前提得是nacos已经配置了外部数据库持久化），无论是你的8401宕机还是sentine宕机都不会丢失原来的sentinel配置

# SpringCloud Alibaba Seata处理分布式事务

## 分布式事务问题由来

单体应用被拆分成微服务应用，原来的三个模块被拆分成三个独立的应用,分别使用三个独立的数据源，业务操作需要调用三三 个服务来完成。此时**每个服务内部的数据一致性由本地事务来保证， 但是全局的数据一致性问题没法保证**。

**比如**：用户购买商品的业务逻辑。整个业务逻辑由3个微服务提供支持：

- 仓储服务：对给定的商品扣除仓储数量。
- 订单服务：根据采购需求创建订单。
- 帐户服务：从用户帐户中扣除余额。

<img src="img(SpringCloud Alibaba)/architecture.png" alt="Architecture" style="zoom:80%;" />

一句话：**一次业务操作需要跨多个数据源或需要跨多个系统进行远程调用，就会产生分布式事务问题**。

## Seata术语

Seata 是一款开源的分布式事务解决方案，致力于提供高性能和简单易用的分布式事务服务。Seata 将为用户提供了 AT、TCC、SAGA 和 XA 事务模式，为用户打造一站式的分布式解决方案。

**Seata模型**：一个典型的分布式事务过程，分为<u>分布式事务处理过程的一ID+三组件模型</u>

- Transaction ID XID 全局唯一的事务ID
- 三组件概念
  - **TC (Transaction Coordinator) - 事务协调者**：维护全局和分支事务的状态，驱动全局事务提交或回滚。
  - **TM (Transaction Manager) - 事务管理器**：定义全局事务的范围：开始全局事务、提交或回滚全局事务。
  - **RM (Resource Manager) - 资源管理器**：管理分支事务处理的资源，与TC交谈以注册分支事务和报告分支事务的状态，并驱动分支事务提交或回滚。

<img src="img(SpringCloud Alibaba)/145942191-7a2d469f-94c8-4cd2-8c7e-46ad75683636.png" alt="image" style="zoom:80%;" />

**处理过程**：

1. TM向TC申请开启一个全局事务，全局事务创建成功并生成一个全局唯一的XID；
2. XID在微服务调用链路的上下文中传播；
3. RM向TC注册分支事务，将其纳入XID对应全局事务的管辖；
4. TM向TC发起针对XID的全局提交或回滚决议；
5. TC调度XID下管辖的全部分支事务完成提交或回滚请求。

 <img src="img(SpringCloud Alibaba)/2d2c6aa29c3158413f66d4ef8c1000dc.png" alt="img" style="zoom:80%;" />

## Seata-Server安装配置

[Seata GitHub官网](https://github.com/seata/seata/releases)

下载解压

**Seata配置**

主要修改：自定义事务组名称+事务日志存储模式为db +数据库连接信息

**修改seata的conf目录下的file.conf配置文件（记得备份）**

service模块

<img src="img(SpringCloud Alibaba)/image-20220320162429806.png" alt="image-20220320162429806" style="zoom:80%;" />

store模块

<img src="img(SpringCloud Alibaba)/image-20220320162652140.png" alt="image-20220320162652140" style="zoom:80%;" />

**修改seata\conf目录下的registry.conf配置文件**

 <img src="img(SpringCloud Alibaba)/image-20220320162917780.png" alt="image-20220320162917780" style="zoom:80%;" />

**新建Seata数据库（跟上面配置的数据库名称一样，这里就叫seata），并在数据库里建表，建表的sql在seata\conf目录里面叫db_store.sql的文件**

```sql
-- the table to store GlobalSession data
drop table if exists `global_table`;
create table `global_table` (
  `xid` varchar(128)  not null,
  `transaction_id` bigint,
  `status` tinyint not null,
  `application_id` varchar(32),
  `transaction_service_group` varchar(32),
  `transaction_name` varchar(128),
  `timeout` int,
  `begin_time` bigint,
  `application_data` varchar(2000),
  `gmt_create` datetime,
  `gmt_modified` datetime,
  primary key (`xid`),
  key `idx_gmt_modified_status` (`gmt_modified`, `status`),
  key `idx_transaction_id` (`transaction_id`)
);

-- the table to store BranchSession data
drop table if exists `branch_table`;
create table `branch_table` (
  `branch_id` bigint not null,
  `xid` varchar(128) not null,
  `transaction_id` bigint ,
  `resource_group_id` varchar(32),
  `resource_id` varchar(256) ,
  `lock_key` varchar(128) ,
  `branch_type` varchar(8) ,
  `status` tinyint,
  `client_id` varchar(64),
  `application_data` varchar(2000),
  `gmt_create` datetime,
  `gmt_modified` datetime,
  primary key (`branch_id`),
  key `idx_xid` (`xid`)
);

-- the table to store lock data
drop table if exists `lock_table`;
create table `lock_table` (
  `row_key` varchar(128) not null,
  `xid` varchar(96),
  `transaction_id` long ,
  `branch_id` long,
  `resource_id` varchar(256) ,
  `table_name` varchar(32) ,
  `pk` varchar(36) ,
  `gmt_create` datetime ,
  `gmt_modified` datetime,
  primary key(`row_key`)
);
```

 <img src="img(SpringCloud Alibaba)/image-20220320163319809.png" alt="image-20220320163319809" style="zoom:80%;" />

**在每个业务的数据库里也都要创建回滚日志表，对应的sql在seata\conf目录里面叫db_ undo_ log.sql的文件**

```sql
-- the table to store seata xid data
-- 0.7.0+ add context
-- you must to init this sql for you business databese. the seata server not need it.
-- 此脚本必须初始化在你当前的业务数据库中，用于AT 模式XID记录。与server端无关（注：业务数据库）
-- 注意此处0.3.0+ 增加唯一索引 ux_undo_log
drop table `undo_log`;
CREATE TABLE `undo_log` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `branch_id` bigint(20) NOT NULL,
  `xid` varchar(100) NOT NULL,
  `context` varchar(128) NOT NULL,
  `rollback_info` longblob NOT NULL,
  `log_status` int(11) NOT NULL,
  `log_created` datetime NOT NULL,
  `log_modified` datetime NOT NULL,
  `ext` varchar(100) DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `ux_undo_log` (`xid`,`branch_id`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8;
```

先启动Nacos再启动Seata

## Seata应用实例

seata用起来其实很简单，下面主要就通过上面官方提到的一个 订单->库存->账户 的实例来看一下Seata的应用，再从中学习一下seata的原理

**Order模块**

pom

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

    <artifactId>seata-order-service2001</artifactId>

    <dependencies>
        <!--nacos-->
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
        </dependency>
        <!--seata-->
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-seata</artifactId>
            <exclusions>
                <exclusion>
                    <artifactId>seata-all</artifactId>
                    <groupId>io.seata</groupId>
                </exclusion>
            </exclusions>
        </dependency>
        <dependency>
            <groupId>io.seata</groupId>
            <artifactId>seata-all</artifactId>
            <version>0.9.0</version>
        </dependency>
        <!--feign-->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-openfeign</artifactId>
        </dependency>
        <!--web-actuator-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>
        <!--mysql-druid-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.47</version>
        </dependency>
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>druid-spring-boot-starter</artifactId>
            <version>1.1.10</version>
        </dependency>
        <dependency>
            <groupId>org.mybatis.spring.boot</groupId>
            <artifactId>mybatis-spring-boot-starter</artifactId>
            <version>2.1.1</version>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <optional>true</optional>
        </dependency>
    </dependencies>

</project>
```

yaml

```yaml
server:
  port: 2001

spring:
  application:
    name: seata-order-service
  cloud:
    alibaba:
      seata:
        #自定义事务组名称需要与seata-server中的对应
        tx-service-group: seata_tx_group
    nacos:
      discovery:
        server-addr: localhost:8848
  datasource:
    driver-class-name: com.mysql.jdbc.Driver
    url: jdbc:mysql://localhost:3306/seata_order
    username: root
    password: root

feign:
  hystrix:
    enabled: false

logging:
  level:
    io:
      seata: info

mybatis:
  mapperLocations: classpath:mapper/*.xml
```

要使用seata，还要在resource目录下引入所使用seata的conf目录下的 file.conf 和 registry.conf 文件

 <img src="img(SpringCloud Alibaba)/image-20220321213519758.png" alt="image-20220321213519758" style="zoom:80%;" />

实体类

```java
package com.eagle.springcloudalibaba.domain;

import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;

import java.math.BigDecimal;

/**
 * @ClassName: Order
 * @author: Maybe
 * @date: 2022/3/20  20:39
 */
@Data
@NoArgsConstructor
@AllArgsConstructor
public class Order {
    private Long id;

    private Long userId;

    private Long productId;

    private Integer count;

    private BigDecimal money;

    private Integer status; //订单状态：0：创建中；1：已完结
}
```

```java
package com.eagle.springcloudalibaba.domain;

import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;

/**
 * @ClassName: CommonResult
 * @author: Maybe
 * @date: 2022/3/20  20:38
 */
@Data
@NoArgsConstructor
@AllArgsConstructor
/**
 * 给前端传的模板类
 */
public class CommonResult<T> {
    private Integer code;
    private String message;
    private T data;

    public CommonResult(Integer code, String message) {
        this(code, message, null);
    }
}
```

OrderDao

```java
package com.eagle.springcloudalibaba.dao;

import com.eagle.springcloudalibaba.domain.Order;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Param;

/**
 * @ClassName: OrderDao
 * @author: Maybe
 * @date: 2022/3/20  21:28
 */
@Mapper
public interface OrderDao {
    //创建订单
    void create(Order order);

    //修改订单状态，从零改为1
    void updateStatus(@Param("userId") Long userId,@Param("status") Integer status);

}
```

resources文件夹下新建mapper文件夹，添加orderMapper.xml

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd" >

<mapper namespace="com.eagle.springcloudalibaba.dao.OrderDao">

    <resultMap id="OrderBaseResultMap" type="com.eagle.springcloudalibaba.domain.Order">
        <id property="id" column="id" jdbcType="BIGINT"/>
        <result property="userId" column="user_id" jdbcType="BIGINT"/>
        <result property="productId" column="product_id" jdbcType="BIGINT"/>
        <result property="count" column="count" jdbcType="Integer"/>
        <result property="money" column="money" jdbcType="DECIMAL"/>
        <result property="status" column="status" jdbcType="Integer"/>
    </resultMap>

    <insert id="create">
        insert into t_order (id,user_id,product_id,count,money,status)
        values (null,#{userId},#{productId},#{count},#{money},0);
    </insert>

    <update id="updateStatus">
        update t_order set satus=1
        where user_id=#{userId} and status=#{status};
    </update>

</mapper>
```

Service接口：这里使用的是Feign，所以要写一下其他要调用的服务的Feign接口

```java
package com.eagle.springcloudalibaba.service;

import com.eagle.springcloudalibaba.domain.Order;

/**
 * @ClassName: OrderService
 * @author: Maybe
 * @date: 2022/3/20  21:46
 */
public interface OrderService {
    void create(Order order);
}
```

```java
package com.eagle.springcloudalibaba.service.impl;

import com.eagle.springcloudalibaba.dao.OrderDao;
import com.eagle.springcloudalibaba.domain.Order;
import com.eagle.springcloudalibaba.service.AccountService;
import com.eagle.springcloudalibaba.service.OrderService;
import com.eagle.springcloudalibaba.service.StorageService;
import lombok.extern.slf4j.Slf4j;
import org.springframework.stereotype.Service;

import javax.annotation.Resource;

/**
 * @ClassName: OrderServiceImpl
 * @author: Maybe
 * @date: 2022/3/20  21:46
 */
@Service
@Slf4j
public class OrderServiceImpl implements OrderService {
    @Resource
    private OrderDao orderDao;
    @Resource
    private StorageService storageService;
    @Resource
    private AccountService accountService;

    /**
     * todo
     * 创建订单->调用库存服务扣减库存->调用账户服务扣减账户余额->修改订单状态
     * 简单说：下订单->扣库存->减余额->改状态
     *
     * @param order
     */
    @Override
    public void create(Order order) {
        log.info("----->开始新建订单");
        //1 新建订单
        orderDao.create(order);

        //2 扣减库存
        log.info("----->订单微服务开始调用库存，做扣减Count");
        storageService.decrease(order.getProductId(), order.getCount());
        log.info("----->订单微服务开始调用库存，做扣减end");

        //3 扣减账户
        log.info("----->订单微服务开始调用账户，做扣减Money");
        accountService.decrease(order.getUserId(), order.getMoney());
        log.info("----->订单微服务开始调用账户，做扣减end");

        //4 修改订单状态，从零到1,1代表已经完成
        log.info("----->修改订单状态开始");
        orderDao.updateStatus(order.getUserId(), 0);
        log.info("----->修改订单状态结束");

        log.info("----->下订单结束了，O(∩_∩)O哈哈~");
    }
}
```

Feign接口

```java
package com.eagle.springcloudalibaba.service;

import com.eagle.springcloudalibaba.domain.CommonResult;
import org.springframework.cloud.openfeign.FeignClient;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestParam;

import java.math.BigDecimal;

/**
 * @ClassName: AccountService
 * @author: Maybe
 * @date: 2022/3/20  21:46
 */
@FeignClient(value = "seata-account-service")
public interface AccountService {
    @PostMapping(value = "/account/decrease")
    CommonResult decrease(@RequestParam("userId") Long userId, @RequestParam("money") BigDecimal money);

}
```

```java
package com.eagle.springcloudalibaba.service;

import com.eagle.springcloudalibaba.domain.CommonResult;
import org.springframework.cloud.openfeign.FeignClient;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestParam;

/**
 * @ClassName: StorageService
 * @author: Maybe
 * @date: 2022/3/20  21:45
 */
@FeignClient(value = "seata-storage-service")
public interface StorageService {
    @PostMapping(value = "/storage/decrease")
    CommonResult decrease(@RequestParam("productId") Long productId, @RequestParam("count") Integer count);

}
```

Controller

```java
package com.eagle.springcloudalibaba.controller;

import com.eagle.springcloudalibaba.domain.CommonResult;
import com.eagle.springcloudalibaba.domain.Order;
import com.eagle.springcloudalibaba.service.OrderService;
import lombok.extern.slf4j.Slf4j;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

import javax.annotation.Resource;

/**
 * @ClassName: OrderController
 * @author: Maybe
 * @date: 2022/3/21  16:28
 */
@RestController
@Slf4j
public class OrderController {
    @Resource
    private OrderService orderService;

    @GetMapping("/order/create")
    public CommonResult create(Order order) {
        orderService.create(order);
        return new CommonResult(200, "创建订单成功");
    }
}
```

config配置

MyBatisConfig

```java
package com.eagle.springcloudalibaba.config;

import org.mybatis.spring.annotation.MapperScan;
import org.springframework.context.annotation.Configuration;

/**
 * @ClassName: MyBatisConfig
 * @author: Maybe
 * @date: 2022/3/21  16:32
 */
@Configuration
@MapperScan({"com.eagle.springcloudalibaba.dao"})
public class MyBatisConfig {
}
```

DataSourceProxyConfig，这里在导 DataSourceProxy 时注意要导 io.seata 的包

```java
package com.eagle.springcloudalibaba.config;

import com.alibaba.druid.pool.DruidDataSource;
import io.seata.rm.datasource.DataSourceProxy;
import org.apache.ibatis.session.SqlSessionFactory;
import org.mybatis.spring.SqlSessionFactoryBean;
import org.mybatis.spring.transaction.SpringManagedTransactionFactory;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.boot.context.properties.ConfigurationProperties;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.core.io.support.PathMatchingResourcePatternResolver;

import javax.sql.DataSource;

/**
 * @ClassName: DataSourceProxyConfig
 * @author: Maybe
 * @date: 2022/3/21  16:52
 */

/**
 * 使用Seata对数据源进行代理
 * 在主启动上取消数据源的自动创建，而是使用自己定义的
 */
@Configuration
public class DataSourceProxyConfig {
    @Value("${mybatis.mapperLocations}")
    private String mapperLocations;

    @Bean
    @ConfigurationProperties(prefix = "spring.datasource")
    public DataSource druidDataSource() {
        return new DruidDataSource();
    }

    @Bean
    public DataSourceProxy dataSourceProxy(DataSource dataSource) {
        return new DataSourceProxy(dataSource);
    }

    @Bean
    public SqlSessionFactory sqlSessionFactoryBean(DataSourceProxy dataSourceProxy) throws Exception {
        SqlSessionFactoryBean sqlSessionFactoryBean = new SqlSessionFactoryBean();
        sqlSessionFactoryBean.setDataSource(dataSourceProxy);
        sqlSessionFactoryBean.setMapperLocations(new PathMatchingResourcePatternResolver().getResources(mapperLocations));
        sqlSessionFactoryBean.setTransactionFactory(new SpringManagedTransactionFactory());
        return sqlSessionFactoryBean.getObject();
    }
}
```

主启动

```java
package com.eagle.springcloudalibaba;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration;
import org.springframework.cloud.client.discovery.EnableDiscoveryClient;
import org.springframework.cloud.openfeign.EnableFeignClients;

/**
 * @ClassName: SeataOrderMainApp2001
 * @author: Maybe
 * @date: 2022/3/21  16:59
 */
@SpringBootApplication(exclude = DataSourceAutoConfiguration.class)//取消数据源的自动创建，而是使用自己定义的
@EnableDiscoveryClient
@EnableFeignClients
public class SeataOrderMainApp2001 {
    public static void main(String[] args) {
        SpringApplication.run(SeataOrderMainApp2001.class, args);
    }
}
```

下面的 Storage 微服务模块和 Account 微服务模块都差不多

## @GlobalTransactional

下订单 -> 减库存 -> 扣余额 -> 改（订单）状态

数据库初始情况：

 <img src="img(SpringCloud Alibaba)/e639c859e870eebd847d579347ed8755.png" alt="img" style="zoom:80%;" />

正常下单 - http://localhost:2001/order/create?userId=1&productId=1&count=10&money=100

数据库正常下单后状况：

 <img src="img(SpringCloud Alibaba)/32401b689cf9a7d624fd0f2aea7ce414.png" alt="img" style="zoom:80%;" />

---

**超时异常，没加@GlobalTransactional**

模拟AccountServiceImpl添加超时

```java
@Service
public class AccountServiceImpl implements AccountService {

    private static final Logger LOGGER = LoggerFactory.getLogger(AccountServiceImpl.class);

    @Resource
    AccountDao accountDao;

    /**
     * 扣减账户余额
     */
    @Override
    public void decrease(Long userId, BigDecimal money) {
        LOGGER.info("------->account-service中扣减账户余额开始");
        //模拟超时异常，全局事务回滚
        //暂停几秒钟线程
        try { TimeUnit.SECONDS.sleep(20); } catch (InterruptedException e) { e.printStackTrace(); }
        accountDao.decrease(userId,money);
        LOGGER.info("------->account-service中扣减账户余额结束");
    }
}
```

OpenFeign的调用默认时间是1s以内，所以最后会抛异常。

数据库情况：

 <img src="img(SpringCloud Alibaba)/af40cc3756cef7179e58c813ed404db3.png" alt="img" style="zoom:80%;" />

**故障情况**

- 当库存和账户金额扣减后，订单状态并没有设置为已经完成，没有从零改为1
- 而且由于feign的重试机制，账户余额还有可能被多次扣减

---

**超时异常，加了@GlobalTransactional**

用@GlobalTransactional标注OrderServiceImpl的create()方法。

```java
@Service
@Slf4j
public class OrderServiceImpl implements OrderService {
    
    ...

    /**
     * 创建订单->调用库存服务扣减库存->调用账户服务扣减账户余额->修改订单状态
     * 简单说：下订单->扣库存->减余额->改状态
     */
    @Override
    //rollbackFor = Exception.class表示对任意异常都进行回滚
    @GlobalTransactional(name = "seata-create-order",rollbackFor = Exception.class)
    public void create(Order order)
    {
		...
    }
}
```

还是模拟AccountServiceImpl添加超时，下单后数据库数据并没有任何改变，记录都添加不进来，**达到出异常，数据库回滚的效果**。

## Seata工作原理

以一个示例来说明整个 AT 分支的工作过程。

业务表：`product`

| Field |     Type     | Key  |
| :---: | :----------: | :--: |
|  id   |  bigint(20)  | PRI  |
| name  | varchar(100) |      |
| since | varchar(100) |      |

AT 分支事务的业务逻辑：

```sql
update product set name = 'GTS' where name = 'TXC';
```

### 一阶段

---

过程：

1. 解析 SQL：得到 SQL 的类型（UPDATE），表（product），条件（where name = 'TXC'）等相关的信息。
2. 查询前镜像：根据解析得到的条件信息，生成查询语句，定位数据。

```sql
select id, name, since from product where name = 'TXC';
```

得到前镜像：

|  id  | name | since |
| :--: | :--: | :---: |
|  1   | TXC  | 2014  |

3. 执行业务 SQL：更新这条记录的 name 为 'GTS'。
4. 查询后镜像：根据前镜像的结果，通过 **主键** 定位数据。

```sql
select id, name, since from product where id = 1;
```

得到后镜像：

|  id  | name | since |
| :--: | :--: | :---: |
|  1   | GTS  | 2014  |

5. 插入回滚日志：把前后镜像数据以及业务 SQL 相关的信息组成一条回滚日志记录，插入到 `UNDO_LOG` 表中。

```json
{
	"branchId": 641789253,
	"undoItems": [{
		"afterImage": {
			"rows": [{
				"fields": [{
					"name": "id",
					"type": 4,
					"value": 1
				}, {
					"name": "name",
					"type": 12,
					"value": "GTS"
				}, {
					"name": "since",
					"type": 12,
					"value": "2014"
				}]
			}],
			"tableName": "product"
		},
		"beforeImage": {
			"rows": [{
				"fields": [{
					"name": "id",
					"type": 4,
					"value": 1
				}, {
					"name": "name",
					"type": 12,
					"value": "TXC"
				}, {
					"name": "since",
					"type": 12,
					"value": "2014"
				}]
			}],
			"tableName": "product"
		},
		"sqlType": "UPDATE"
	}],
	"xid": "xid:xxx"
}
```

6. 提交前，向 TC 注册分支：申请 `product` 表中，主键值等于 1 的记录的 **全局锁** 。
7. 本地事务提交：业务数据的更新和前面步骤中生成的 UNDO LOG 一并提交。
8. 将本地事务提交的结果上报给 TC。

 <img src="img(SpringCloud Alibaba)/image-20220322144337165.png" alt="image-20220322144337165" style="zoom:80%;" />

### 二阶段-回滚

---

1. 收到 TC 的分支回滚请求，开启一个本地事务，执行如下操作。
2. 通过 XID 和 Branch ID 查找到相应的 UNDO LOG 记录。
3. 数据校验：拿 UNDO LOG 中的后镜与当前数据进行比较，如果有不同，说明数据被当前全局事务之外的动作做了修改。这种情况，需要根据配置策略来做处理，详细的说明在另外的文档中介绍。
4. 根据 UNDO LOG 中的前镜像和业务 SQL 的相关信息生成并执行回滚的语句：

```sql
update product set name = 'TXC' where id = 1;
```

5. 提交本地事务。并把本地事务的执行结果（即分支事务回滚的结果）上报给 TC。

**注意**：在还原前要首先要校验脏写，对比“数据库当前业务数据”和"after image"。如果两份数据完全一致就说明没有脏写， 可以还原业务数据，如果不一致就说明有脏写, 出现脏写就需要转人工处理。

 <img src="img(SpringCloud Alibaba)/image-20220322144400633.png" alt="image-20220322144400633" style="zoom: 67%;" />

### 二阶段-提交

---

1. 收到 TC 的分支提交请求，把请求放入一个异步任务的队列中，马上返回提交成功的结果给 TC。
2. **异步任务阶段的分支提交请求将异步和批量地删除相应 UNDO LOG 记录。**

 <img src="img(SpringCloud Alibaba)/image-20220322144640150.png" alt="image-20220322144640150" style="zoom:80%;" />

### 回滚日志表

---

UNDO_LOG Table：不同数据库在类型上会略有差别。

以 MySQL 为例：

|     Field     |     Type     |
| :-----------: | :----------: |
|   branch_id   |  bigint PK   |
|      xid      | varchar(100) |
|    context    | varchar(128) |
| rollback_info |   longblob   |
|  log_status   |   tinyint    |
|  log_created  |   datetime   |
| log_modified  |   datetime   |

```sql
-- 注意此处0.7.0+ 增加字段 context
CREATE TABLE `undo_log` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `branch_id` bigint(20) NOT NULL,
  `xid` varchar(100) NOT NULL,
  `context` varchar(128) NOT NULL,
  `rollback_info` longblob NOT NULL,
  `log_status` int(11) NOT NULL,
  `log_created` datetime NOT NULL,
  `log_modified` datetime NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `ux_undo_log` (`xid`,`branch_id`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8;
```



<img src="img(SpringCloud Alibaba)/seata原理流程图.jpg" alt="seata原理流程图" style="zoom:80%;" />

