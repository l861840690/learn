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













