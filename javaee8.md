---
description: JavaEE8规范大纲简介
---

# JavaEE8

## **Java EE Platform（JavaEE平台）**

### Java Platform, Enterprise Edition 8 \(Java EE 8\)**（**Java平台企业版8（Java EE 8）**）**

这个规范定义了JavaEE平台的一个版本。

该版本的主要重点是对HTML 5和新出现的HTTP2.0标准的支持；增强简化和托管bean集成；以及改进运行在云中的应用程序的基础设施。

##  **Web Application Technologies（**网络应用技术**）**

### Java API for WebSocket 1.1

此JSR将定义用于创建WebSocket应用程序的标准API。有各种各样的web应用程序依赖于中央服务器的及时更新，如股票代码、实时地图、聊天应用程序、协作在线工具和基于多人网络的游戏。WebSocket为基于HTTP的解决方案\(如轮询、长轮询和HTTP流\)带来的延迟、可伸缩性和性能问题提供了解决方案。

### Java API for JSON Binding 1.0

JSON作为一种可移植的表示对象和数据的方法已经有了很大的发展。它被越来越多的系统和层所使用，从Web服务到配置数据。

最近建立的JavaAPIforJSON处理\(JSON-P\)规范定义了一个用于解析和生成JSON数据的标准API。下一个逻辑步骤是标准化将JSON转换为Java对象的方法，反之亦然。Json-B将利用JSON-P，并在其之上提供一个转换层。

### Java API for JSON Processing 1.1

此JSR将为JavaAPIforJSON处理规范\(JSON-P\)提供更新。

这个JSR有3个目标**：**1、支持JSON指针和JSON修补程序 2、将编辑/转换操作添加到JSON对象模型中 3、更新API以使用JavaSE 8

### Java Servlet 4.0

该JSR的主要目标是向ServletAPI的用户公开对即将推出的IETF标准HTTP/2的支持。第二个目标是刷新ServletAPI，以满足HTTP1.1中的新特性，并响应社区输入。

### JavaServer Faces 2.3

该JSR旨在提高现有JavaServer Faces（JSF）规范的清晰度。

### Expression Language 3.0（表达语言）

JSP2.0中的专家组认识到EL本身是有用的，并创建了一个独立于JSP规范的单独EL规范，尽管它们属于同一个JSR。这个拟议的规范将把EL规范放在自己的JSR中。

### JavaServer Pages 2.3（Java服务页面）

JSP技术的重点是简化动态Web内容的生成。JSP2.0规范\(JSR-152\)通过集成一种简单但功能强大的表达式语言、简化标记扩展API、增强纯XML语法以及其他重要的增强功能，大大扩展了该技术。

### Standard Tag Library for JavaServer Pages \(JSTL\) 1.2（JavaServerPages标准标记库）

这个JSR请求为JavaServer页面创建一个标准标记库。这个标准标记库可以在所有兼容的JSP容器中使用，JSP作者和JSP创作工具可以使用它们来创建JSP页面。

## **Enterprise Application Technologies（**企业应用技术**）**

### Batch Applications for the Java Platform 1.0（Java Platform 1.0的批处理应用程序）

这项提议打算具体说明以下几点：1、批作业 2、批作业步骤 3、批量应用 4、批执行器 5、批作业管理器

### Concurrency Utilities for Java EE 1.0（Java EE 1.0的并发实用程序）

JavaEE规范的并发实用程序通过构建JSR-166提供了一个干净、简单、独立的API，使得它适合在任何JavaEE容器中使用。

### Contexts and Dependency Injection for Java 2.0（Java 2.0的上下文和依赖注入）

CDI 2将对CDI 1.1进行重大更新，并将重点放在两个主要功能上：

1.在Java EE容器之外定义CDI的行为。

2.使CDI更具模块化，以帮助其他Java EE规范更好地与之集成。

### Dependency Injection for Java 1.0（Java 1.0的依赖注入）

这个JSR将标准化：

     1、用于可注入类的一组注释

     2、一个类型化的、对用户友好的注入器配置api，它为更高级别的依赖注入配置方法提供了一个集成点。

### Bean Validation 2.0（Bean验证2.0）

bean验证标准化了Java平台的约束定义、声明和验证。与许多其他规范\(CDI、JAX-RS、JPA等\)的集成并建立了框架。

### Enterprise JavaBeans 3.2（企业JavaBeans 3.2）

EnterpriseJavaBeans\(EJB\)是一种用于开发和部署基于组件的业务应用程序的体系结构。使用EnterpriseJavaBeans架构编写的应用程序具有可伸缩性、事务性和多用户安全性。

EnterpriseJavaBeans3.0规范的重点是为EJBAPI带来易用性。EnterpriseJavaBeans 3.1规范从开发人员的角度进一步简化了EJB体系结构，同时还根据社区的需要添加了重要的新功能。

EnterpriseJavaBeans 3.2的目标是巩固这些进步，继续简化EJB体系结构，并为JavaEE平台范围内进一步启用云计算的目标提供支持。EJB3.2的范围在专注于这些目标时是相对受限的。

### Enterprise JavaBeans 3.1/Interceptors 1.2（拦截器1.2）JSR318

EnterpriseJavaBeans3.0规范的重点是为EJBAPI带来易用性。EnterpriseJavaBeans 3.1规范的目的是进一步简化EJB体系结构，从开发人员的角度降低其复杂性，同时根据社区的需要添加新功能。

重点将放在核心会话bean和消息驱动的bean组件模型及其客户端API上。

### Java EE Connector Architecture 1.7（Java EE连接器体系结构1.7）

JavaEE连接器架构1.6规范的目的是解决J2EE连接器架构1.5中需要连接器专家组和公众进一步支持的领域。本规范打算涉及的领域如下：

通用流入上下文

连接器架构1.5支持事务流入上下文。WorkManager合同与事务流入上下文密切相关。此特性将将事务流入上下文增强到更一般的上下文，以适应其他功能，如安全性。工作经理机制将变得更加灵活和独立于流入合同之外。

### Java Persistence 2.2（Java持久性2.2）

JavaPersistence2.1规范的目的是扩展JavaPersistenceAPI，以包括社区请求的其他特性。专家组的目标将是评估这些问题，并确定和继续改进Java持久性API的总体编程模型和工具的方向。

### Common Annotations for the Java Platform 1.3（Java Platform 1.3的常见注释）

本JSR的目的是定义一小部分公共注释，以便在其他JSR中使用。希望这将有助于避免不同JSR中定义的注释之间不必要的冗余或重复。

### Java Message Service API 2.0（Java消息服务API 2.0）

此JSR建议开发JMS规范的新修订版。自上一次修订以来，JavaSE、JavaEE和消息传递领域都有了许多发展。正因为如此，修改规范的建议在复杂性和雄心上差异很大。

### Java Transaction API \(JTA\) 1.2

本文档介绍Java事务API（JTA）。 JTA指定本地 事务管理器与参与交易的各方之间的Java接口 分布式交易系统：应用程序，资源管理器和 应用服务器。

### JavaMail 1.6

许多人需要Java平台的附加组件：邮件和消息传递框架。本规范中描述的JavaMailTM API满足了需求。 JavaMail API提供了一组抽象类，这些抽象类定义了组成邮件的对象 系统。

##  **Web Services Technologies（Web服务技术）**

### Java API for RESTful Web Services \(JAX-RS\) 2.1

该规范定义了一组Java API，用于开发根据Web服务构建的Web服务。

### Implementing Enterprise Web Services 1.3**（**实施企业Web服务1.3**）**

该规范定义了Java EE Web服务（WSEE）架构。 这是一个服务架构 利用Java EE组件体系结构来提供客户端和服务器编程模型， 可以跨应用程序服务器移植和互操作，提供可扩展的安全环境**。**

### Web Services Metadata for the Java Platform 2.1**（**Java Platform 2.1的Web服务元数据**）**

该规范定义了简化的编程模型，可促进和加速 企业Web服务的开发。此JSR减少了实现Web所需的信息量 Java EE上的服务，方法是使用元数据声明性地指定 每个应用程序都提供。

### Java API for XML-Based RPC \(JAX-RPC\) 1.1 \(Optional\)**（**用于基于XML的RPC（JAX-RPC）1.1的Java API**）**

基于XML的RPC服务器应用程序可以将Web服务定义，描述和导出为 基于RPC的服务。

### Java API for XML Registries \(JAXR\) 1.0 \(Optional\)

这个JSR请求创建JavaAPIforXMLRegistry1.0规范\(JAXR\)。JAXR可被视为类似于，Java命名和目录接口\(JNDI\)**，**但是专门为与xml相关的商业信息的互联网共享而设计的。

##  **Management and Security Technologies（管理和安全技术）**

### Java EE Security API 1.0**（**Java EE安全性API 1.0**）**

这个JSR的目标是通过确保SecurityAPI方面在现代云/PaaS应用程序范例中很有用来改进JavaEE平台。这提高了所有JavaEE服务器的自包含应用程序可移植性，并促进了现代编程概念\(如表达式语言、上下文和依赖项注入\)的使用。

### Java Authentication Service Provider Interface for Containers 1.1**（**容器1.1的Java身份验证服务提供程序接口**）**

拟议的规范将定义一个标准服务提供者接口，通过该接口可以将身份验证机制提供程序与容器集成。通过此接口集成的提供者将用于建立容器访问决策中使用的身份验证标识，包括容器在调用其他容器中的组件时使用的身份验证标识。

### Java Authorization Contract for Containers 1.5**（**Java容器授权合同1.5**）**

拟议的规范将定义新的java.security.Permission类以满足基于J2EE角色的授权模型.该规范将定义容器访问决策与这些实例上的操作的绑定。

### Java EE Application Deployment 1.2**（**Java EE应用程序部署1.2**）**

这是Java的规范™2企业版部署API。这个部署体系结构定义了支持多个提供程序，用于在任何Java EE平台产品上配置和部署应用程序。

### J2EE Management 1.1**（**J2EE管理1.1**）**

JavaTM 2企业版（J2EETM）平台的日益普及 已授权规范Java交付的通用框架 企业管理和监控服务。 JSR77的目标是抽象 J2EE架构的基本可管理方面提供了良好的基础 定义的用于实现检测和信息访问的模型。

### Debugging Support for Other Languages 1.0（对其他语言的调试支持1.0）

本规范建立了相关Java的标准化工具TM虚拟机字节代码到Java以外语言的源代码TM编程语言

##  **Java EE-related Specs in Java SE（**Java SE中与Java EE相关的规范**）**

### Java Management Extensions \(JMX\) 2.0**（**Java管理扩展（JMX）2.0**）**

JMX规范将提供管理架构、API和服务，用于构建基于Web、分布式、动态和模块化的解决方案，以管理启用Java的资源。

### SOAP with Attachments API for Java \(SAAJ\) Specification 1.3（带有Java附件API的SOAP（SAAJ）规范1.3）

JAXM提供了一个API，用于使用ebXML.org、OASIS、W3C和IETF定义的在线协议打包和传输业务事务。

### Streaming API for XML \(StAX\) 1.0（XML流媒体API（StAX）1.0）

用于XML\(StAX\)解析的流API将为XML指定一个基于Java的拉式解析API。流API通过公开一个简单的基于迭代器的API向程序员提供解析控制。这允许程序员请求下一个事件\(拉出事件\)，并允许以过程方式存储状态。

### Java API for XML Processing \(JAXP\) 1.6（用于XML处理的Java API（JAXP）1.6）

本文档介绍了用于XML处理的Java API，版本1.4。 此版本的规范 通过一组标准的Java引入了对解析和处理XML文档的基本支持 平台API。

### Java Database Connectivity 4.0（Java数据库连接4.0）

该规范旨在通过提供易于开发的重点特性和在实用程序和API级别的改进来改善Java应用程序对SQL数据存储的访问。

### Java Architecture for XML Binding \(JAXB\) 2.2（用于XML绑定的Java体系结构（JAXB）2.2）

JAXB2.0是JSR 31 Java的后续，基于JAXB1.0JAXB1.0中引入的体系结构的XML数据绑定规范降低了开发人员从JavaTM应用程序中操作XML内容的障碍。JAXB2.0将研究对所有W3CXMLSchema的支持，包括频繁请求的特性，如类型和元素替换。

### Java API for XML-Based Web Services \(JAX-WS\) 2.2（基于XML的Web服务的Java API（JAX-WS）2.2）

JAX-RPC 2.0规范以新的特性扩展了现有的JAX-RPC 1.0规范，包括以下部分或全部功能：直接支持基于JAXB 2.0的数据绑定、支持最新的W3C和WS-i标准\(例如SOAP 1.2、WSDL 1.2\)、Java&lt;-&gt;WSDL映射的标准化元数据、易于开发的特性、对Web服务更容易演化的支持、改进的处理程序框架、对异步RPC和非HTTP传输的支持。

### JavaBeans Activation Framework \(JAF\) 1.1（JavaBeans激活框架（JAF）1.1）

JavaBeans™激活框架规范是数据输入和注册表技术的标准扩展 Java™平台。



\*\*\*\*













