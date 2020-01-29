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

两个感知接口，分别用来声明ApplicationContext和bean的名称。

#### 1.6.3.Other Aware Interfaces（其他感知接口）

介绍了一些感知接口的作用和用法。

### 1.7. Bean Definition Inheritance（bean定义继承）

子bean定义从父定义继承配置数据。子定义可以覆盖某些值，也可以根据需要添加其他值。使用父bean和子bean定义可以节省大量的输入。这实际上是一种模版形式。本节内容介绍了使用基于xml的配置元数据时，如何使用parent属性，将父bean指定为此属性值。

### 1.8.Container Extension Points（容器扩展点）

通常，应用程序开发人员不需要子类。ApplicationContext实现类。相反，可以通过插入特殊集成接口的实现来扩展SpringIoC容器。接下来的几节将描述这些集成接口。

#### 1.8.1.使用BeanPostProcessor自定义bean

这个BeanPostProcessor接口定义了回调方法，可以通过实现这些方法来提供自己的实例化逻辑\(或覆盖容器的默认\)、相关性解析逻辑等等。

#### 1.8.2.使用BeanFactoryPostProcessor自定义配置元数据

Spring IoC容器允许BeanFactoryPostProcessor读取配置元数据，并有可能在容器实例化除BeanFactoryPostProcessor实例以外的任何bean之前更改它。

#### 1.8.3.用FactoryBean定制实例化逻辑

FactoryBean接口是可插入Spring IoC容器的实例化逻辑的一点。 如果您有复杂的初始化代码，而不是（可能）冗长的XML，可以用Java更好地表达，则可以创建自己的FactoryBean，在该类中编写复杂的初始化，然后将自定义FactoryBean插入容器。

### 1.9. Annotation-based Container Configuration（基于注释的容器配置）

基于注释的配置提供了XML设置的替代方案，它依赖字节码元数据来连接组件，而不是角括号声明。视情况使用，注释和xml都有其优点和缺点，通常由开发人员来决定哪种策略更适合他们。

#### 1.9.1. @Required

这个@Required注释适用于bean属性setter方法。

#### 1.9.2. Using @Autowired（使用@Autowired）

在SpringFramework4.3中，@Autowired如果目标bean开始只定义一个构造函数，则不再需要对此类构造函数进行注释。但是，如果有几个构造函数可用，至少必须用@Autowired为了指导容器使用哪一个。

#### 1.9.3. Fine-tuning Annotation-based Autowiring with @Primary（基于注解的微调自动装配@Primary）

由于按类型自动排列可能会导致多个候选对象，因此通常需要对选择过程有更多的控制。实现这一目标的一种方法是使用Spring的@Primary注释，@Primary指示当多个bean被自动分配到单值依赖项时，应优先考虑特定bean。如果候选人中恰好存在一个主bean，则它将成为自动设置的值。

#### 1.9.4. Fine-tuning Annotation-based Autowiring with Qualifiers（**带有限定符的微调注解自动装配**）

@Primary是一种有效的方法，在确定一个主要候选对象时，可以通过几个实例使用自动按类型进行自动装配。当您需要对选择过程进行更多的控制时，可以使用Spring的@Qualifier注释可以将限定符值与特定的参数关联起来，缩小类型匹配的集合，以便为每个参数选择特定的bean。

#### **1.9.5.使用泛型作为自动装配限定符**

介绍了如何使用泛型作为自动装配限定符，它是一种隐式限定形式。

**1.9.6.使用CustomAutowireConfigurer**

CustomAutowireConfigurer是BeanFactoryPostProcessor，即使您没有使用Spring的@Qualifier注释来注释自己的自定义限定符注释类型，也可以使用它来注册。

#### 1.9.7.注入@Resource

@Resource接受一个name属性。默认情况下，Spring将该值解释为要注入的bean名。

#### 1.9.8.使用@Value

@Value通常用于注入外部属性

#### 1.9.9.使用@PostConstruct和@PreDestroy

在Spring 2.5中引入的对这些注释的支持提供了初始化回调和销毁回调中描述的生命周期回调机制的替代方法。

### 1.10. Classpath Scanning and Managed Components**（**类路径扫描和托管组件**）**

本章中的大多数示例都使用xml来指定生成每个元数据的配置元数据**。**

#### **1.10.1. @Component和进一步的原型注释**

@Component是任何Spring托管组件的通用原型**。**Spring提供了进一步的原型注释：@Component, @Service，和@Controller**。**

####  **1.10.2.使用元注释和组合注释**

Spring提供的许多注释都可以在您自己的代码中用作元注释。 元注释是可以应用于另一个注释的注释。 例如，前面提到的@Service注释使用@Component进行元注释**。**

#### **1.10.3.自动检测类和注册Bean定义**

Spring可以自动检测构造型类并注册相应的BeanDefinition实例的ApplicationContext**。**

#### **1.10.4.使用过滤器自定义扫描**

默认情况下，用@Component, @Repository, @Service, @Controller, @Configuration，或自定义注释本身用@Component是唯一检测到的候选组件。但是，可以通过应用自定义筛选器来修改和扩展此行为。将它们添加为includeFilters或excludeFilters属性的@ComponentScan注释\(或AS\)或的子元素元素\)。每个筛选器元素都需要type和expression属性。

#### **1.10.5.在组件中定义Bean元数据**

Spring组件还可以将bean定义元数据贡献给容器。 您可以使用与@Configuration注释类中的Bean元数据定义相同的@Bean注释进行此操作。

#### **1.10.6.命名自动检测组件**

在扫描过程中自动检测到组件时，该组件的Bean名称由该扫描程序已知的BeanNameGenerator策略生成。 默认情况下，任何包含名称值的Spring构造型注释（@ Component，@ Repository，@ Service和@Controller）都会将该名称提供给相应的bean定义。

#### **1.10.7.为自动检测的组件提供作用域**

通常，与Spring管理的组件一样，自动检测到的组件的默认范围也是最常见的范围是singleton（单例）。 但是，有时您需要使用@Scope注释指定其他作用域。

#### **1.10.8.为限定符元数据提供注释**

这个@Qualifier注释将在带有限定符的微调注解自动装配。本节中的示例演示了如何使用@Qualifier注释和自定义限定符注释，以便在解析自动选择时提供细粒度控制。

#### **1.10.9.生成候选组件索引**

虽然类路径扫描非常快，但可以通过在编译时创建一个静态候选列表（候选组件索引）来提高大型应用程序的启动性能。在这种模式下，所有作为组件扫描目标的模块都必须使用此机制。

### 1.11.使用JSR 330标准注释

从Spring3.0开始，Spring提供了对JSR-330标准注释\(依赖注入\)的支持。这些注释的扫描方式与Spring注释相同。需要添加相关的jar包。

#### **1.11.1.依赖注入@Inject和@Named**

代替@Autowired，你可以用@javax.inject.Inject。如果要为应该注入的依赖项使用限定名，则应使用@Named注释。

#### **1.11.2. @Named和@ManagedBean\*与@Component注记**

代替@Component，你可以用@javax.inject.Named或javax.annotation.ManagedBean。

#### **1.11.3.JSR-330标准注释的局限性**

介绍了标准注释中哪些重要的特性是不可用的。

### 1.12.基于Java的容器配置

本节介绍如何在Java代码中使用注释配置Spring容器。

#### **1.12.1.基本概念：@Bean和@Configuration**

这个@Bean注释用于指示方法实例化、配置和初始化要由SpringIoC容器管理的新对象。用@Configuration指示其主要用途是作为bean定义的来源。

**1.12.2.使用AnnotationConfigApplicationContext**

以下各节介绍了Spring 3.0中引入的Spring的AnnotationConfigApplicationContext。 这种通用的ApplicationContext实现不仅能够接受@Configuration类作为输入，而且还可以接受普通的@Component类和带有JSR-330元数据注释的类。

#### **1.12.3.使用@Bean注解**

@Bean是方法级注释和xml的直接模拟。此节介绍了使用@Bean注解的详细流程。

**1.12.4使用@Configuration注解**

@Configuration是一个类级注释，指示对象是bean定义的源。此节介绍了如何使用该注释的详细说明。

#### **1.12.5.组合基于Java的配置**

Spring的基于Java的配置功能使您可以撰写注释，从而降低配置的复杂性。

### 1.13.Environment Abstraction（环境抽象）

这个Environment接口是一个集成在容器中的抽象，它为应用程序环境的两个关键方面建模：切面和属性。

#### **1.13.1.bean** Definition Profiles**（定义概要）**

bean定义概要文件在核心容器中提供了一种机制，允许在不同的环境中注册不同的bean。

#### **1.13.2. PropertySource\(属性源\)抽象**

spring的Environment抽象在可配置的属性源层次结构上提供搜索操作。

#### **1.13.3.使用@PropertySource**

@PropertySource注释为将PropertySource添加到Spring的环境中提供了一种方便的声明性机制。

#### 1.13.4. 声明中的占位符解析

以前元素中占位符的值只能根据JVM系统属性或环境变量来解析。现在可以更改搜索系统属性和环境变量的优先级，也可以完全删除它们。 您还可以根据需要将自己的属性源添加到组合中。

### 1.14.注册一个LoadTimeWeaver

Spring使用LoadTimeWeaver在将类加载到Java虚拟机（JVM）中时对其进行动态转换。

### 1.15.ApplicationContext的附加功能

#### 1.15.1.使用MessageSource的国际化

ApplicationContext接口扩展了一个称为MessageSource的接口，因此提供了国际化（“ i18n”）功能。 Spring还提供了HierarchicalMessageSource接口，该接口可以分层解析消息。 这些接口一起提供了Spring影响消息解析的基础。

#### **1.15.2.标准和自定义事件**

\*\*\*\*



\*\*\*\*



\*\*\*\*



