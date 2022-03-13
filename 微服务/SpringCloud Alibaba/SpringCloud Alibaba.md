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
- [开发组写的文档](https://spring-cloud-alibaba-group.github.io/github-pages/greenwich/spring-cloud-alibaba.html)



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
| Nacos              | AP      | 支持       | 高              |

据说Nacos在阿里巴巴内部有超过10万的实例运行，已经过了类似双十一等各种大型流量的考验。

## Nacos安装

- 本地Java8+Maven环境已经OK先
- 从上面的GitHub官网下载Nacos压缩包
- 解压安装包，直接运行bin目录下的startup.cmd
- 命令运行成功后直接访问http://localhost:8848/nacos，默认账号密码都是nacos
- 结果页面