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





