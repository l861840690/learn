---
description: Spring Cloud Alibaba参考文档的大纲
---

# Spring Cloud Alibaba



## 1.Introduction（介绍）

Spring Cloud Alibaba旨在为微服务开发提供一站式解决方案。这个项目包括开发分布式应用程序和服务所需的组件，这样开发人员可以使用Spring云编程模型轻松地开发分布式应用程序。

有了Spring Cloud Alibaba，只需要添加一些注解和配置，就可以将Alibaba的分布式解决方案应用到自己的应用中，并用Alibaba中间件构建自己的分布式系统。

## 2. Dependency Management（依赖管理）

如果您是Maven中心用户，请将BOM添加到pom.xml部分。这将允许您省略任何Maven依赖项的版本，而是将版本控制委托给BOM。

## 3. Spring Cloud Alibaba Nacos Discovery（Spring Cloud阿里巴巴Nacos发现）

Nacos是一个易于使用的动态服务发现、配置和服务管理平台，用于构建云本地应用程序。通过Spring Cloud阿里Nacos发现，您可以基于Spring Cloud的编程模型快速访问Nacos服务注册功能。

### 3.1 Service Registration/Discovery: Nacos Discovery（服务注册/发现：Nacos发现）

服务发现是微服务体系结构中的关键组件之一。在这样的体系结构中，手动为每个客户机配置服务列表可能是一项令人望而生畏的任务，并且使动态扩展变得极其困难。Nacos发现帮助您自动向Nacos服务器注册服务，Nacos服务器跟踪服务并动态刷新服务列表。

### 3.2 How to Introduce Nacos Discovery for service registration/discovery（如何引入Nacos Discovery进行服务注册/发现）

请使用组ID为com.alibaba.cloud的启动程序，并将工件ID为spring-cloud-starter-alibaba-nacos-discovery。

### 3.3 An example of using Nacos Discovery for service registration/discovery and call（使用Nacos Discovery进行服务注册/发现和呼叫的示例）

Nacos Discovery与Netflix Ribbon，RestTemplate或OpenFeign集成在一起，可用于服务到服务的呼叫。

#### 3.3.1 Nacos Server Startup（Nacos服务器启动）

有关如何下载和启动Nacos的详细信息，请访问Nacos网站。

Nacos Server启动后，请访问http：// ip：8848以查看控制台（默认帐户名/密码为nacos / nacos）

#### 3.3.2 Start a Provider Application（启动提供者应用程序）

本小节给出了演示如何将服务注册到Nacos的例子。

#### 3.3.3 Start a Consumer Application（启动消费者应用程序）

在本例中，将使用最原始的方式，也就是将LoadBalanceClient和restemlate显式地结合起来访问RESTful服务。

### 3.4 Nacos Discovery Endpoint（Nacos Discovery端点）

Nacos Discovery在内部提供一个端点，其对应的端点id为Nacos Discovery。

端点公开的json包含两个属性：

subscribe（订阅）：显示当前服务订阅服务器

NacosDiscoveryProperties：显示当前服务的当前基本Nacos配置

本小节还给出了服务实例如何访问终结点的例子。

### 3.5 More Information about Nacos Discovery Starter Configurations（有关Nacos Discovery Starter配置的更多信息）

本节包含了Nacos Discovery启动器的其他配置

## 4. Spring Cloud Alibaba Nacos Config（Spring Cloud阿里Nacos配置）

Nacos是一个易于使用的动态服务发现、配置和服务管理平台，用于构建云本地应用程序。

### 4.1 How to Introduce Nacos Config for configuration（如何引入Nacos配置）

请使用组ID为com.alibaba.cloud的启动程序，并将工件ID为spring-cloud-starter-alibaba-nacos-config使用。

### 4.2 Quickstart（快速入门）

Nacos Config使用DataId和GROUP来确定配置。

本节例子中显示DataId使用myDataid，GROUP使用DEFAULT\_GROUP，并配置格式为Properties的配置项。

### 4.3 Add Configurations with DataId in YAML Format（添加YAML格式的DataId配置）

Nacos配置也支持yaml格式。您只需要完成以下两个步骤。

1、 在bootstrap.properties文件中，添加以下行以声明DataId的格式为yaml。

2、 在Nacos控制台上添加一个DataId为yaml格式的配置。

具体配置本节中都有示例。

### 4.4 Support Dynamic Configuration Udpates（支持动态配置Udpates）

Nacos Config还支持动态配置更新。启动Spring Boot应用程序测试的代码在本节中给出了示例。

### 4.5 Support configurations at the profile level（配置文件级别的支持配置）

当配置由Nacos Config加载时，DataId为$ {spring.application.name}的基本配置。 $ {file-extension：properties}和$ {spring.application.name}-$ {profile}的DataId。 $ {file-extension：properties}也被加载。 如果需要使用来自不同环境的不同配置，则可以使用Spring提供的$ {spring.profiles.active}配置。

### 4.6 Support Custom Namespaces（支持自定义命名空间）

有关Nacos中名称空间的详细信息，请参阅Nacos概念

命名空间用于隔离不同租户的配置。 跨不同名称空间的组和数据ID可以相同。 命名空间的典型场景是隔离不同环境的配置，例如，开发/测试环境与生产环境（配置和服务等）之间的隔离。

### 4.7 Support Custom Groups（支持自定义组）

如果未定义{spring.cloud.nacos.config.group}配置，则默认使用DEFAULT\_GROUP。 如果需要定义自己的组，示例中给出了方法。

### 4.8 Support Custom Data Id（支持自定义数据ID）

从Spring Cloud Alibaba Nacos Config开始，数据ID可以自定义。 有关此部分的详细设计，请参阅Github问题。本节给出了完整的示例。

### 4.9 Nacos Config Endpoint（Nacos配置端点）

Nacos Config在内部提供一个具有相应nacos-config端点ID的端点。

端点公开的json包含三个属性：

来源：当前应用程序配置数据信息 RefreshHistory：配置刷新历史记录 NacosConfigProperties：显示当前服务的当前基本Nacos配置 

本节给出了服务实例如何访问端点的例子。

### 4.10 Disable Nacos Config AutoConfiguration（禁用Nacos Config自动配置）

设置spring.cloud.nacos.config.enabled = false禁用Spring Cloud Nacos配置自动配置。

### 4.11 More Information about Nacos Config Starter Configurations（有关Nacos Config Starter配置的更多信息）

本节示例显示了Nacos Config的启动程序的其他配置。

## 5. Spring Cloud Alibaba Sentinel（Spring Cloud阿里巴巴哨兵）

### 5.1 Introduction of Sentinel（哨兵介绍）

随着微服务的普及，服务调用的稳定性变得越来越重要。 Sentinel以“流量”为切入点，在流量控制，断路和负载保护等多个领域工作，以保护服务可靠性。

### 5.2 How to Use Sentinel（如何使用哨兵）

如果要在项目中使用Sentinel，请使用组ID为com.alibaba.cloud的启动程序，并将工件ID为spring-cloud-starter-alibaba-sentinel。

#### 5.2.1 Sentinel Dashboard（哨兵仪表板）

Sentinel仪表板是一个轻量级的控制台，提供诸如机器发现，单服务器资源监视，群集资源数据概述以及规则管理等功能。

#### 5.2.2 Configure the Dashboard（配置仪表板）

在spring.cloud.sentinel.transport.port中指定的端口号将在应用程序的相应服务器上启动HTTP Server，并且该服务器将与Sentinel仪表板进行交互。

### 5.3 OpenFeign Support（OpenFeign支持）

Sentinel与OpenFeign组件兼容。 要使用它，除了引入sendinel-starter依赖关系之外，还需要完成以下两个步骤：

在属性文件中启用伪装的Sentinel支持。 feign.sentinel.enabled = true 添加openfeign启动器依赖项以触发并启用哨兵启动器。

### 5.4 RestTemplate Support（RestTemplate支持）

Spring Cloud Alibaba Sentinel支持使用Sentinel保护RestTemplate服务调用。 为此，在构造RestTemplate bean时需要添加@SentinelRestTemplate批注。

### 5.5 Dynamic Data Source Support（动态数据源支持）

SentinelProperty提供数据源属性以配置数据源。本节给出了配置示例。

### 5.6 Support Zuul（支持Zuul）

如果要与Zuul一起使用Sentinel Starter，则需要添加spring-cloud-alibaba-sentinel-gateway依赖关系，并且需要添加spring-cloud-starter-netflix-zuul依赖关系以让Zuul AutoConfiguration类在网关中 模块生效。

### 5.7 Support Spring Cloud Gateway（支持Spring Cloud Gateway）

如果您想将Sentinel Starter与Spring Cloud Gateway一起使用，则需要添加spring-cloud-alibaba-sentinel-gateway依赖项并添加spring-cloud-starter-gateway依赖项以使模块中的Spring Cloud Gateway AutoConfiguration类生效。

### 5.8 Sentinel Endpoint（哨兵端点）

Sentinel在内部为端点提供了一个相应的哨点ID。端点公开的json包含多个属性，在本节中都有介绍。

### 5.9 Configuration（配置）

本节表格中显示了当ApplicationContext中有相应的bean类型时，将采取一些措施。

## 6. Spring Cloud Alibaba Dubbo

### 6.1 Introduction（简介）

无论开发人员是Dubbo用户还是Spring Cloud用户，Dubbo Spring Cloud都是基于Dubbo Spring Boot 2.7.3 \[1\]和Spring Cloud 2.x开发的。 轻松导航和上载应用程序，成本接近“零”成本。 Dubbo Spring Cloud旨在简化Cloud Native开发成本，提高研发性能以及提高应用程序性能。

### 6.2 Features（特点）

由于Dubbo Spring Cloud构建在本地Spring Cloud之上，因此其服务治理功能被认为是Spring Cloud Plus。它不仅完全覆盖了Spring Cloud的本机特性\[5\]，而且还提供了一个更加稳定和成熟的实现，本节介绍了它的特性。

### 6.3 Reference（参考）

本节中列出了Spring Cloud Alibaba Dubbo参考了哪些技术。

## 7. Spring Cloud Alibaba RocketMQ Binder

### 7.1 Introduction of RocketMQ（RocketMQ简介）

RocketMQ是一个开源的分布式消息系统。 它基于高度可用的分布式群集技术，并提供具有低延迟和高稳定性的消息发布和订阅服务。 RocketMQ被广泛用于各种行业，例如异步通信，企业支持，金融结算，电信，电子商务，物流，市场营销，社交媒体，即时消息传递，移动应用程序，移动游戏，vedios，IoT和 车联网。

### 7.2 RocketMQ Usages（RocketMQ 用法）

本节介绍了如何下载RocketMQ，以及如何去使用它。

### 7.3 Introduction of Spring Cloud Stream（Spring Cloud Stream简介）

Spring Cloud Stream是一个微服务框架，用于基于消息构建架构。 它可以帮助您基于SpringBoot创建可用于生产环境的单服务器Spring应用程序，并使用Spring Integration与Broker连接。

Spring Cloud Stream提供了消息中间件配置的统一抽象，并提出了诸如发布-订阅，使用者组和分区之类的概念。

### 7.4 How to use Spring Cloud Alibaba RocketMQ Binder （如何使用Spring Cloud阿里巴巴RocketMQ Binder）

要使用Spring Cloud Alibaba RocketMQ Binder，只需使用本节提供的Maven坐标将其添加到Spring Cloud Stream应用程序中。

### 7.5 How Spring Cloud Alibaba RocketMQ Binder Works（Spring Cloud Alibaba RocketMQ Binder 如何工作）

本节介绍了Spring Cloud Stream RocketMQ Binder的实现架构。

### 7.6 Support MessageSource（支持消息源）

SCS RocketMQ Binder支持MessageSource，可以通过拉去模式接收消息。

### 7.7 Configuration Options（配置选项）

#### 7.7.1 RocketMQ Binder Properties（RocketMQ Binder 属性）

#### 7.7.2 RocketMQ Consumer Properties（ RocketMQ 消费者属性）

#### 7.7.3 RocketMQ Provider Properties（RocketMQ 提供程序属性）

## 8. Spring Cloud Alibaba Cloud ANS（Spring Cloud阿里云ANS）

ANS（应用程序命名服务）是EDAS的组件。 Spring Cloud Alibaba Cloud ANS提供符合Spring Cloud规范的商业版本的服务注册和发现，因此您可以在本地开发应用程序并在云上运行它们。

### 8.1 How to Introduce Spring Cloud Alibaba Cloud ANS（如何引入Spring Cloud Alibaba Cloud ANS）

如果要在项目中使用ANS，请使用组ID为com.alibaba.cloud的启动程序，并将工件ID为spring-cloud-starter-alicloud-ans。

### 8.2 Use ANS to Register Service（使用ANS注册服务）

在客户端上引入Spring Cloud AliCloud ANS Starter时，服务的元数据（例如IP，端口号和weright）将自动注册到注册中心。 客户端将与服务器保持心跳，以证明其能够正确提供服务。

### 8.3 Start Registration Center（启动注册中心）

ANS使用两种类型的注册中心。一个是免费的轻量级配置中心，另一个是通过EDAS提供的云端注册中心。通常，您可以使用轻量级版本进行应用程序开发和本地测试，并使用EDAS进行canary部署或生产。

#### 8.3.1 Start Lightweight Configuration Center（启动轻量级配置中心）

有关如何下载和安装轻量级配置中心的详细信息，请参考配置轻量级配置中心。

#### 8.3.2 User Registration Center on the Cloud（云端用户注册中心）

在云端使用注册中心可以使您免于繁琐的服务器维护工作，同时还可以提供更好的稳定性。 在云端使用注册中心和轻量级配置中心之间在代码级别上没有区别，但是配置方面存在一些差异。

## 9. Spring Cloud Alibaba Cloud ACM

Spring Cloud AliCloud ACM是Spring Cloud客户端上商业产品应用程序配置管理（ACM）的实现，并且是免费的。

使用Spring Cloud AliCloud ACM可基于Spring Cloud的编程模型快速访问ACM配置管理功能。

### 9.1 How to Introduce Spring Cloud Alibaba Cloud ACM（如何引入Spring Cloud Alibaba Cloud ACM）

### 9.2 Use ACM to Manage Configurations（使用ACM管理配置）

将Spring Cloud Alibaba Cloud ACM Starter引入客户端后，该应用程序将在启动时自动从配置管理服务器获取配置信息，并将配置注入Spring Environment。

本节提供了一个简单的示例。

#### 9.2.1 Start Configuration Center（启动配置中心）

ACM使用两种类型的配置中心。一个是轻量级配置中心，另一个是在阿里云上使用的ACM。通常，您可以使用轻量级版本进行应用程序开发和本地测试，并使用ACM进行canary部署或生产。

#### 9.2.2 Add Configuration in the Configuration Center（在配置中心添加配置）

#### 9.2.3 Start Application Verification（开始应用验证）

本小节的示例，您可以看到控制台上打印的值是我们在轻量级配置中心中配置的值。

### 9.3 Modify Configuration File Extension（修改配置文件扩展名）

spring-cloud-starter-alicloud-acm中dataId的默认文件扩展名是properties。 除了属性外，还支持yaml。 您可以使用spring.cloud.alicloud.acm.file-extension设置文件扩展名。 只需将其设置为yaml或yml格式即可。

### 9.4 Dynamic Configuration Refresh（动态配置刷新）

spring-cloud-starter-alicloud-acm支持动态配置更新。 在配置中心中更新配置时，将发布Spring中的RefreshEvent。 具有@RefreshScope和@ConfigurationProperties批注的所有类将自动刷新。

### 9.5 Configure Profile Granularity（配置配置文件粒度）

通过spring-cloud-starter-alicloud-acm加载配置时，使用DataId {spring.application.name}进行配置。 {file-extension}将首先加载。 如果spring.profiles.active中包含内容，则为spring.profile的内容，以及配置的数据ID格式为{spring.application.name}-{profile}。 {file-extension}也将依次加载，后者具有更高的优先级。

### 9.6 Support Custom ACM Timeout（支持自定义ACM超时）

ACM client get config from sever的默认超时为3000 ms。如果需要定义超时，请设置配置spring.cloud.aliyun.acm.timeout，单位为毫秒。

### 9.7 Support Custom Group Configurations（支持自定义组配置）

如果未定义{spring.cloud.alicloud.acm.group}配置，则默认使用DEFAULT\_GROUP。 如果需要定义自己的组，本节介绍了可以使用的方法。

#### 9.7.1 Support Shared Configurations（支持共享配置）

ACM提供了在多个应用程序之间共享相同配置的解决方案。 您可以通过在Bootstrap中添加spring.application.group配置来执行此操作。

### 9.8 Actuator Endpoint（执行器端点）

ACM的执行器端点为/ acm，config表示ACM元数据配置信息，runtime.sources对应于从ACM服务器获得的配置信息，上一次刷新时间runtime.refreshHistory对应于动态刷新历史记录。

## 10. Spring Cloud Alibaba Cloud OSS

OSS（对象存储服务）是阿里云上的存储产品。 Spring Cloud阿里云OSS提供符合Spring Cloud规范的商业化存储服务。 我们提供易于使用的API，并支持将Resource集成到Spring框架中。

### 10.1 How to Introduce Spring Cloud Alibaba Cloud OSS（如何引入 Spring Cloud Alibaba Cloud OSS）

### 10.2 How to Use OSS API（如何使用OSS API）

#### 10.2.1 Configure OSS（配置OSS）

在开始使用Spring Cloud Alibaba Cloud OSS之前，请在application.properties中添加本节示例给出的配置。

#### 10.2.2 Introduce OSS API（引入OSS API）

Spring Cloud Alibaba Cloud OSS的OSS API基于官方的OSS SDK，并包含用于上载，下载，查看文件的API。

这是一个使用OSS API的简单应用程序。

### 10.3 Integrate with the Resource Specifications of Spring（与Spring的资源规范集成）

Spring Cloud阿里云OSS集成了Spring框架的资源，使您可以轻松使用OSS资源。

本节包含了有关如何使用资源的简单示例。

### 10.4 Use STS Authentication（使用STS身份验证）

除了AccessKeys，Spring Cloud Alibaba Cloud OSS还支持STS身份验证。 STS是具有临时安全令牌的身份验证方法，通常用于第三方临时访问其资源。

对于第三方临时访问资源，本节给出了配置步骤。

### 10.5 More Configurations for the Client（客户端的更多配置）

除了基本配置，Spring Cloud Alibaba Cloud OSS还支持许多其他配置，这些配置也包含在application.properties文件中。

本节给出了一些例子。

## 11. Spring Cloud Alibaba Cloud SchedulerX

SchedulerX（分布式作业调度）是阿里云产品EDAS的组件。 Spring Cloud Alibaba Cloud SchedulerX提供符合Spring Cloud规范的分布式作业调度。 SchedulerX提供具有几秒钟的高精度，高稳定性和高可用性的定时作业调度服务，并支持多种作业类型，例如简单的单服务器作业，简单的多主机作业，脚本作业和网格作业。

### 11.1 How to Introduce Spring Cloud Alibaba Cloud SchedulerX（如何引入Spring Cloud Alibaba Cloud SchedulerX）

### 11.2 Start SchedulerX（启动SchedulerX）

将Spring Cloud Alibaba Cloud SchedulerX Starter引入客户端后，您只需要完成一些简单的配置，就能自动初始化SchedulerX服务。

本节含有一个简单的示例。

### 11.3 Compile a simple job（编译一个简单的工作）

简单作业是最常用的作业类型。 您只需要实现ScxSimpleJobProcessor接口。

本节含有一个简单的单服务器作业示例。

### 11.4 Job Scheduling（作业调度）

转到SchedulerX作业页面，选择“测试”区域，然后单击右上角的“创建作业”以创建作业，本节给出了示例。

### 11.5 Usage in Production Environment（在生产环境中的使用）

前面的示例显示了如何在“测试”区域中使用SchedulerX，该区域主要用于本地测试。

在生产级别，除了如上所述的组ID和名称空间之外，您还需要完成一些其他配置。 请参阅本节中的示例。

## 12. Spring Cloud Alibaba Cloud SMS（Spring Cloud阿里云短信）

SMS（短消息服务）是一种覆盖全球的消息服务，阿里巴巴SMS提供便捷，高效和智能的通信功能，可帮助企业快速联系其客户。

Spring Cloud Alibaba Cloud SMS提供了易于使用的API，可用于快速访问基于Spring Cloud Alibaba SMS的Alibaba Cloud的SMS服务。

### 12.1 How to Introduce Spring Cloud Alibaba Cloud SMS（如何引入Spring Cloud Alibaba Cloud SMS）

### 12.2 How to use SMS API（如何使用SMS API）

#### 12.2.1 Configure SMS（配置SMS）

在开始使用Spring Cloud Alibaba Cloud SMS之前，请在application.properties中添加本节中给出的配置。

#### 12.2.2 Introduce SMS API（引入SMS API）

Spring Cloud Alicloud SMS中的SMS API基于阿里云SMS SDK。 它具有单个SMS发送，多个SMS批量发送，SMS查询，SMS消息（SMS接收消息和上游SMS消息）类操作API。

本节含有如何使用SMS api发送短消息的简单示例。

### 12.3 The Advanced Features of SMS Api（SMS Api的高级功能）

为了降低学习成本，Spring Cloud Alicloud SMS软件包的API接口与官方网站提供的API和示例保持一致。

批量短信发送 请参考本节示例，以通过批量SMS发送快速开发功能。 在Controller中添加以下代码或创建新的Controller。











