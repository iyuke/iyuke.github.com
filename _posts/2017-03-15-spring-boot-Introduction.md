---
layout:         post
title:          Spring Boot 参考指南之入门指南
subtitle:       
card-image:     https://ww1.sinaimg.cn/mw690/906cb9dbly1fdoq1o4qe1j20q00d4qed
date:           2017-03-15 13:00:00
tags:           code
post-card-type: image
---

## Spring Boot 介绍

这个段落提供 Spring Boot 参考指南的简要综述。将它视作其他部分介绍的指引。你可以顺次阅读本参考指南，或者跳过你不感兴趣的部分。

### 1.关于资料

Spring Boot 参考指南现提供 [html](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/html)，[pdf](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/pdf/spring-boot-reference.pdf) 以及 [epub](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/epub/spring-boot-reference.epub) 版本，最新版可以访问 [http://docs.spring.io/spring-boot/docs/current/reference](http://docs.spring.io/spring-boot/docs/current/reference)。
这些资料的副本允许个人拥有及向他人发布。规定你不得利用这些副本获得任何费用。并且该规定也适用于包含此版权声明的电子分发制品。

### 2.获得帮助
对于 Spring Boot 中遇到的问题，我们愿意帮助你！

* 尝试 [How-to’s](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#howto) — 对于大部分普通问题他们会提供解决方案。
* 学习 Spring 基本要素 — Spring Boot 是构建在其他诸多 Spring 工程之上，访问 [spring.io](spring.io) 网站会提供大量参考指南。如果你是刚刚接触 Spring，尝试其中的 [guides](http://spring.io/guides)。
* 提问 — 我们会关注 [stackoverflow.com](http://stackoverflow.com/) 上被标注为 spring-boot 的问题。
* 报告 Spring Boot 的缺陷可以访问 [github.com/spring-projects/spring-boot/issues](https://github.com/spring-projects/spring-boot/issues)。

> 全部 Spring Boot 为开放源代码，包括文档！如果你发现文档的问题，或者你只是想改善它们，请访问 [get involved](get involved)。

### 3.第一步

如果你刚刚开始接触 Spring Boot 或者 Spring，通常是 [从这里开始](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#getting-started)！

* 从头做起：[概览](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#getting-started-introducing-spring-boot) | [需求](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#getting-started-system-requirements) | 安装
* 教程： [Part 1](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#getting-started-first-application) | [Part 2](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#getting-started-first-application-code)
* 运行你的例子： [Part 1](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#getting-started-first-application-run) | [Part 2](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#getting-started-first-application-executable-jar)

### 4.使用 Spring Boot

已经准备好实际开始使用 Spring Boot 了吗？ [我们已经替你代劳了](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#using-boot)。

* 构建环境：[Maven](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#using-boot-maven) | [Gradle](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#using-boot-gradle) | [Ant](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#using-boot-ant) | [Starters](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#using-boot-starter)
* 最佳实践：[程序结构](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#using-boot-structuring-your-code) | [@Configuration](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#using-boot-configuration-classes) | [@EnableAutoConfiguration](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#using-boot-auto-configuration) | [Beans 与依赖注入](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#using-boot-spring-beans-and-dependency-injection)
* 运行你的程序：[IDE](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#using-boot-running-from-an-ide) | [Packaged](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#using-boot-running-as-a-packaged-application) | [Maven](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#using-boot-running-with-the-maven-plugin) | [Gradle](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#using-boot-running-with-the-gradle-plugin)
* 打包你的应用： [Production jars](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#using-boot-running-with-the-gradle-plugin)
* Spring Boot CLI：[使用 CLI](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#cli)

### 5.了解 Spring Boot 的技术特征

需要了解更多关于 Spring Boot 的核心技术特征？[这个适合你](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#boot-features)！

* 核心技术特征：[Spring应用程序](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#boot-features-spring-application) | [外部配置](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#boot-features-external-config) | [Profiles] | [Logging]
* Web 应用：[MVC](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#boot-features-spring-mvc) | [内嵌容器](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#boot-features-embedded-container)
* 操作数据：[SQL](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#boot-features-sql) | [NO-SQL](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#boot-features-nosql)
* 消息：[概览](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#boot-features-messaging) | [JMS](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#boot-features-jms)
* 测试：[概览](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#boot-features-testing) | [Boot 应用程序](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#boot-features-testing-spring-boot-applications) | [实用工具](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#boot-features-test-utilities)
* 扩展：[Auto-configuration](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#boot-features-developing-auto-configuration) | [@Conditions](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#boot-features-condition-annotations)

### 6.部署到生产环境

当你已经准备好将你的 Spring Boot 应用部署到生产环境时，我们已经为你准备好 [一些使用技巧也许你会喜欢](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#production-ready)！

* 管理节点：[概览](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#production-ready-endpoints) | [定制化](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#production-ready-customizing-endpoints)
* 网络连接选项：[HTTP](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#production-ready-monitoring) | [JMX](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#production-ready-jmx) | [SSH](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#production-ready-remote-shell)
* 监视：[Metrics](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#production-ready-metrics) | [Auditing](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#production-ready-metrics) | [Tracing](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#production-ready-tracing) | [Process](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#production-ready-process-monitoring)

### 7.高级话题

最后，我们有一些话题留给更加高级的使用者。

* 部署 Spring Boot 应用：[部署到云服务器](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#cloud-deployment) | [系统服务](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#deployment-service)
* 构建工具插件：[Maven](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#build-tool-plugins-maven-plugin) | [Gradle](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#build-tool-plugins-gradle-plugin)
* 附录：[应用程序配置](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#common-application-properties) | [自动配置类](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#auto-configuration-classes) | [可执行 Jars](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#executable-jar)

## 入门指南

如果你刚刚准备开始 Spring Boot 或者“Spring”，这个章节适合你！在这里我们会回答最基本的“什么？”，“怎样？”和“为什么？”的问题。

伴随着安装介绍，你会找到一个详尽的 Spring Boot 入门。随后我们会构建第一个 Spring Boot 应用程序。随着我们的推进会探讨一些核心原理。

### 8.Spring Boot 介绍

Spring Boot 允许你能够通过“简单运行”的方式来轻松地创建一些独立运行的生产环境级别的基于 Spring 技术的应用程序。我们可以凭借着 Spring 平台的固有的观点和第三方资源库，使得你以最小的代价来开始学习。绝大多数的 Spring Boot 应用程序需要非常少量的 Spring 配置。

你可以使用 Spring Boot 来创建能够被```java -var```方式或者其他经典的 war 部署方式所使用的 Java 应用程序。我们也提供了一个命令行工具来运行“spring scripts”。

我们的主要目标是：

* 为所有 Spring 开发者提供一个更加快捷的，能够被广泛接受的入门体验。
* 跳出固有的条条框框，快速地回避一些与初始要求相背离的必要条件。
* 针对工程中大量的共用类，提供一整套非功能性特征描述（比如：内嵌服务器，安全，指标测量，健康度检查，外部配置）。
* 绝对的避免代码生成以及不必要的 XML 配置。

### 9.系统需求

默认情况，Spring Boot 1.4.2.RELEASE 需要 Java 7 以及 Spring Framework 4.3.4.RELEASE 以上的环境运行。你可以使用一些追加配置来在 Java 6 的环境中运行 Spring Boot。更多细节请参考 80.11章，“怎样在 Java 6 中使用” 。请明确需要在被支持的 Maven（3.2+）以及 Gradle（1.12 或 2.x）上构建应用。Gradle 2.8 及更早期版本虽然被支持但已不被推荐使用。Gradle 3 不被支持。

> 虽然你可以使用 Java 6 或 7 来使用 Spring Boot，但通常情况下如有可能我们还是会推荐使用 Java 8.

#### 9.1.Servlet 容器

以下表格中的内嵌 Servlet 容器可以被支持：

| 名称          | Servlet 版本 | Java 版本|
|--------------|-------------|-------------|
| Tomcat 8     | 3.1         | Java 7+|
| Tomcat 7     | 3.0         | Java 6+|
| Jetty 9.3    | 3.1 	     | Java 8+|
| Jetty 9.2    | 3.1	     | Java 7+|
| Jetty 8      | 3.0         | Java 6+|
| Undertow 1.3 | 3.1         | Java 7+|

你也可以部署 Spring Boot 应用程序至任意兼容的 Servlet 3.0+ 容器。

### 10.安装 Spring Boot

Spring Boot 可以与“经典的” Java 开发工具一起使用，或者被安装成为命令行工具。无论如何，你都需要一个 Java SDK v1.6 或更高版本的环境。你可以在正式开始前检查以下自己当前安装的 Java 版本。

```
$ java -version
```

如果你不太熟悉 Java 开发，亦或你只是像尝试一下 Spring Boot，你也许会想先尝试一下 Spring Boot CLI ，此外，你还需要看一下“经典的”安装介绍。

> 虽然 Spring Boot 兼容 Java1.6，但是，如果可能能的话，你应该考虑一下使用最新版本的 Java。


#### 10.1.面向 Java 开发人员的安装介绍

你可以像其他标准的 Java 库一样来使用 Spring Boot。在你的 classpath 中简单的添加正确的 ```spring-boot-*.jar``` 文件。Spring Boot 不需要其他特殊的集成工具，因此你可以使用任意的 IDE 或文本编辑器；并且也无需做任何与 Spring Boot 应用程序有关的事情，你可以像其他 Java 程序那样来运行和调试。
虽然你可以仅仅复制 Spring Boot 的Jars文件，通常我们还是会推荐你使用一款支持依赖管理的构建工具。（比如 Maven 或者 Gradle）。

##### 10.1.1.Maven 安装

Spring Boot 兼容 Apache Maven 3.2 及以上版本。如果你尚未安装 Maven，你可以按照下面的介绍（ [maven.apache.org](http://maven.apache.org/) ）来安装。

> 在许多操作系统上 Maven 可以通过 package 管理器来进行安装。如果你是一位 OSX Homebrew 用户，试一下 ```brew install maven``` 。Ubuntu 用户可以运行 ```sudo apt-get install maven``` 。

Spring Boot 需要使用 ```org.springframework.boot``` ```groupId``` 来进行依赖管理。最典型的，你的 Maven POM 文件将继承自 ```spring-boot-starter-parent``` 工程并且定义了依赖于1个或多个“ 启动器 ”。Spring Boot 也提供了一个可选项 Maven 插件 来创建可执行的 jars 文件。

下面是一个典型的 pom.xml 文件：

```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>myproject</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <!-- Inherit defaults from Spring Boot -->
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.4.2.RELEASE</version>
    </parent>
    <!-- Add typical dependencies for a web application -->
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
    </dependencies>
    <!-- Package as an executable jar -->
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
</project>
```

> ```spring-boot-starter-parent``` 是一个很棒的方法来使用 Spring Boot。但它可能不是所有时候都适用。有时你也许需要继承自一个其他的父 POM ，亦或者你也许只是不喜欢我们的默认设置。参考 13.2.2章,”摆脱父 POM 来使用 Spring Boot” 是一个替代方案来使用一个 ```import``` 范围。

##### 10.1.2.Gradle 安装

Spring Boot 兼容 Gradle 1.12 或者 2.x 版本。但 2.8及更早期的版本不推荐使用。Gradle 2.14.1版本被推荐使用。Gradle 3 不被支持。如果你尚未安装好 Gradle，你可以按照 [www.gradle.org](http://www.gradle.org/) 上的介绍来安装。
Spring Boot 的依赖关系能够使用 ```org.springframework.boot group``` 来进行定义。最典型的，你的工程将被定义成与1个或多个“ [Starters](http://docs.spring.io/spring-boot/docs/1.4.2.RELEASE/reference/htmlsingle/#using-boot-starter) ”有依赖关系。Spring Boot 提供了有帮助的 Gradle 插件，以用来简化创建可执行 jars 文件时依赖关系的定义。

> ##### Gradle Wrapper
当你需要构建一个工程时，Gradle Wrapper 提供了一个巧妙的办法来“获取”Gradle。它是由一个能够使用你自己的代码引导构建过程的小型脚本和类库组成。更多的细节请参考 docs.gradle.org/2.14.1/userguide/gradle_wrapper.html 。

以下是一个典型的 build.gradle 文件：

```
buildscript {
    repositories {
        jcenter()
        maven { url "http://repo.spring.io/snapshot" }
        maven { url "http://repo.spring.io/milestone" }
    }
    dependencies {
        classpath("org.springframework.boot:spring-boot-gradle-plugin:1.4.2.RELEASE")
    }
}
apply plugin: 'java'
apply plugin: 'org.springframework.boot'
jar {
    baseName = 'myproject'
    version =  '0.0.1-SNAPSHOT'
}
repositories {
    jcenter()
    maven { url "http://repo.spring.io/snapshot" }
    maven { url "http://repo.spring.io/milestone" }
}
dependencies {
    compile("org.springframework.boot:spring-boot-starter-web")
    testCompile("org.springframework.boot:spring-boot-starter-test")
}
```

#### 10.2.安装 Spring Boot CLI

Spring Boot CLI 是一个可以让你用来快速进行 Spring 原型开发的命令行工具。它允许你运行 [Groovy](http://groovy.codehaus.org/) 脚本，这意味你可以摆脱引用很多代码的前提下，使用类似 Java 的语法。
你不需要使用 CLI 来进行 Spring Boot 开发，但它确实是一条最快的途径来实际开发一个 Spring 应用程序。

##### 10.2.1安装手册

你可以从 Spring 软件仓库下载 Spring CLI 的分发版本：

* [spring-boot-cli-1.4.2.RELEASE-bin.zip](http://repo.spring.io/release/org/springframework/boot/spring-boot-cli/1.4.2.RELEASE/spring-boot-cli-1.4.2.RELEASE-bin.zip)
* [spring-boot-cli-1.4.2.RELEASE-bin.tar.gz](http://repo.spring.io/release/org/springframework/boot/spring-boot-cli/1.4.2.RELEASE/spring-boot-cli-1.4.2.RELEASE-bin.tar.gz)

最新版本的 [快照](http://repo.spring.io/snapshot/org/springframework/boot/spring-boot-cli/) 也可以使用。

成功下载之后，解开压缩包按照 [INSTALL.txt](https://raw.github.com/spring-projects/spring-boot/v1.4.2.RELEASE/spring-boot-cli/src/main/content/INSTALL.txt) 来进行操作。概括起来：在 ```.zip``` 文件的 ```bin/``` 目录中有一个 spring 脚本（Windows 是 ```spring.bat``` ），或者作为替代方案，你可以使用 ```java -jar``` 来运行 ```.jar 文件```（脚本文件将帮助你确定 classpath 是否设置正确）

##### 10.2.2.使用 SDKMAN！安装

SDKMAN！（The Software Development Kit Manager）可以被用来管理多版本的各种各样的 SDK，包括 Groovy 和 Spring Boot CLI。可以从 [sdkman.io](http://sdkman.io/) 获得SDKMAN！并安装 Spring Boot：

```
$ sdk install springboot
$ spring --version
Spring Boot v1.4.2.RELEASE
```

如果你正在为 CLI 开发功能，并且希望很方便的调用你刚刚构建的版本的话，请按照以下扩展说明来做。

```
$ sdk install springboot dev /path/to/spring-boot/spring-boot-cli/target/spring-boot-cli-1.4.2.RELEASE-bin/spring-1.4.2.RELEASE/
$ sdk default springboot dev
$ spring --version
Spring CLI v1.4.2.RELEASE
```

这样会安装一个本地的 ```Spring``` 实例，并被称作 ```dev``` 实例。它指向你的目标构建位置，因此你可以随时重构你的 Spring Boot，Spring 将会更新到最新版本。

进行如下操作后可以看到：

```
$ sdk ls springboot
================================================================================
Available Springboot Versions
================================================================================
> + dev
* 1.4.2.RELEASE
================================================================================
+ - local version
* - installed
> - currently in use
================================================================================
```

##### 10.2.3.OSX Homebrew 安装

如果你正在 Mac 上使用 Homebrew，以下是你为了安装 Spring Boot CLI 所有做的全部：

```
$ brew tap pivotal/tap
$ brew install springboot
```

Homebrew 将会把 ```spring``` 安装到 ```/usr/local/bin```。

> 如果你没有看到预期的结果，可能你安装的 brew 版本已经过时。只需要执行 ```brew update``` 并再试一次。

##### 10.2.4.MacPorts 安装

如果你正在 Mac 上使用 MacPorts，以下是你为了安装 Spring Boot CLI 所有做的全部：

```
$ sudo port install spring-boot-cli
```

##### 10.2.5.命令行实现

作为过渡，Spring Boot CLI 为 BASH 和 zsh 提供了命令行实现的脚本。你可以在任意shell里 ```source``` 脚本（也被成为 spring），或者把它放入你个人或者系统级别的 bash 初始化中。在 Debian 系统中系统级别的脚本被放置在 ```/shell-completion/bash``` 中，并且当一个新的 shell 执行时，那个目录中的所有脚本都会被执行。要手动执行脚本，例如，如果你已经通过 SDKMAN！安装了的话：

```
$ . ~/.sdkman/candidates/springboot/current/shell-completion/bash/spring
$ spring <HIT TAB HERE>
  grab  help  jar  run  test  version
```

> 如果你使用 Homebrew 或者 MacPorts 安装 Spring Boot，命令行实现脚本将会自动注册到你的 shell 中。

##### 10.2.6.快速开始 Spring CLI 范例

这里有一个相当简单的 web 应用程序以供你能够用来测试你的安装。建立一个命名为 ```app.groovy``` 的文件：

```
@RestController
class ThisWillActuallyRun {
    @RequestMapping("/")
    String home() {
        "Hello World!"
    }
}
```

然后从 shell 中简单的运行：

```
$ spring run app.groovy
```

> 当你初次运行这个程序有余需要下载依赖的程序，所以它会花费一些时间。再次运行之后它会更快一些，

在你常用的浏览器中打开 [localhost:8080](http://localhost:8080)，你会看到如下输出结果：

```
Hello World!
```

#### 10.3.升级早期版本的 Spring Boot

如果你要从早期的 Spring Boot 发行版本升级，请检查 (project wiki)[https://github.com/spring-projects/spring-boot/wiki] 在上的“发行记录”。你可以找到关于每个版本“新特性及值得注意地方”的升级介绍。
要使用一个适当的包管理器命令来升级一个已经安装的 CLI（例如 ```brew upgrade``` ） 亦或者你要按照 标准介绍 手动的更新已经安装的 CLI，记住要更新你的 ```PATH``` 环境变量以移除一些旧的关联信息。
