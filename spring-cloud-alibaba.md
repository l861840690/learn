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







