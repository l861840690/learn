---
description: Spring boot 2.24大纲
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







