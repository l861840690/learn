---
description: Spring5.22大纲
---

# Spring Framework

### 

## **1.**The IoC Container（控制反转容器）

### 1.1.SpringIoC容器和bean简介

IoC：也称为依赖注入\(DI\)。它是一个过程，对象仅通过构造函数、工厂方法的参数或在从工厂方法构造或返回对象实例后在对象实例上设置的属性来定义它们的依赖关系\(即与它们一起工作的其他对象\)。然后，容器在创建bean时注入这些依赖项。从根本上说，这个过程是bean本身的逆\(因此是名称、控制反转\)，它通过使用类的直接构造或服务定位器模式等机制来控制其依赖项的实例化或位置。

Bean：在Spring中，构成应用程序主干并由SpringIoC容器管理的对象称为bean。bean是由SpringIoC容器实例化、组装和以其他方式管理的对象。

### 1.2.Container Overview（集装箱概述）

介绍了org.springframework.context.ApplicationContext接口的作用以及如何去配置spring的配置文件。

#### 1.2.1.**Configuration Metadata**（配置元数据）

介绍了基于XML的配置元数据和基于Java的配置元数据。

#### **1.2.2. Instantiating a Container（实例化容器）**

介绍了如何实例化springioc容器，以及组合基于xml的配置元数据。在Spring的GroovyBean定义DSL中表示bean定义，通常这种配置位于“.groovy”文件中。

#### 1.2.3.**Using the Container（使用容器）**

介绍了如何去使用ioc容器。

### 1.3.Bean Overview（Bean概述）

SpringIoC容器管理一个或多个bean。这些bean是通过提供给容器的配置元数据\(例如，以xml的形式\)创建的。主要介绍了组成每个bean定义的一组属性的描述。

#### 1.3.1.Naming Beans（Bean的命名）

每个bean都有一个或多个标识符。这些标识符在承载bean的容器中必须是唯一的。bean通常只有一个标识符，如果需要一个以上的标识符，额外的可以被视为别名。配置别名在基于xml的配置元数据中指定bean标识符可以直接使用别名。

#### 此外还介绍了**在Bean定义之外对Bean进行混叠**

#### **1.3.2.**Instantiating Beans（实例化Bean）

主要介绍了实例化Bean的三种方式，1、用构造器实例化 2、用静态工厂方法实例化 3、使用实例化工厂方法实例化

### 1.4.Dependencies（依赖性）

#### 1.4.1.**Dependency Injection（依赖注入）**

使用DI原则，代码更加简洁，当对象提供依赖项时，解耦更有效。DI有两个主要变体：基于构造函数的依赖注入和基于setter的依赖注入。之后还介绍了依赖解决过程与依赖注入的示例。

#### 1.4.2.**Dependencies and Configuration in Detail（依赖性和配置的细节）**

本小节的内容包含了直线值（原语、字符串等）、对其他bean的引用、内部bean、集合、空和空字符串值、使用p命名空间的xml快捷方式、使用c-命名空间的xml快捷方式、复合属性名。

#### 1.4.3.**Using depends-on（使用依赖）**

介绍了depens-on属性的用法，该属性既可以指定初始化时依赖项，也可以指定单例bean。

#### 1.4.4. Lazy-initialized Beans（延迟初始化bean）

介绍了如何延迟初始化bean。

#### 1.4.5.Autowiring Collaborators（自动装配）

介绍了如何使用自动装配，自动装配的局限性和缺点，如何从自动装配中排除一个bean。

#### 1.4.6. Method Injection（方法注入）

讲述了什么情况下需要使用方法注入，如何使用方法注入、查找方法注入和任意方法替换。

### 1.5. Bean Scopes（bean的作用域）

介绍了bean的所有作用域

#### 1.5.1.The Singleton Scope（单例作用域）

当定义bean定义并将其作用域为单例时，SpringIoC容器将创建由该bean定义定义的对象的一个实例。此单个实例存储在此类单例bean的高速缓存中，而对该命名bean的所有后续请求和引用都返回缓存的对象。

#### 1.5.2.The Prototype Scope（原型作用域）

每次对特定bean提出请求时，bean部署的非单例原型作用域都会导致创建一个新bean实例。

#### 1.5.3. Singleton Beans with Prototype-bean Dependencies（**带有原型bean依赖项的单例bean**）

#### 1.5.4. Request, Session, Application, and WebSocket Scopes（**请求、会话、应用程序和WebSocket Scopes**）

#### 1.5.5. Custom Scopes（自定义**作用域**）

介绍了如何创建自定义作用域和使用自定义作用域。

### 1.6. Customizing the Nature of a Bean（定制bean的性质）

#### 1.6.1. Lifecycle Callbacks（生命周期回调）

通过实现SpringInitializingBean和DisposableBean接口，可以与容器的bean生命周期管理进行交互。此节内容介绍了初始化回调与销毁回调，默认初始化和销毁方法，如何控制bean生命周期的三种选项，如何启动和关闭回调，在非Web应用程序中关闭SpringIoC容器。

#### **1.6.2. ApplicationContextAware和BeanNameAware**

\*\*\*\*
