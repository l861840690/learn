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

通过ApplicationEvent类和ApplicationListener接口提供ApplicationContext中的事件处理。此节描述了Spring提供的标准事件和一些自定义事件。

#### **1.15.3.方便地访问低级别资源**

描述了如何更方便地访问低级别资源的方式。

#### 1.15.4.Web应用程序的便捷ApplicationContext实例化

你可以创建ApplicationContext实例，例如，通过使用ContextLoader。当然，您也可以创建ApplicationContext实例以编程方式使用ApplicationContext实现。

#### **1.15.5.部署SpringApplicationContext作为JavaEERAR文件**

可以将Spring ApplicationContext部署为RAR文件，将上下文及其所有必需的Bean类和库JAR封装在Java EE RAR部署单元中。 这等效于引导独立的ApplicationContext（仅托管在Java EE环境中）能够访问Java EE服务器功能。

### 1.16. The BeanFactory**（Bean工厂）**

BeanFactory API为Spring的IoC功能提供了基础。 它的特定合同主要用于与Spring的其他部分以及相关的第三方框架集成，并且其DefaultListableBeanFactory实现是更高级别的GenericApplicationContext容器中的关键委托。

#### **1.16.1. BeanFactory or ApplicationContext?**

本节说明BeanFactory和ApplicationContext容器级别之间的区别以及对引导的影响。

除非有充分的理由，否则应使用ApplicationContext，将GenericApplicationContext及其子类AnnotationConfigApplicationContext作为自定义引导的常见实现。

因为ApplicationContext包含BeanFactory的所有功能，所以通常建议在纯BeanFactory上使用，除非需要对Bean处理的完全控制。

## **2.**Resources（资源）

本章介绍Spring如何处理资源以及如何在Spring中使用资源。

### 2.1. Introduction（导言）

### 2.2. The Resource Interface（资源接口）

Spring的Resource接口旨在成为一种功能更强大的接口，用于抽象化对低级资源的访问。

### 2.3. Built-in Resource Implementations（内置资源实现）

介绍了Spring内包括的Resource实现。

#### 2.3.1. UrlResource

UrlResource包装了java.net.URL，可用于访问通常可以通过URL访问的任何对象，例如文件，HTTP目标，FTP目标等。

#### 2.3.2. ClassPathResource（类路径资源）

此类表示应从类路径获取的资源。 它使用线程上下文类加载器，给定的类加载器或给定的类来加载资源。

#### **2.3.3. FileSystemResource**

这是java.io.File和java.nio.file.Path句柄的Resource实现。 它支持解析为文件和URL。

#### **2.3.4. ServletContextResource**

这是ServletContext资源的Resource实现，用于解释相关Web应用程序根目录中的相对路径。

#### **2.3.5. InputStreamResource**

InputStreamResource是给定InputStream的Resource实现。 仅当没有特定的资源实现适用时才应使用它。 特别是，尽可能选择ByteArrayResource或任何基于文件的Resource实现。

#### **2.3.6. ByteArrayResource**

这是给定字节数组的Resource实现。 它为给定的字节数组创建一个ByteArrayInputStream。

### 2.4. The ResourceLoader（资源加载器）

ResourceLoader接口旨在由可以返回（即加载）Resource实例的对象实现。所有应用程序上下文都实现ResourceLoader接口。 因此，所有应用程序上下文都可用于获取Resource实例。

### 2.5. The ResourceLoaderAware interface

ResourceLoaderAware接口是一个特殊的回调接口，用于标识期望随ResourceLoader参考一起提供的组件。

### 2.6. Resources as Dependencies（资源依赖）

如果Bean本身将通过某种动态过程来确定并提供资源路径，那么对于Bean来说，使用ResourceLoader接口加载资源可能是有意义的。 例如，考虑加载某种模板，其中所需的特定资源取决于用户的角色。

### 2.7. Application Contexts and Resource Paths（应用程序上下文和资源路径）

本节介绍如何使用资源创建应用程序上下文，包括使用XML的快捷方式、如何使用通配符和其他详细信息。

#### 2.7.1. Constructing Application Contexts（构造应用程序上下文）

应用程序上下文构造函数（针对特定的应用程序上下文类型）通常采用字符串或字符串数组作为资源的位置路径，例如构成上下文定义的XML文件。

#### **2.7.2. Wildcards in Application Context Constructor Resource Paths（**应用程序上下文构造函数资源路径中的通配符**）**

应用程序上下文构造函数值中的资源路径可以是简单路径（如先前所示），每个路径都具有到目标资源的一对一映射，或者可以包含特殊的“ classpath \*：”前缀或内部Ant。 样式的正则表达式（通过使用Spring的PathMatcher实用程序进行匹配）。 后者都是有效的通配符。此节介绍了如何去使用通配符。

#### **2.7.3. FileSystemResource Caveats（警告）**

未附加到FileSystemApplicationContext的FileSystemResource（即，当FileSystemApplicationContext不是实际的ResourceLoader时）将按您期望的那样处理绝对路径和相对路径。 相对路径是相对于当前工作目录的，而绝对路径是相对于文件系统的根的。

## **3.**Validation, Data Binding, and Type Conversion（验证、数据绑定和类型转换）

### 3.1. Validation by Using Spring’s Validator Interface（使用Spring的Validator接口进行验证）

Spring具有Validator接口，可用于验证对象。 Validator接口通过使用Errors对象工作，以便在验证时，验证器可以将验证失败报告给Errors对象。

### 3.2. Resolving Codes to Error Messages（将代码解析为错误消息）

本节介绍与验证错误相对应的输出消息。

### 3.3. Bean Manipulation and the BeanWrapper（Bean操作和BeanWrapper）

这个org.springframework.beans包遵循JavaBeans标准。bean包中一个非常重要的类是BeanWrapper接口及其相应的实现\(BeanWrapperImpl\)。

#### **3.3.1.设置和获取基本属性和嵌套属性**

设置和获取属性是通过使用setPropertyValue, setPropertyValues, getPropertyValue，和getPropertyValues方法，这些方法带有几个重载变体。Spring javadoc更详细地描述了它们。

#### 3.3.2.内置的PropertyEditor实现

Spring使用的概念是PropertyEditor之间的转换。Object和一个String。可以方便地以不同于对象本身的方式表示属性。

### 3.4. Spring Type Conversion**（spring类型转换）**

Spring 3引入了core.convert包，该包提供了通用的类型转换系统。 该系统定义了一个用于实现类型转换逻辑的SPI和一个用于在运行时执行类型转换的API。 在Spring容器中，可以使用此系统作为PropertyEditor实现的替代方法，以将外部化的bean属性值字符串转换为所需的属性类型。 您还可以在应用程序中需要类型转换的任何地方使用公共API。

#### **3.4.1. Converter SPI（**转换器SPI**）**

用于实现类型转换逻辑的SPI非常简单且类型严格。要创建自己的转换器，请实现Converter接口，并将S设置为要转换的类型，并将T设置为要转换的类型。

#### 3.4.2. Using ConverterFactory（使用ConverterFactory）

当需要集中整个类层次结构的转换逻辑时（例如，从String转换为Enum对象时），可以实现ConverterFactory。

#### 3.4.3. Using GenericConverter（使用GenericConverter）

当您需要复杂的Converter实现时，请考虑使用GenericConverter接口。 与Converter相比，GenericConverter具有比Converter更灵活但类型不太强的签名，支持在多种源类型和目标类型之间进行转换。

**3.4.4. The ConversionService API**

ConversionService定义了一个统一的API，用于在运行时执行类型转换逻辑。

####  **3.4.5. Configuring a ConversionService（**配置ConversionService**）**

ConversionService是无状态对象，旨在在应用程序启动时实例化，然后在多个线程之间共享。

####  **3.4.6. Using a ConversionService Programmatically**（以编程方式使用ConversionService）

要以编程方式使用ConversionService实例，可以像对待其他任何bean一样注入对该实例的引用。

### 3.5. Spring Field Formatting（Spring字段格式）

通常，当您需要实现通用类型转换逻辑时（例如，用于在java.util.Date和Long之间进行转换），可以使用Converter SPI。 在客户端环境（例如Web应用程序）中工作并且需要解析和打印本地化的字段值时，可以使用Formatter SPI。 ConversionService为两个SPI提供统一的类型转换API。

#### 3.5.1. The Formatter SPI（格式化器SPI）

用于实现字段格式化逻辑的Formatter SPI非常简单且类型严格。此小节给出了显示了Formatter接口定义的详细示例。

#### **3.5.2. Annotation-driven Formatting（**注释驱动的格式**）**

可以通过字段类型或注释配置字段格式。 要将注释绑定到Formatter，需要实现AnnotationFormatterFactory。

#### **3.5.3. The FormatterRegistry SPI**

FormatterRegistry是用于注册格式器和转换器的SPI。

#### **3.5.4. The FormatterRegistrar SPI**

FormatterRegistrar是一个SPI，用于通过FormatterRegistry注册格式器和转换器。

#### **3.5.5. Configuring Formatting in Spring MVC（**在Spring MVC中配置格式**）**

参见Spring MVC一章中的转换和格式化

### 3.6. Configuring a Global Date and Time Format**（**配置全局日期和时间格式**）**

默认情况下，未使用@DateTimeFormat注释的日期和时间字段是使用DateFormat.SHORT样式从字符串转换的。如果愿意，可以通过定义自己的全局格式来更改此设置。

### 3.7. Spring Validation（Spring验证）

Spring 3对其验证支持进行了一些增强。 首先，完全支持JSR-303 Bean验证API。 其次，以编程方式使用时，Spring的DataBinder可以验证对象并绑定到对象。 第三，Spring MVC支持声明式验证@Controller输入。

#### **3.7.1. Overview of the JSR-303 Bean Validation API（**JSR-303 Bean验证API概述**）**

JSR-303标准化了Java平台的验证约束声明和元数据。 通过使用此API，您可以使用声明性验证约束来注释域模型属性，并且运行时会强制执行它们。

#### **3.7.2. Configuring a Bean Validation Provider（**配置Bean验证提供程序**）**

Spring提供了对Bean验证API的全面支持。 这包括对将JSR-303或JSR-349 Bean验证提供程序引导为Spring Bean的便捷支持。这样，您可以在应用程序中需要验证的任何地方注入javax.validation.ValidatorFactory或javax.validation.Validator。

#### **3.7.3. Configuring a DataBinder（**配置一个DataBinder**）**

从Spring 3开始，您可以使用Validator配置DataBinder实例。配置完成后，您可以通过调用binder.validate（）来调用Validator。任何验证错误都会自动添加到活页夹的BindingResult中。

#### **3.7.4. Spring MVC 3 Validation（**Spring MVC 3验证**）**

参见Spring MVC一章中的验证。

## 4. Spring Expression Language \(SpEL**，Spring表达式语言**\)

Spring表达式语言（简称“ SpEL”）是一种功能强大的表达式语言，支持在运行时查询和操作对象图。 语言语法类似于Unified EL，但是提供了其他功能，最著名的是方法调用和基本的字符串模板功能。

### 4.1. Evaluation（评估）

本节介绍SpEL接口及其表达语言的简单用法。 完整的语言参考可以在“语言参考”中找到。

#### **4.1.1. Understanding EvaluationContext（了解评估上下文）**

在评估表达式以解析属性，方法或字段并帮助执行类型转换时，使用EvaluationContext接口。 本节介绍了Spring提供的两种实现。

#### **4.1.2. Parser Configuration（**解析器配置**）**

可以通过使用解析器配置对象（org.springframework.expression.spel.SpelParserConfiguration）配置SpEL表达式解析器。 

#### **4.1.3. SpEL Compilation（**SpEL编译**）**

Spring Framework 4.1包含一个基本的表达式编译器。通常对表达式进行解释，这在评估过程中提供了很大的动态灵活性，但没有提供最佳性能。

### 4.2. Expressions in Bean Definitions**（**Bean定义中的表达式**）**

您可以将SpEL表达式与基于XML或基于注释的配置元数据一起使用，以定义BeanDefinition实例。 在这两种情况下，用于定义表达式的语法都采用＃{&lt;表达式字符串&gt;}的形式。

#### **4.2.1. XML Configuration（**XML配置**）**

可以使用表达式来设置属性或构造函数参数值，此小节给出了详细的示例。

**4.2.2. Annotation Configuration（注释配置）**

若要指定默认值，可以将@Value批注放置在字段，方法以及方法或构造函数参数上。

### 4.3. Language Reference**（**语言参考**）**

本节描述了Spring Expression Language的工作方式。

#### **4.3.1. Literal Expressions（文字表达）**

支持的文字表达式的类型为字符串，数值（int，实数，十六进制），布尔值和null。 字符串由单引号引起来。 要将单引号本身放在字符串中，请使用两个单引号字符。

#### **4.3.2. Properties, Arrays, Lists, Maps, and Indexers（**属性，数组，列表，映射和索引器**）**

此小节介绍了它们的用法。

#### **4.3.3. Inline Lists（**内联列表**）**

您可以使用{}符号在表达式中直接表达列表。

#### **4.3.4. Inline Maps（**内联映射**）**

也可以使用{key:value}符号直接在表达式中表示映射。

**4.3.5. Array Construction（队列结构）**

您可以使用熟悉的Java语法构建数组，还可以选择提供一个初始值设定项，以便在构建时填充数组。

**4.3.6. Methods（方法）**

您可以使用典型的Java编程语法来调用方法。还可以对文本调用方法。也支持变量参数。

**4.3.7. Operators（运算符）**

本小节描述了Spring表达式语言支持的几种运算符。

#### **4.3.8. Types（**种类**）**

您可以使用特殊的T运算符来指定java.lang.Class（类型）的实例。

**4.3.9. Constructors（构造器）**

您可以使用new运算符来调用构造方法。

**4.3.10. Variables（变量）**

可以使用variableName语法引用表达式中的变量。变量是通过对EvaluationContext实现使用setVariable方法设置的**。**

**4.3.11. Functions（功能）**

通过注册可在表达式字符串中调用的用户定义函数，可以扩展SpEL。函数是通过EvaluationContext注册的。

#### **4.3.12. Bean References（**Bean引用**）**

如果已使用bean解析器配置求值上下文，则可以使用@符号从表达式中查找bean**。**

**4.3.13. Ternary Operator \(If-Then-Else，三元运算符\)**

可以使用三元运算符在表达式中执行if-then-else条件逻辑。

**4.3.14. The Elvis Operator（Elvis操作符）**

Elvis运算符是三元运算符语法的一种简化，在Groovy语言中使用。

**4.3.15. Safe Navigation Operator（Safe Navigation运算符）**

safe navigation操作符用于避免NullPointerException，它来自Groovy语言。

**4.3.16. Collection Selection（集合选择）**

Selection是一种强大的表达语言功能，可让您通过从源集合中进行选择来将其转换为另一个集合。

**4.3.17. Collection Projection（集合投影）**

投影允许集合驱动子表达式的求值，结果是一个新集合。投影的语法是。！\[投影表达式\]。

**4.3.18. Expression templating（表达式模板化）**

表达式模板允许将文字文本与一个或多个评估块混合。 每个评估块都由您可以定义的前缀和后缀字符定界。

### 4.4. Classes Used in the Examples**（**示例中使用的类**）**

本节列出了本章示例中使用的类。

## 5. Aspect Oriented Programming with Spring（Spring面向切面编程）

面向切面编程（AOP）通过提供另一种思考程序结构的方式，补充了面向对象编程（OOP）。在OOP中，模块化的关键单元是类，而在AOP中，模块化的单元是方面。方面支持跨多个类型和对象的关注点（如事务管理）的模块化。

### 5.1. AOP Concepts（AOP概念）

让我们首先定义一些核心AOP概念和术语。这些术语不是Spring特有的。不幸的是，AOP术语并不是特别直观。然而，如果Spring使用自己的术语，则会更加混乱。

### 5.2. Spring AOP Capabilities and Goals（Spring AOP的能力和目标）

Spring AOP是用纯Java实现的。不需要特殊的编译过程。Spring AOP不需要控制类装入器层次结构，因此适合在servlet容器或应用程序服务器中使用。

### 5.3. AOP Proxies（AOP代理）

Spring AOP默认将标准JDK动态代理用于AOP代理。 这使得可以代理任何接口（或一组接口）。

### 5.4. @AspectJ support（@AspectJ 支持）

@AspectJ指的是一种将方面声明为带有注释的常规Java类的样式。

#### **5.4.1. Enabling @AspectJ Support（**启用@AspectJ支持**）**

要在Spring配置中使用@AspectJ方面，您需要启用Spring支持，以便基于@AspectJ方面配置Spring AOP，并根据这些方面是否建议使用自动代理bean。

**5.4.2. Declaring an Aspect（声明一个切面）**

启用@AspectJ支持后，Spring会自动检测应用程序上下文中定义的具有@AspectJ方面（具有@aspect注释）的类的任何bean，并将其用于配置Spring AOP。

**5.4.3. Declaring a Pointcut（声明切入点）**

切入点确定了关注的连接点，从而使我们能够控制执行建议的时间。 Spring AOP仅支持Spring Bean的方法执行连接点，因此您可以将切入点视为与Spring Bean上的方法执行匹配。

**5.4.4. Declaring Advice（声明通知）**

通知与切入点表达式关联，并在与切入点匹配的方法执行之前、之后或周围运行。切入点表达式可以是对命名切入点的简单引用，也可以是就地声明的切入点表达式。

**5.4.5. Introductions（简介）**

简介（在AspectJ中称为类型间声明）使切面可以声明通知对象实现给定的接口，并代表那些对象提供该接口的实现。

#### **5.4.6. Aspect Instantiation Models（切面实例化模型）**

默认情况下，应用程序上下文中每个方面都有一个实例。AspectJ称之为单例实例化模型。可以用交替的生命周期定义方面。

#### **5.4.7. An AOP Example（**AOP示例**）**

练习前几节的AOP工作原理，此节把它们组合起来做了一个AOP示例。

### 5.5. Schema-based AOP Support（基于模式的AOP支持）

如果您喜欢基于XML的格式，Spring还支持使用新的aop名称空间标记定义方面。支持与使用@AspectJ样式时完全相同的切入点表达式和建议类型。因此，在本节中，我们将重点放在新语法上，并使读者参考上一节中的讨论（@AspectJ支持），以了解编写切入点表达式和建议参数的绑定。

#### **5.5.1. Declaring an Aspect**（声明一个切面）

使用模式支持时，方面是在Spring应用程序上下文中定义为bean的常规Java对象。状态和行为在对象的字段和方法中捕获，切入点和建议信息在XML中捕获。

**5.5.2. Declaring a Pointcut（声明切入点）**

您可以在元素中声明一个命名的切入点，让切入点定义在多个方面和顾问之间共享。

**5.5.3. Declaring Advice（声明通知）**

基于模式的AOP支持使用与@AspectJ样式相同的五种通知，并且它们具有完全相同的语义。

**5.5.4. Introductions（简介）**

简介（在AspectJ中称为类型间声明）允许方面声明建议的对象实现给定的接口，并代表这些对象提供该接口的实现。

**5.5.5. Aspect Instantiation Models（切面实例化模型）**

模式定义方面唯一支持的实例化模型是singleton模型。其他实例化模型可能在将来的版本中得到支持。

**5.5.6. Advisors（顾问）**

“advisors”的概念来自于Spring中定义的AOP支持，在AspectJ中没有直接的等价物。顾问就像一个独立的小方面，只有一条建议。通知本身由bean表示，并且必须实现在Spring的通知类型中描述的其中一个通知接口。顾问可以利用AspectJ切入点表达式。

**5.5.7. An AOP Schema Example（AOP模式示例）**

本节展示了使用模式支持重写AOP示例时并发锁定失败重试示例的外观。

### 5.6. Choosing which AOP Declaration Style to Use**（**选择要使用的AOP声明样式**）**

一旦确定切面是实现给定需求的最佳方法，您如何在使用Spring AOP或AspectJ以及在Aspect语言（代码）样式，@ AspectJ批注样式或Spring XML样式之间做出选择？ 这些决定受许多因素影响，包括应用程序需求，开发工具和团队对AOP的熟悉程度。

#### 5.6.1. Spring AOP or Full AspectJ?（Spring AOP还是Full AspectJ？）

用最简单的方法。Spring AOP比使用完整的AspectJ更简单，因为不需要在开发和构建过程中引入AspectJ编译器/编织器。

#### 5.6.2. @AspectJ or XML for Spring AOP?（@AspectJ还是Spring AOP的XML？）

如果您选择使用Spring AOP，那么可以选择@AspectJ或XML样式。XML样式可能是现有Spring用户最熟悉的，并且它是由真正的POJOs支持的。

### 5.7. Mixing Aspect Types（混合切面类型）

完全可以通过使用自动代理支持、模式定义的AOP:Aspect&gt;方面、“AOP：Advor”声明的顾问，甚至在同一配置中其他样式的代理和拦截器来混合@ AspectJ风格方面。

### 5.8. Proxying Mechanisms（代理机制）

Spring AOP使用JDK动态代理或CGLIB来为给定的目标对象创建代理。JDK动态代理被内置到JDK中，而CGLIB是一个常见的开源类定义库（重新打包成Spring Core）。

#### **5.8.1. Understanding AOP Proxies（**了解AOP代理**）**

Spring AOP是基于代理的。在编写自己的方面或使用Spring框架提供的任何基于Spring AOP的方面之前，掌握最后一条语句的实际含义是非常重要的。

### 5.9. Programmatic Creation of @AspectJ Proxies**（**@AspectJ代理程序的创建**）**

除了使用“&lt;AOP:CONFIG&gt;或&lt;AOP:AspectJ AutoPosixServer”来声明配置中的方面之外，还可以以编程方式创建建议目标对象的代理。

### 5.10. Using AspectJ with Spring Applications（在Spring应用程序中使用AspectJ）

在本节中，我们将介绍如何使用AspectJ编译器或weaver，如果您的需求超出了Spring AOP所提供的功能范围，则可以代替springaop或除了springaop之外使用它。

####  **5.10.1. Using AspectJ to Dependency Inject Domain Objects with Spring（**使用AspectJ通过Spring依赖注入域对象**）**

Spring容器实例化并配置在您的应用程序上下文中定义的bean。 给定包含要应用的配置的Bean定义的名称，也可以要求Bean工厂配置预先存在的对象。

####  **5.10.2. Other Spring aspects for AspectJ（**AspectJ的其他Spring方面**）**

除了@Configurable方面之外，spring-aspects.jar还包含一个AspectJ方面，您可以使用该方面来驱动Spring的事务管理，以使用@Transactional批注来批注类型和方法。

#### **5.10.3. Configuring AspectJ Aspects by Using Spring IoC（**使用Spring IoC配置AspectJ Aspects**）**

AspectJ运行时本身负责切面的创建，通过Spring配置AspectJ创建的切面的方法取决于切面使用的AspectJ实例化模型（per-xxx子句）。

#### **5.10.4. Load-time Weaving with AspectJ in the Spring Framework（**在Spring Framework中使用AspectJ进行加载时编织**）**

加载时编织（LTW）是指当AspectJ方面被加载到Java虚拟机（JVM）中时，将其编织到应用程序的类文件中的过程。

### 5.11. Further Resources**（**更多信息**）**

有关AspectJ的更多信息，需要访问AspectJ网站。

## 6. Spring AOP APIs

在本章中，我们将讨论较低级别的Spring AOP api。对于常见的应用程序，我们建议将Spring AOP与AspectJ切入点结合使用。

### 6.1. Pointcut API in Spring（Spring中的切入点API）

本节描述Spring如何处理关键的切入点概念。

**6.1.1. Concepts（概念）**

Spring的切入点模型使切入点重用不受建议类型的影响。 您可以使用相同的切入点来定位不同的通知。

#### **6.1.2. Operations on Pointcuts（**切入点的操作**）**

Spring支持切入点上的操作（特别是联合和相交）。联合表示两个切入点都匹配的方法。 相交是指两个切入点都匹配的方法。您可以通过使用org.springframework.aop.support.Pointcuts类中的静态方法或使用同一包中的ComposablePointcut类来编写切入点。 但是，使用AspectJ切入点表达式通常是一种更简单的方法。

#### **6.1.3. AspectJ Expression Pointcuts（**AspectJ表达切入点**）**

从2.0开始，Spring使用的最重要的切入点类型是org.springframework.aop.aspectj.AspectJExpressionPointcut。 这是一个切入点，该切入点使用AspectJ提供的库来解析AspectJ切入点表达式字符串。有关支持的AspectJ切入点原语的讨论，请参见上一章。

#### **6.1.4. Convenience Pointcut Implementations（**便捷切入点实现**）**

Spring提供了几种方便的切入点实现。 您可以直接使用其中一些。 其他的则应归入特定于应用程序的切入点中。

#### **6.1.5. Pointcut Superclasses（**切入点超类**）**

Spring提供了有用的切入点超类，以帮助您实现自己的切入点。

#### **6.1.6. Custom Pointcuts（**自定义切入点**）**

由于Spring AOP中的切入点是Java类，而不是语言功能（如AspectJ），因此可以声明自定义切入点，无论是静态还是动态。Spring中的自定义切入点可以任意复杂。 但是，如果可以的话，我们建议使用AspectJ切入点表达语言。

### 6.2. Advice API in Spring**（Spring通知API）**

现在，我们可以检查Spring AOP如何处理通知。

#### **6.2.1. Advice Lifecycles（通知**生命周期**）**

每个通知都是一个Spring bean。 通知实例可以在所有通知对象之间共享，或者对于每个通知对象都是唯一的。 这对应于每个班级或每个实例的通知。

**6.2.2. Advice Types in Spring（Spring通知类型）**

Spring提供了几种通知类型，并且可以扩展以支持任意通知类型。 本节介绍基本概念和标准通知类型。

### 6.3. The Advisor API in Spring（Spring的顾问 API）

在Spring中，顾问程序是一个切面，仅包含与切入点表达式关联的单个通知对象。

### 6.4. Using the ProxyFactoryBean to Create AOP Proxies（使用ProxyFactoryBean创建AOP代理）

如果您将Spring IoC容器（ApplicationContext或BeanFactory）用于您的业务对象（应该是！），则要使用Spring的AOP FactoryBean实现之一。 （请记住，工厂bean引入了一个间接层，使它可以创建其他类型的对象。）

**6.4.1. Basics（基础）**

像其他Spring FactoryBean实现一样，ProxyFactoryBean引入了一个间接级别。如果定义一个名为foo的ProxyFactoryBean，则引用foo的对象将看不到ProxyFactoryBean实例本身，而是看到由ProxyFactoryBean中的getObject（）方法的实现创建的对象。

**6.4.2. JavaBean Properties（JavaBean属性）**

与Spring随附的大多数FactoryBean实现一样，ProxyFactoryBean类本身就是JavaBean。

#### **6.4.3. JDK- and CGLIB-based proxies（**基于JDK和CGLIB的代理**）**

本部分是有关ProxyFactoryBean如何选择为特定目标对象（将被代理）创建基于JDK的代理或基于CGLIB的代理的权威性文档。

**6.4.4. Proxying Interfaces（代理接口）**

此小节演示了一个简单的ProxyFactoryBean操作示例。

**6.4.5. Proxying Classes（代理类）**

想象一下，在我们之前的示例中，没有Person接口。我们需要通知一个名为Person的类，该类没有实现任何业务接口。在这种情况下，您可以将Spring配置为使用CGLIB代理而不是动态代理。

#### 6.4.6. Using “Global” Advisors（使用“全球”顾问）

通过在拦截器名称后附加一个星号，所有具有与该星号之前的部分匹配的Bean名称的顾问程序都将添加到顾问程序链中。

### 6.5. Concise Proxy Definitions（简洁的代理定义）

使用父子bean定义和子bean定义以及内部bean定义可以使代理定义更加简洁明了。

### 6.6. Creating AOP Proxies Programmatically with the ProxyFactory（使用ProxyFactory以编程方式创建AOP代理）

使用Spring以编程方式创建AOP代理很容易。 这使您可以使用Spring AOP，而无需依赖Spring IoC。

### 6.7. Manipulating Advised Objects（操作通知对象）

创建AOP代理时，可以使用Or.SrpFrrasWork.Aop.FrasWork.Debug接口来操作AOP代理。任何AOP代理都可以强制转换到此接口，不管它实现的是哪个接口。

### 6.8. Using the "auto-proxy" facility（使用“自动代理”功能）

Spring允许我们使用“自动代理” Bean定义，该定义可以自动代理选定的Bean定义。 它基于Spring的“ bean后处理器”基础架构，可在容器加载时修改任何bean定义。

#### **6.8.1. Auto-proxy Bean Definitions（**自动代理Bean定义**）**

本节介绍了org.springframework.aop.framework.autoproxy包提供的自动代理创建者。

### 6.9. Using TargetSource Implementations**（**使用TargetSource实现**）**

Spring提供了TargetSource的概念，以org.springframework.aop.TargetSource接口表示。 该接口负责返回实现连接点的“目标对象”。 每当AOP代理处理方法调用时，都会向TargetSource实现请求目标实例。

#### **6.9.1. Hot-swappable Target Sources（**可热交换的目标源**）**

org.springframework.aop.target.HotSwappableTargetSource的存在是为了允许AOP代理的目标切换，同时允许调用者保留对其的引用。

  
**6.9.2. Pooling Target Sources（池化目标源）**

使用池目标源提供了与无状态会话EJB相似的编程模型，在无状态会话EJB中，维护了相同实例的池，并且方法调用将释放池中的对象。

#### **6.9.3. Prototype Target Sources（**原型目标源**）**

设置“原型”目标源类似于设置池化TargetSource。 在这种情况下，每次方法调用都会创建目标的新实例。

#### **6.9.4. ThreadLocal Target Sources（**ThreadLocal目标源**）**

如果需要为每个传入请求（即每个线程）创建对象，则ThreadLocal目标源非常有用。ThreadLocal的概念提供了一个JDK范围的工具，可以透明地将资源存储在线程旁边。

### 6.10. Defining New Advice Types**（**定义新的通知类型**）**

Spring AOP被设计为可扩展的。 尽管目前在内部使用拦截实现策略，但是除了在通知周围，在通知之前，抛出通知和返回通知之后进行拦截之外，还可以支持任意通知类型。

## 7.Null-safety（空安全）

尽管Java不允许用它的类型系统来表示空安全性，但是Spring框架现在在org.Spring Framework.lang包中提供了一些本节种介绍的注释，允许您声明API和字段的空性。

### 7.1. Use cases（用例）

除了为Spring Framework API可空性提供显式声明外，IDE（例如IDEA或Eclipse）还可以使用这些批注提供与空安全有关的有用警告，以避免在运行时出现NullPointerException。

### 7.2. JSR-305 meta-annotations（JSR-305元注释）

Spring注释使用JSR 305注释（休眠但广泛使用的JSR）进行元注释。JSR-305元注释使工具供应商（如IDEA或Kotlin）以通用方式提供了空安全支持，而无需对Spring注释进行硬编码支持。

## 8. Data Buffers and Codecs（数据缓冲区和编解码器）

Java NIO提供了ByteBuffer，但是许多库在顶部构建了自己的字节缓冲区API，特别是对于网络操作，其中重用缓冲区和/或使用直接缓冲区对性能有利。

### 8.1. DataBufferFactory（数据缓冲区工厂）

DataBufferFactory用于通过两种本节介绍的方式之一创建数据缓冲区。

### 8.2. DataBuffer（数据缓冲区）

DataBuffer接口提供了与java.nio.ByteBuffer类似的操作，但也带来了一些额外的好处，其中一些好处是受到Netty ByteBuf的启发。本节介绍了这些好处的详细信息。

### 8.3. PooledDataBuffer（池数据缓冲区）

正如Javadoc for ByteBuffer中所解释的，字节缓冲区可以是直接的，也可以是非直接的。直接缓冲区可以位于Java堆之外，这样就无需复制本机I/O操作。这使得直接缓冲区对于通过套接字接收和发送数据特别有用，但是它们的创建和发布成本也更高，这就产生了缓冲区池的想法。

### 8.4. DataBufferUtils（数据库缓冲）

本节介绍了DataBufferUtils提供的许多在数据缓冲区上操作的实用方法。

### 8.5. Codecs（编解码器）

org.springframework.core.codec包提供以下策略接口：

Encoder（编码器），用于将Publisher 编码为数据缓冲区流。

Decoder（解码器），用于将Publisher 解码为更高级别的对象流。

### 8.6. Using DataBuffer（使用DataBuffer）

使用数据缓冲区时，必须特别小心以确保释放缓冲区，因为它们可能会被合并。本节介绍了编解码器必须在内部执行哪些操作来管理数据缓冲区。

## 9. Appendix（附录）

### 9.1. XML Schemas（XML架构）

附录的此部分列出了与核心容器相关的XML模式。

#### 9.1.1. The util Schema（**util**架构）

顾名思义，util标签处理常见的实用程序配置问题，例如配置集合，引用常量等。要在util模式中使用标签，您需要在Spring XML配置文件的顶部具有本节中示例的序言（代码段中的文本引用了正确的模式，以便您可以使用util名称空间中的标签）。

#### **9.1.2. The aop Schema（aop**架构**）**

aop标签用于配置Spring中的所有AOP，包括Spring自己的基于代理的AOP框架以及Spring与AspectJ AOP框架的集成。 这些标签在标题为“面向方面的Spring编程”的章节中全面介绍。

#### **9.1.3. The context Schema（上下文**架构**）**

上下文标记处理与管道相关的ApplicationContext配置-即通常不是对最终用户重要的bean，而是在Spring中完成大量“艰巨”工作的bean，例如BeanfactoryPostProcessors。本节给出了引用了正确的架构的示例代码段，以便您可以使用上下文名称空间中的元素。

#### 9.1.4. The Beans Schema（Bean架构）

最后但并非最不重要的一点是，我们在bean模式中具有元素。 自框架刚诞生以来，这些元素就一直出现在Spring。 本节未显示Bean模式中各种元素的示例，因为它们在依赖关系和配置中非常全面地涵盖了它们（实际上，在整章中也是如此）。

### 9.2. XML Schema Authoring（XML架构创作）

从2.0版开始，Spring提供了一种机制，该机制可将基于架构的扩展添加到基本Spring XML格式中，以定义和配置bean。 本节介绍如何编写自己的自定义XML Bean定义解析器，以及如何将此类解析器集成到Spring IoC容器中。

#### 9.2.1. Authoring the Schema（编写架构）

创建一个XML配置扩展以用于Spring的IoC容器首先要编写一个XML模式来描述扩展。本小节示例了如何配置SimpleDateFormat对象。

**9.2.2. Coding a NamespaceHandler（编写命名空间处理程序）**

除了模式之外，我们还需要一个NamespaceHandler来解析Spring在解析配置文件时遇到的这个特定名称空间的所有元素。

  
**9.2.3. Using BeanDefinitionParser（使用BeanDefinitionParser）**

如果NamespaceHandler遇到已映射到特定bean定义解析器的类型的XML元素（本例中为dateformat），则使用bean definition parser。换句话说，BeanDefinitionParser负责解析模式中定义的一个不同的顶级XML元素。

**9.2.4. Registering the Handler and the Schema（注册处理程序和架构）**

编码完成。剩下要做的就是让Spring XML解析基础设施了解我们的自定义元素。我们通过在两个特殊用途的属性文件中注册自定义名称空间处理程序和自定义XSD文件来实现这一点。

#### **9.2.5. Using a Custom Extension in Your Spring XML Configuration（**在Spring XML配置中使用自定义扩展**）**

使用您自己实现的自定义扩展与使用Spring提供的“自定义”扩展没有什么不同。本小节示例使用在Spring XML配置文件中的前面步骤中开发的自定义&lt;dateformat/&gt;元素。

#### **9.2.6. More Detailed Examples（更详细的例子）**

本节介绍一些更详细的自定义XML扩展示例**。了**

\*\*\*\*





\*\*\*\*

