---
layout: post
title: Spring Boot Features 之 Profiles
tags: ["Spring Boot"]
---

Spring Profiles 提供了一种隔离应用程序部分配置的方法，使其仅在特定环境中可用。任何 @Component 或者 @Configuration 加载时都可以被 @Profile 来标记作限制，如以下示例所示：
```java
@Configuration
@Profile("production")
public class ProductionConfiguration {
// ...
}
```

你可以使用 `spring.profiles.active` 环境变量来指定哪些配置文件是活动的。例如，您可以将它包含在您的  application.properties 配置文件中，如以下示例所示：
```
spring.profiles.active=dev,hsqldb
```

你也可以在命令行中指定它，使用以下方式：`--spring.profiles.active=dev,hsqldb`。

## 1. 添加活动的配置
spring.profiles.active 属性遵循与其他属性相同的排序规则：最高的 PropertySource 获胜。这意味着您可以在 application.pro   perties 指定活动的配置文件，然后使用命令行开关替换它们。

有时候，将特定配置文件中的属性添加到活动配置文件而不是去替换他们是很有用的，pring.profiles.include 属性可用于无条件地添加活动配置文件。SpringApplication入口点还有一个JavaAPI，用于设置其他配置文件（也就是说，在 Spring.profiles.Active 属性激活的对象之上）。请参阅 [SpringApplication](https://docs.spring.io/spring-boot/docs/2.1.3.RELEASE/api/org/springframework/boot/SpringApplication.html) 中的 setAtttionalProfiles() 方法。

例如，当一个具有以下属性的应用程序使用开关 --Spring.profiles.Active=prod 运行时，proddb 和 prodmq 配置文件也会被激活：
``` yaml
---
my.property: fromyamlfile
---
spring.profiles: prod
spring.profiles.include:
 - proddb
 - prodmq
```
`笔记: <br>请记住，Spring.profile属性可以在YAML文档中定义，以确定何时将此特定文档包含在配置中。`

## 2. 以编程的方式设置配置文件
你可以在应用启动前以编码的方式调用 SpringApplication.setAdditionalProfiles(…) 方法来设置激活的配置。你也可以使用 Spring 的 ConfigurableEnvironment 接口来激活配置文件。

## 3. 必要的配置文件
application.properties (或 application.yml) 和参考文件都视为文档，通过注解 @ConfigurationProperties 来加载。