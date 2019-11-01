[All questions](README.md)

# Spring framework
## Spring
+ [What is Spring Data JPA?](#what-is-spring-data-jpa)
## Spring Boot
+ [What is Spring Boot? Why should you use it?](#what-is-spring-boot?-why-should-you-use-it)
+ [What Are the Differences Between Spring and Spring Boot?](#what-are-the-differences-between-spring-and-spring-boot)
+ [How set up a Spring Boot Application with Maven?](#how-set-up-a-spring-boot-application-with-maven)
+ [What Spring Boot Starters are available?](#what-spring-boot-starters-are-available)

### What is Spring Data JPA?
__Spring Data JPA__ is not a JPA provider but a specification — it is a library/framework that adds an extra layer of abstraction on the top of our JPA provider. It simply “hides” the Java Persistence API and the JPA provider behind its repository abstraction.

__JPA__ is the sun specification for persisting objects in the enterprise application. 

The __JPA Provider__ implements the Java Persistence API. 
The Java Persistence API is used for managing, persisting, and accessing data between objects and the relational database. Hibernate is an ORM (Object Relational Mapping) tool that implements JPA specification.

The implementation of JPA specifications is provided by many JPA providers, such as Hibernate, Toplink, iBatis, OpenJPA, etc.

### What are main feature of Spring Data JPA?
Main features:
* Create and support repositories created with Spring and JPA
* Support JPA queries
* Support for batch loading, sorting, dynamical queries
* Supports XML mapping for entities
* Reduce code size for generic CRUD operations by using the CrudRepository

### What is DAO?
DAO = Data Access Object

### What is Spring Boot? Why should you use it?
Spring Boot is another Java framework from Spring umbrella which aims to simplify the use of Spring Framework for Java development.
It removes most of the pain associated with dealing with Spring e.g. a lot of configuration and dependencies and a lot of manual setups.<BR/>

Why should you use it? Well, Spring Boot not only provides a lot of convenience by auto-configuration a lot of things for you 
but also improves the productivity because it lets you focus only on writing your business logic.

For example, you don't need to setup a Tomcat server to run your web application. 
You can just write code and run it as Java application because it comes with an embedded Tomcat server. 
You can also create a JAR file or WAR file for deployment based on your convenience.

There are many reasons to use Spring Boot. In fact, it's now the standard way to develop Java application with Spring framework.

[Table of content](#spring-framework)

### What Are the Differences Between Spring and Spring Boot?
The __Spring Framework__ provides multiple features that make the development of web applications easier. 
These features include dependency injection, data binding, aspect-oriented programming, data access, and many more.

Over the years, Spring has been growing more and more complex, and the amount of configuration such application requires can be intimidating. 
__Spring Boot__ makes it easy to create stand-alone, production-grade Spring based Applications that you can "just run".
Most Spring Boot applications need very little Spring configuration.

Spring Boot Features:
* Create stand-alone Spring applications
* Automatically configure Spring and 3rd party libraries whenever possible
* Embed Tomcat, Jetty or Undertow directly (no need to deploy WAR files)
* Provide opinionated 'starter' dependencies to simplify your build configuration
* Provide production-ready features such as metrics, health checks and externalized configuration
* Absolutely no code generation and no requirement for XML configuration

[Table of content](#spring-framework)

### How set up a Spring Boot Application with Maven?
Spring Boot can be included in a Maven project just like we would any other library. 
There are several ways to do it:
* The best way is to inherit from the spring-boot-starter-parent project and declare dependencies to Spring Boot starters. 
Doing this lets our project reuse the default settings of Spring Boot.
Inheriting the spring-boot-starter-parent project is straightforward – we only need to specify a parent element in pom.xml:
```
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.2.0.RELEASE</version>
</parent>
```
The latest version of spring-boot-starter-parent can be found on Maven Central.
Using the starter parent project is convenient, but not always feasible. 
For instance, if our company requires all projects to inherit from a standard POM, we cannot rely on the Spring Boot starter parent.

* Add dependency to reap the benefits of dependency management with this POM element:
```
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-dependencies</artifactId>
            <version>2.2.0.RELEASE</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
```

* Add some dependencies to required equSpring Boot starters.

[Table of content](#spring-framework)

### What Spring Boot Starters are available?
Dependency management is a crucial facet of any project. 
Each starter plays a role as a one-stop shop for concrete Spring technologies. 
Other required dependencies are then transitively pulled in and managed in a consistent way.

All starters are under the `org.springframework.boot` group, and their names start with `spring-boot-starter-`. 

The most commonly used starters are:
* spring-boot-starter: core starter, including auto-configuration support, logging, and YAML
* spring-boot-starter-aop: starter for aspect-oriented programming with Spring AOP and AspectJ
* spring-boot-starter-data-jpa: starter for using Spring Data JPA with Hibernate
* spring-boot-starter-jdbc: starter for using JDBC with the HikariCP connection pool
* spring-boot-starter-security: starter for using Spring Security
* spring-boot-starter-test: starter for testing Spring Boot applications
* spring-boot-starter-web: starter for building web, including RESTful, applications using Spring MVC
    
[Table of content](#spring-framework)

### How to Disable a Specific Auto-Configuration?
* indicate it using the exclude attribute of the __@EnableAutoConfiguration__ annotation. 
For instance, this code snippet neutralizes DataSourceAutoConfiguration:
```
// other annotations
@EnableAutoConfiguration(exclude = DataSourceAutoConfiguration.class)
public class MyConfiguration { }
```
* If we enabled auto-configuration with the @SpringBootApplication annotation — 
which has __@EnableAutoConfiguration__ as a meta-annotation — we could disable auto-configuration with an attribute of the same name:

```
// other annotations
@SpringBootApplication(exclude = DataSourceAutoConfiguration.class)
public class MyConfiguration { }
```
* with the `spring.autoconfigure.exclude` environment property. This setting in the `application.properties` file does the same thing as before:
```
spring.autoconfigure.exclude=org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration
```
[Table of content](#spring-framework)

### How to Register a Custom Auto-Configuration?
To register an auto-configuration class, we must have its fully-qualified name listed under the `EnableAutoConfiguration` key in the `META-INF/spring.factories` file:
```
org.springframework.boot.autoconfigure.EnableAutoConfiguration=com.mycompany.autoconfigure.CustomAutoConfiguration
```
If we build a project with Maven, that file should be placed in the `resources/META-INF` directory, 
which will end up in the mentioned location during the package phase.

[Table of content](#spring-framework)

### How to Tell an Auto-Configuration to Back Away When a Bean Exists?
To instruct an auto-configuration class to back off when a bean is already existent, use the `@ConditionalOnMissingBean` annotation. 
The most noticeable attributes of this annotation are:
* value: The types of beans to be checked
* name: The names of beans to be checked
When placed on a method adorned with @Bean, the target type defaults to the method's return type:
```
@Configuration
public class CustomConfiguration {
    @Bean
    @ConditionalOnMissingBean
    public CustomService service() { ... }
}

```

[Table of content](#spring-framework)

### How to Deploy Spring Boot Web Applications as Jar and War Files?
Spring tackles this problem by providing a plugin __spring-boot-maven-plugin__, to package a web application as an executable JAR. 
To include this plugin, just add a plugin element to pom.xml:
```
<plugin>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-maven-plugin</artifactId>
</plugin>
```
With this plugin in place, we'll get a fat JAR after executing the package phase. 
This JAR contains all the necessary dependencies, including an embedded server. 
Thus, we no longer need to worry about configuring an external server.
We can then run the application just like we would an ordinary executable JAR.
Notice that the packaging element in the pom.xml file must be set to jar to build a JAR file:
```
<packaging>jar</packaging>
```
If we don't include this element, it also defaults to jar.

In case we want to build a WAR file, change the packaging element to war:
```
<packaging>war</packaging>
```
And leave the container dependency off the packaged file:
```
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-tomcat</artifactId>
    <scope>provided</scope>
</dependency>
```
After executing the Maven package phase, we'll have a deployable WAR file.

[Table of content](#spring-framework)

### How to Use Spring Boot for Command Line Applications?
Just like any other Java program, a Spring Boot command line application must have a main method. 
This method serves as an entry point, which invokes the SpringApplication#run method to bootstrap the application:
```
@SpringBootApplication
public class TestApplication {
    public static void main(String[] args) {
        SpringApplication.run(TestApplication.class);
        // more statements
    }
}
```
The SpringApplication class then fires up a Spring container and auto-configures beans.
Notice we must pass a configuration class to the run method to work as the primary configuration source. 
By convention, this argument is the entry class itself.
    
[Table of content](#spring-framework)
    
### What Are Possible Sources of External Configuration?
Spring Boot provides support for external configuration, allowing us to run the same application in various environments. 
We can use properties files, YAML files, environment variables, system properties, and command-line option arguments to specify configuration properties.
We can then gain access to those properties using the @Value annotation, a bound object via the @ConfigurationProperties annotation, or the Environment abstraction.
The most common sources of external configuration:
* __Command-line properties__: Command-line option arguments are program arguments starting with a double hyphen, such as `–server.port=8080`. 
Spring Boot converts all the arguments to properties and adds them to the set of environment properties.
* __Application properties__: Application properties are those loaded from the application.properties file or its YAML counterpart. 
By default, Spring Boot searches for this file in the current directory, classpath root, or their config subdirectory.
* __Profile-specific properties__: Profile-specific properties are loaded from the application-{profile}.properties file or its YAML counterpart. The {profile} placeholder refers to an active profile. These files are in the same locations as, and take precedence over, non-specific property files.

[Table of content](#spring-framework)

### What does it mean that Spring Boot supports relaxed binding?
__Relaxed binding__ in Spring Boot is applicable to the type-safe binding of configuration properties.
With relaxed binding, the key of an environment property doesn't need to be an exact match of a property name. 
Such an environment property can be written in camelCase, kebab-case, snake_case, or in uppercase with words separated by underscores.

For example, if a property in a bean class with the `@ConfigurationProperties` annotation is named `myProp`, 
it can be bound to any of these environment properties: `myProp`, `my-prop`, `my_prop`, or `MY_PROP`.

[Table of content](#spring-framework)

### What is Spring Boot Devtools Used For?
Spring Boot Developer Tools, or DevTools, is a set of tools making the development process easier. 
To include these development-time features, we just need to add a dependency to the pom.xml file:
```
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
</dependency>
```
The spring-boot-devtools module is automatically disabled if the application runs in production. 
The repackaging of archives also excludes this module by default. 

By default, DevTools applies properties suitable to a development environment. 
These properties disable template caching, enable debug logging for the web group, and so on. 
As a result, we have this sensible development-time configuration without setting any properties.

Applications using DevTools restart whenever a file on the classpath changes. 
This is a very helpful feature in development, as it gives quick feedback for modifications.

By default, static resources, including view templates, don't set off a restart. 
Instead, a resource change triggers a browser refresh. 
Notice this can only happen if the LiveReload extension is installed in the browser to interact with the embedded LiveReload server that DevTools contains.

[Table of content](#spring-framework)

### How to Write Integration Tests?
When running integration tests for a Spring application, we must have an `ApplicationContext`.

To make our life easier, Spring Boot provides a special annotation for testing – `@SpringBootTest`. 
This annotation creates an ApplicationContext from configuration classes indicated by its classes attribute.

In case the classes attribute isn't set, Spring Boot searches for the primary configuration class. 
The search starts from the package containing the test up until it finds a class annotated with @SpringBootApplication or @SpringBootConfiguration.

Notice if we use JUnit 4, we must decorate the test class with @RunWith(SpringRunner.class).

[Table of content](#spring-framework)

### What Is Spring Boot Actuator Used For?
Actuator brings Spring Boot applications to life by enabling production-ready features. 
These features allow us to monitor and manage applications when they're running in production.

Integrating Spring Boot Actuator into a project is very simple:

```
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```
Spring Boot Actuator can expose operational information using either HTTP or JMX endpoints. Most applications go for HTTP, though, where the identity of an endpoint and the /actuator prefix form a URL path.

The most common built-in endpoints Actuator provides:
* __auditevents__: Exposes audit events information
* __env__: Exposes environment properties
* __health__: Shows application health information
* __httptrace__: Displays HTTP trace information
* __info__: Displays arbitrary application information
* __metrics__: Shows metrics information
* __loggers__: Shows and modifies the configuration of loggers in the application
* __mappings__: Displays a list of all @RequestMapping paths
* __scheduledtasks__: Displays the scheduled tasks in your application
* __threaddump__: Performs a thread dump
    
[Table of content](#spring-framework)
                    
### What are some important features of using Spring Boot?
This is a good subjective question and used by the interviewer to gauge the experience of a candidate with Spring Boot. 
Anyway, following are some of the important features of Spring Boot framework:
1. Starter dependency
This feature aggregates common dependencies together. For example, if you want to develop Spring MVC based RESTful services then instead of including Spring MVC JAR and Jackson JAR file into classpath you can just specify spring-boot-web-starter and it will automatically download both those JAR files. Spring Boot comes with many such starter dependencies to improve productivity.
2. Auto-Configuration
This is another awesome features of Spring Boot which can configure many things for you. For example, If you are developing Spring web application and Thymeleaf.jar is present on the classpath then it can automatically configure Thymeleaf template resolver, view resolver, and other settings. A good knowledge of auto-configuration is required to become an experienced Spring Boot developers.
3. Spring Initializer
A web application which can create initial project structure for you. This simplifies initial project setup part.
4. Spring Actuator
This feature provides a lot of insights of a running Spring boot application. For example, you can use Actuator to find out which beans are created in Spring's application context and which request path are mapped to controllers.
5. Spring CLI
This is another awesome feature of Spring Boot which really takes Spring development into next level. It allows you to use Groovy for writing Spring boot application which means a lot more concise code.

### What is auto-configuration in Spring boot? how does it help? Why Spring Boot is called opinionated?
There are a lot of questions in this one question itself, but let's first tackle auto-configuration. 
auto-configuration is one of awesome features of Spring Boot which can configure many things for you. 
For example, If you are developing Spring web application and Thymeleaf.jar is present on the classpath then it can automatically configure Thymeleaf template resolver, view resolver, and other settings. A good knowledge of auto-configuration is required to become an experienced Spring Boot developers.
it automatically configures a lot of things based upon what is present in the classpath.

For example, it can configure JdbcTemplate if its present and a DataSource bean are available in the classpath. 
It can even do some basic web security stuff if Spring security is present in the classpath.
Anyway, the point is auto-configuration does a lot of work for you with respect to configuring beans, controllers, view resolvers etc, 
hence it helps a lot in creating a Java application.<BR/>
<BR/>
__why it's considered opinionated__? 
Because it makes a judgment on its own. Sometimes it imports things which you don't want, but don't worry, 
Spring Boot also provides ways to override auto-configuration settings.

It's also disabled by default and you need to use either @SpringBootApplication or @EnableAutoConfiguration annotations on the Main class to enable the auto-configuration feature. See Spring Boot Essentials for learning more about them.

### What is starter dependency in Spring Boot? how does it help?
It's quite similar to auto-configuration and many developers get confused between both of them. 
As the name suggests, starter dependency deal with dependency management.

After examining several Spring-based projects Spring guys notice that there is always some set of libraries which are used together 
e.g. Spring MVC with Jackson for creating RESTful web services. Since declaring a dependency in Maven's pom.xml is the pain, 
they combined many libraries into one based upon functionality and created this starter package.

This not only frees you from declaring many dependencies but also fees you from compatibility and version mismatch issue. 
Spring Boot starter automatically pulls compatible version of other libraries so that you can use them without worrying about any compatibility issue.

### What is the difference between @SpringBootApplication and @EnableAutoConfiguration annotation?
Even though both are essential Spring Boot application and used in the Main class or Bootstrap class there is a subtle difference between them. 
The `@EnableAutoConfiguration` is used to enable auto-configuration but `@SpringBootApplication` does a lot more than that.

It also combines `@Configuration` and `@ComponentScan` annotations to enable Java-based configuration and component scanning in your project.

The `@SpringBootApplication` is in fact combination of @Configuration, @ComponentScan and @EnableAutoConfiguration annotations. You can also check Spring Boot MasterClass to learn more about this annotation and it's used.

### What is Spring Initializer? why should you use it?
One of the difficult things to start with a framework is initial setup, particularly if you are starting from scratch and you don't have a reference setup or project. Spring Initializer addresses this problem in Spring Boot.

It's nothing but a web application which helps you to create initial Spring boot project structure and provides Maven or Gradle build file to build your code.

### What is Spring Actuator? What are its advantages?
Spring Actuator is another cool Spring Boot feature which allows seeing inside a running application.
It allows you to see inside an application. 
Since Spring Boot is all about auto-configuration it makes debugging difficult and at some point in time, 
you want to know which beans are created in Spring's Application Context and how Controllers are mapped. Spring Actuator provides all that information.

It provides several endpoints e.g. a REST endpoint to retrieve this kind of information over the web. 
It also provides a lot of insight and metrics about application health e.g. CPU and memory usage, number of threads etc.

It also comes with a remote shell which you can use to securely go inside Spring Boot application and run some command to expose the same set of data. 
You can even use JMX to control this behavior at runtime.

Btw, it's important to secure your Spring Actuator endpoints because it exposes a lot of confidential information and a potentially dangerous one-two. 
For example, by using /showdown endpoint you can kill a Spring Boot application.
We can use Spring Security to secure Spring Actuator endpoints. 

### What is Spring Boot CLI? What are its benefits?
__Spring Boot CLI__ is a command line interface which allows you to create Spring-based Java application using Groovy. 
Since it's used Groovy, it allows you to create Spring Boot application from the command line without ceremony 
e.g. you don't need to define getter and setter method, or access modifiers, return statements etc.

It's also very powerful and can auto-include a lot of library in Groovy's default package if you happen to use it.

For example, if you use JdbcTempalte, it can automatically load that for you.

### Where do you define properties in Spring Boot application?
You can define both application and Spring boot related properties into a file called `application.properties`. 
You can create this file manually or you can use Spring Initializer to create this file, albeit empty.

You don't need to do any special configuration to instruct Spring Boot load this file. 
If it exists in classpath then Spring Boot automatically loads it and configure itself and application code according.

### Can you change the port of Embedded Tomcat server in Spring boot? If Yes, How?
Yes, the port of Embedded Tomcat Server in Spring Boot can be changed by adding a property called `server.port` in the `application.properties` file.
This property file is automatically loaded by Spring Boot and can be used to configure both Spring Boot as well as application code.

### What is the difference between an embedded container and a WAR?
The main difference between an embedded container and a WAR file is that you can run Spring Boot application as a JAR from the command prompt without setting up a web server. 
But to run a WAR file, you need to first set up a web server like Tomcat which has Servlet container and then you need to deploy WAR there.

### What embedded containers does Spring Boot support?
Spring Boot support three embedded containers: Tomcat, Jetty, and Undertow. By default, it uses Tomcat as embedded containers but you can change it to Jetty or Undertow.

### What are some common Spring Boot annotations?
Some of the most common Spring Boot annotations are `@EnableAutoConfiguration`, `@SpringBootApplication`, `@SpringBootConfiguration`, and `@SpringBootTest`.

The `@EnableAutoConfiguration` is used to enable auto-configuration on Spring Boot application, 
while `@SpringBootApplication` is used on the Main class to allow it to run a JAR file. 
`@SpringBootTest` is used to run unit test on Spring Boot environment.

### Can you name some common Spring Boot Starter POMs?
Some of the most common Spring Boot Start dependencies or POMs are:
- spring-boot-starter, 
- spring-boot-starter-web, 
- spring-boot-starter-test. 
F.e. __spring-boot-starter-web__ can be used to enable Spring MVC in Spring Boot application.

### Can you control logging with Spring Boot? How?
Yes, we can control logging with Spring Boot by specifying log levels on application.properties file. 
Spring Boot loads this file when it exists in the classpath and it can be used to configure both Spring Boot and application code.

Spring Boot uses Commons Logging for all internal logging and you can change log levels by adding following lines in the `application.properties` file:
```
logging.level.org.springframework=DEBUG
logging.level.com.demo=INFO
```

### What is @MockBean annotation?
Spring Boot @MockBean annotation makes it easy to replace a bean with a mock in the application context.

@MockBean is used to add mock objects to the Spring application context. 
The mock will replace any existing bean of the same type in the application context.
If no bean of the same type is defined, a new one will be added. 
This annotation is useful in integration tests where a particular bean – for example, an external service – needs to be mocked.

To use this annotation, we have to use @SpringRunner to run the test:
                    
### What log providers are supported by Spring Boot?
* [Logback, 5](https://logback.qos.ch)
* [Log4j 2](https://logging.apache.org/log4j/2.x/)
* [Java Util Logging](https://docs.oracle.com/javase/7/docs/api/java/util/logging/package-summary.html)
__Spring Boot 2 doesn’t support the older Log4j framework; it supports its
successor, Log4j 2!__
Spring Boot by default uses Logback as the provider for the logging. 
It does, however, support Java Util Logging as well as Log4j 2.
To use another logging framework, you will have to first exclude the default framework and include your own. 
Spring Boot has a spring-boot-starter-log4j2 to include all necessary dependencies for Log4j 2.

### How to configure logging in Sprint Boot?
Spring Boot uses SLF4J as the logging API, and when writing components you should use those interfaces to write your logging.

By default, Spring Boot will only log to the console.
The logging levels can be configured through the regular `application.properties` as well as
patterns can be specified and where to, optionally, write log files to.
```
logging.level.org.springframework.web=DEBUG

```
If you want to write to a file as well, you need to specify either logging.file or logging.path. 
The first takes the name of the file; the second, the path. 
The default filename used is spring.log and the default directory used is the Java temp directory.
```
logging.file=application.log
logging.path=/var/log
```                    
[All questions](README.md)