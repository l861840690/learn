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

