---
description: Spring boot 2.24 如何使用Spring boot
---

# Spring Boot

## 1. Build Systems（构建系统）

强烈建议您选择一个支持依赖关系管理并且可以使用发布到“ Maven Central”存储库的工件的构建系统。

### 1.1. Dependency Management（依赖管理）

每个Spring Boot版本都提供了它所支持的依赖关系的精选列表。 实际上，您不需要为构建配置中的所有这些依赖项提供版本，因为Spring Boot会为您管理该版本。 当您升级Spring Boot本身时，这些依赖项也会以一致的方式升级。

### 1.2. Maven

Maven用户可以从spring-boot-starter-parent项目继承，以获得合理的默认值。此节介绍了父项目提供的功能。

#### **1.2.1. Inheriting the Starter Parent（**继承入门级父级**）**

此小节介绍了要将项目配置为从spring-boot-starter-parent继承，如何去设置父项。

#### **1.2.2. Using Spring Boot without the Parent POM（**在没有父POM的情况下使用Spring Boot**）**

介绍了如果不想使用spring boot starter父项，如何通过使用scope=import dependency来保留依赖项管理（而不是插件管理）的好处。

#### **1.2.3. Using the Spring Boot Maven Plugin（**使用Spring Boot Maven插件**）**

Spring Boot包含一个Maven插件，它可以将项目打包为一个可执行jar。此小节说明了如何去使用这个插件。

### 1.3. Gradle（摇篮）

要了解如何在Gradle中使用Spring Boot，请参阅Spring Boot Gradle插件的文档。

### 1.4. Ant（蚂蚁）

可以使用Apache Ant + Ivy构建Spring Boot项目。 spring-boot-antlib“ AntLib”模块也可用于帮助Ant创建可执行jar。要声明依赖关系，典型的ivy.xml文件看起来类似于本节给出的示例。

### 1.5. Starters（入门程序）

Starters是一组方便的依赖关系描述符，可以包含在应用程序中。您可以一站式地获得所需的所有Spring和相关技术，而无需搜索示例代码和复制粘贴的依赖描述符。

## 2. Structuring Your Code（构建代码）

Spring Boot不需要任何特定的代码布局就可以工作。然而，有一些最佳实践是有帮助的。

### 2.1. Using the “default” Package（使用“默认”包）

当类不包含程序包声明时，将其视为在“默认程序包”中。 通常不建议使用“默认程序包”，应避免使用。

### 2.2. Locating the Main Application Class（找到主要的应用程序类别）

我们通常建议您将主应用程序类放在其他类之上的根包中。 @SpringBootApplication批注通常放在您的主类上，它隐式定义某些项目的基本“搜索包”。

##  3. Configuration Classes（配置类）

Spring Boot支持基于Java的配置。 尽管可以将SpringApplication与XML源一起使用，但是我们通常建议您的主要源为单个@Configuration类。 通常，定义main方法的类是首选的@Configuration。

### 3.1. Importing Additional Configuration Classes（导入其他配置类）

您不必将所有的@Configuration放在一个类中。@Import注释可用于导入其他配置类。或者，您可以使用@components can自动获取所有Spring组件，包括@Configuration类。

### 3.2. Importing XML Configuration（导入XML配置）

如果您绝对必须使用基于XML的配置，我们建议您仍然从@configuration类开始。然后可以使用@importersource注释加载XML配置文件。

## 4. Auto-configuration（自动配置）

Spring Boot自动配置尝试根据您添加的jar依赖项自动配置Spring应用程序。例如，如果HSQLDB在您的类路径上，并且您没有手动配置任何数据库连接bean，那么Spring Boot将自动配置内存中的数据库。

### 4.1. Gradually Replacing Auto-configuration（逐渐取代自动配置）

自动配置是非侵入性的。在任何时候，您都可以开始定义自己的配置来替换自动配置的特定部分。例如，如果您添加了自己的数据源bean，那么默认的嵌入式数据库支持就会消失。

### 4.2. Disabling Specific Auto-configuration Classes（禁用特定的自动配置类）

如果发现正在应用不需要的特定自动配置类，则可以使用@EnableAutoConfiguration的exclude属性禁用它们。

## 5. Spring Beans and Dependency Injection（SpringBeans和依赖注入）

您可以自由使用任何标准的Spring框架技术来定义bean及其注入的依赖项。为了简单起见，我们经常发现使用@ComponentScan（来查找bean）和使用@Autowired（来进行构造函数注入）可以很好地工作。

## 6. Using the @SpringBootApplication Annotation（使用@springbootsapplication注释）

许多Spring Boot开发人员喜欢他们的应用程序使用自动配置、组件扫描，并且能够在他们的“应用程序类”上定义额外的配置。本节介绍了如何启用这些功能的注释。

## 7. Running Your Application（运行应用程序）

将应用程序打包为jar并使用嵌入式HTTP服务器的最大优点之一是，可以像运行其他应用程序一样运行应用程序。调试Spring Boot应用程序也很容易。您不需要任何特殊的IDE插件或扩展。

### 7.1. Running from an IDE（从IDE运行）

您可以从IDE运行一个Spring Boot应用程序作为一个简单的Java应用程序。但是，首先需要导入项目。导入步骤因IDE和生成系统而异。大多数ide都可以直接导入Maven项目。

### 7.2. Running as a Packaged Application（作为打包的应用程序运行）

如果使用Spring Boot Maven或Gradle插件创建可执行jar，则可以使用java-jar运行应用程序。

### 7.3. Using the Maven Plugin（使用Maven插件）

Spring Boot Maven插件包含一个运行目标，可用于快速编译和运行应用程序。应用程序以分解的形式运行，就像它们在IDE中一样。

### 7.4. Using the Gradle Plugin（使用Gradle插件）

SpringBootGradle插件还包含一个bootRun任务，可用于以分解形式运行应用程序。每当应用org.springframework.boot和java插件时，都会添加bootRun任务。

### 7.5. Hot Swapping（热交换）

由于Spring引导应用程序只是普通的Java应用程序，JVM热交换应该是现成的。JVM热交换在某种程度上受限于它可以替换的字节码。对于更完整的解决方案，可以使用JRebel。

## 8. Developer Tools（开发人员工具）

Spring Boot包括一组额外的工具，这些工具可以使应用程序开发体验更加愉快。spring boot devtools模块可以包含在任何项目中，以提供额外的开发时特性。

### 8.1. Property Defaults（属性默认值）

Spring Boot支持的几个库使用缓存来提高性能。虽然缓存在生产中非常有用，但在开发过程中可能会适得其反，使您无法看到刚刚在应用程序中所做的更改。因此，默认情况下，spring boot devtools会禁用缓存选项。

### 8.2. Automatic Restart（自动重启）

每当类路径上的文件发生更改时，使用spring boot devtools的应用程序都会自动重新启动。

#### **8.2.1. Logging changes in condition evaluation（**记录条件评估中的更改**）**

默认情况下，每次应用程序重新启动时，都会记录显示条件求值增量的报告。在您进行更改（如添加或删除bean以及设置配置属性）时，报表将显示应用程序自动配置的更改。

**8.2.2. Excluding Resources（排除资源）**

某些资源在更改时不一定需要触发重新启动。例如，可以就地编辑Thymeleaf模板。默认情况下，更改/META-INF/maven、/META-INF/resources、/resources、/static、/public或/templates中的资源不会触发重新启动，但会触发实时重新加载。如果要自定义这些排除，可以使用spring.devtools.restart.exclude属性。

**8.2.3. Watching Additional Paths（监视其他路径）**

更改不在类路径上的文件时，您可能希望重新启动或重新加载应用程序。为此，请使用spring.devtools.restart.additional-paths属性配置其他路径以监视更改。

**8.2.4. Disabling Restart（禁用重新启动）**

如果不想使用重新启动功能，可以使用spring.devtools.restart.enabled属性禁用它。在大多数情况下，可以在application.properties中设置此属性（这样做仍然会初始化restart classloader，但它不会监视文件更改）。

**8.2.5. Using a Trigger File（使用触发器文件）**

如果使用的IDE持续编译更改的文件，则可能希望仅在特定时间触发重新启动。为此，您可以使用“触发器文件”，这是一个特殊文件，当您希望实际触发重新启动检查时，必须对其进行修改。

#### **8.2.6. Customizing the Restart Classloader（**自定义重新启动类加载器**）**

如果您在一个多模块项目上工作，并且不是每个模块都导入到您的IDE中，那么您可能需要定制一些东西。为此，可以创建一个META-INF/spring-devtools.properties文件。

**8.2.7. Known Limitations（已知限制）**

重新启动功能不能很好地处理使用标准ObjectInputStream反序列化的对象。如果需要反序列化数据，可能需要将Spring的ConfigurableObjectInputStream与Thread.currenthread（）.getContextClassLoader（）结合使用。

### 8.3. LiveReload**（一个自动刷新插件）**

spring boot devtools模块包括一个嵌入式LiveReload服务器，当资源发生更改时，该服务器可用于触发浏览器刷新。从LiveReload.com可以免费获得针对Chrome、Firefox和Safari的LiveReload浏览器扩展。

### 8.4. Global Settings**（全局设置）**

您可以通过将以下任何文件添加到$HOME/.config/spring boot文件夹来配置全局devtools设置：

spring-boot-devtools.properties

spring-boot-devtools.yaml

spring-boot-devtools.yml

添加到这些文件中的任何属性都适用于使用devtools的计算机上的所有Spring引导应用程序。

### 8.5. Remote Applications（远程应用程序）

Spring Boot开发工具并不局限于本地开发。您还可以在远程运行应用程序时使用一些功能。远程支持是可选的，因为启用它可能会带来安全风险。只有在受信任的网络上运行或使用SSL保护时才应启用它。

**8.5.1. Running the Remote Client Application（运行远程客户端应用程序）**

远程客户端应用程序设计为从IDE中运行。您需要使用与连接到的远程项目相同的类路径运行org.springframework.boot.devtools.RemoteSpringApplication。应用程序的唯一必需参数是它连接到的远程URL。                                                                    

**8.5.2. Remote Update（远程更新）**

远程客户机以与本地重新启动相同的方式监视应用程序类路径的更改。任何更新的资源都被推送到远程应用程序，并（如果需要）触发重新启动。如果您迭代使用本地没有的云服务的功能，这将非常有用。通常，远程更新和重新启动要比完整的重建和部署周期快得多。

**8.5.3. Configuring File System Watcher（配置文件系统监视程序）**

FileSystemWatcher的工作方式是按一定时间间隔轮询类更改，然后等待预定义的静默期以确保没有更多更改。然后将更改上传到远程应用程序。配置文件系统监视程序监视的类路径文件夹以设定的时间轮询一次以获取更改，再设定静默期的时间， 保持一段时间的静默期以确保没有其他类更改。

## 9. Packaging Your Application for Production（将应用程序打包以供部署）

可执行jar可以用于生产部署。 由于它们是独立的，因此它们也非常适合基于云的部署。

## 10. What to Read Next（下一步阅读）

现在您应该了解如何使用Spring Boot以及应该遵循的一些最佳实践。现在，您可以继续深入了解特定的Spring Boot特性。

