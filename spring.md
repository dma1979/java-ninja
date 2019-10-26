[All questions](README.md)

# Spring framework
+ [What does PECS stand for?](#what-does-pecs-stand-for)
+ [What are wildcards and their types?](#what-are-wildcards-and-their-types)
+ [What are covariant, contravariant and invariant?](#what-are-covariant-contravariant-and-invariant)

### What Are the Differences Between Spring and Spring Boot??
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
                    
[All questions](README.md)