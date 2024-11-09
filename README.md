# Spring-Boot-Doc

# Table of content
- [Introduction](#Introduction)
  - [Diffrence between Spring and Spring boot](#Diffrence-between-Spring-and-Spring-boot)
  - [the advantages of using Spring Boot](#the-advantages-of-using-Spring-Boot)
- [Spring Boot architecture](#Spring-Boot-architecture)
  - [Core Components of Spring Boot](#Core-Components-of-Spring-Boot)
  - [Layers of a Spring Boot Application](#Layers-of-a-Spring-Boot-Application)
  - [Example of Spring Boot Architecture in Action](#Example-of-Spring-Boot-Architecture-in-Action)
  - [Spring Boot project architecture](#Spring-Boot-project-architecture)

# Introduction
> - Spring Boot is a powerful framework designed to simplify the development of Spring applications by providing a streamlined setup and reducing configuration complexity.<br/>
> - It’s widely used for building standalone, production-grade Spring applications with minimal setup.<br/>

## Diffrence between Spring and Spring boot
<table>
  <tr>
    <th>Spring</th>
    <th>Spring Boot</th>
  </tr>
  <tr>
    <td>Spring is an open-source lightweight framework widely used to develop enterprise applications.</td>
    <td>Spring Boot is built on top of the conventional spring framework, widely used to develop REST APIs.</td>
  </tr>
  <tr>
    <td>The most important feature of the Spring Framework is dependency injection.</td>
    <td>The most important feature of the Spring Boot is Autoconfiguration.</td>
  </tr>
  <tr>
    <td>It helps to create a loosely coupled application.</td>
    <td>It helps to create a stand-alone application.</td>
  </tr>
  <tr>
    <td>To run the Spring application, we need to set the server explicitly.</td>
    <td>Spring Boot provides embedded servers such as Tomcat and Jetty etc.</td>
  </tr>
  <tr>
    <td>To run the Spring application, a deployment descriptor is required.</td>
    <td>There is no requirement for a deployment descriptor.</td>
  </tr>
  <tr>
    <td>To create a Spring application, the developers write lots of code.</td>
    <td>It reduces the lines of code.</td>
  </tr>
    <tr>
    <td>It doesn’t provide support for the in-memory database.</td>
    <td>It provides support for the in-memory database such as H2.</td>
  </tr>
    <tr>
    <td>Developers have to define dependencies manually in the pom.xml file.</td>
    <td>pom.xml file internally handles the required dependencies.</td>
  </tr>
</table>

## the advantages of using Spring Boot

> - **Easy to use:** The majority of the boilerplate code required to create a Spring application is reduced by Spring Boot.<br/>
> - **Rapid Development:** Spring Boot’s opinionated approach and auto-configuration enable developers to quickly develop apps without the need for time-consuming setup, cutting down on development time.<br/>
> - **Scalable:** Spring Boot apps are intended to be scalable. This implies they may be simply scaled up or down to match your application’s needs.<br/>
> - **Production-ready:** Metrics, health checks, and externalized configuration are just a few of the features that Spring Boot includes and are designed for use in production environments.<br/>
> - **Auto-configuration:** Spring Boot automatically configures dependencies by using @EnableAutoconfiguration annotation and reduces boilerplate code.<br/>
> - **Spring Boot Starter POM:** These Starter POMs are pre-configured dependencies for functions like database, security, maven configuration etc.<br/>
> - **Spring Boot CLI (Command Line Interface):** This command line tool is generally for managing dependencies, creating projects and running the applications.<br/>
> - **Actuator:** Spring Boot Actuator provides health check, metrics and monitors the endpoints of the application. It also simplifies the troubleshooting management.<br/>
> - **Embedded Servers:** Spring Boot contains embedded servers like Tomcat and Jetty for quick application run. No need of external servers.<br/>


# Spring Boot architecture

## Core Components of Spring Boot

### Spring Boot Starters
> - Spring Boot Starters are dependency descriptors provided by Spring Boot to simplify setting up dependencies for different aspects of an application.<br/>
> - Each starter is a pre-defined set of dependencies for a specific use case or functionality, such as web development, testing, or data access.<br/>
> - They make it easier to start a new Spring project without manually adding multiple dependencies and worrying about version compatibility.<br/>
> - Spring Boot Starters are dependency descriptors that can be added under the <dependencies> section in pom.xml.<br/>

every is implemented like this:
```java
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-DEPENDENCYNAME</artifactId>
    </dependency>
</dependencies>
```
> here is some important dependencies:<br/>
> - **spring-boot-starter-web:** Used for building web, RESTful, and Spring MVC applications.<br/>
> - **spring-boot-starter-data-jpa:** Simplifies the setup for applications needing relational database access with JPA.<br/>
> - **spring-boot-starter-security:** Adds Spring Security support to the application.<br/>
> - **spring-boot-starter-test:** Provides dependencies for testing Spring applications.<br/>
> - **spring-boot-starter-thymeleaf:** Used for applications with server-side HTML rendering using Thymeleaf.<br/>
> - **spring-boot-starter-validation:** Provides support for bean validation with Hibernate Validator.<br/>
> - **spring-boot-starter-mail:** Used for email functionality within applications.<br/>

### Spring Boot Auto-configuration
> - Auto-configuration in Spring Boot is a feature that automatically configures the Spring application context based on the dependencies and settings in your project.<br/>

#### SpringBootApplication annotation
> It provides a main entry point with the SpringApplication.run(...) method, which launches the application.<br/>

The `@SpringBootApplication` annotation is a combination of three key annotations:

**@EnableAutoConfiguration:** 
> - Tells Spring Boot to start adding beans based on classpath settings, other beans, and various property settings.<br/>
> - Enables Spring Boot’s auto-configuration feature, which automatically configures Spring application components based on the dependencies found in the project.<br/>

**@ComponentScan:** 
> - Instructs Spring to scan for components, configurations, and services in the current package and all sub-packages.<br/>
> - Automatically detects Spring components (@Component, @Service, @Repository, @Controller, etc.) in the application and registers them as beans in the Spring context.<br/>

**@Configuration:**
> - Indicates that the class is a source of bean definitions.<br/>
> - Allows the class to define beans that will be managed by the Spring container, similar to using XML-based configuration files in traditional Spring applications.<br/>

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class MyApplication {
    public static void main(String[] args) {
        SpringApplication.run(MyApplication.class, args);
    }
}
```

### Spring Boot CLI
> - A command-line interface that lets you run and test Spring Boot applications with minimal configuration.<br/>
> - It’s particularly useful for prototyping and scripting.<br/>

### Spring Initializr
> - A web-based tool that helps to bootstrap a Spring Boot project with selected dependencies.<br/>
> - It generates the necessary project structure and configuration files.<br/>

## Layers of a Spring Boot Application
The spring boot consists of the following four layers:<br/>

### Presentation Layer
> – Presentation Layer-Authentication & Json Translation is the top layer of the spring boot architecture.<br/>
> - It consists of Views. i.e., the front-end part of the application.<br/>
> - It handles the HTTP requests and performs authentication.<br/>
> - It is responsible for converting the JSON field’s parameter to Java Objects and vice-versa.<br/>
> - Once it performs the authentication of the request it passes it to the next layer. i.e., the business layer.<br/>

### Business Layer
> - The business layer contains all the business logic.<br/>
> - It consists of services classes.<br/>
> - It is responsible for validation and authorization.<br/>

### Persistence Layer
> - The persistence layer contains all the database storage logic.<br/>
> - It is responsible for converting business objects to the database row and vice-versa.<br/>

### Database Layer
> - The database layer contains all the databases such as MySql, MongoDB, etc.<br/>
> - This layer can contain multiple databases.<br/>
> - It is responsible for performing the CRUD operations.<br/>

## Example of Spring Boot Architecture in Action

> 1- The Client makes an HTTP request(GET, PUT, POST, etc.)<br/>
> 2- The HTTP request is forwarded to the Controller. The controller maps the request. It processes the handles and calls the server logic.<br/>
> 3- The business logic is performed in the Service layer. The spring boot performs all the logic over the data of the database which is mapped to the spring boot model class through 
     Java Persistence Library(JPA).<br/>
> 4- The JSP page is returned as Response from the controller.<br/>

## Spring Boot project architecture

> - **java folder:** where is the Main Java Code. <br/>
> - **test folder:** Structure your tests similarly to your main codebase, Unit tests, integration tests, and other testing classes go in the src/test/java directory.<br/>
> - **ressources folder:** used to store configuration files, templates, static resources, and other non-code assets that are required by the application.<br/>
> - **pom.xml file:** is the configuration file used by Maven, the build tool for managing dependencies and the build lifecycle of the project.(yaml in gradle<br/>

# Introduction to RESTful Web Services
> - RESTful Web Services REST stands for REpresentational State Transfer.<br/>
> - It was developed by Roy Thomas Fielding, one of the principal authors of the web protocol HTTP.<br/>
> - Consequently, REST was an architectural approach designed to make the optimum use of HTTP protocol.<br/>
> - It uses the concepts and verbs already present in HTTP to develop web services.<br/>

## Important Methods of HTTP
### GET

