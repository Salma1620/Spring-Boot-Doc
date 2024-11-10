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
- [Introduction to RESTful Web Services](#Introduction-to-RESTful-Web-Services)
  - [Important Annotations RESTful Web services](#Important-Annotations-RESTful-Web-services)
    - [Parameter Annotations](#Parameter-Annotations)
      - [@PathVariable](#@PathVariable)
      - [@RequestParam](#@RequestParam)
      - [@RequestBody](#@RequestBody)
      - [@RequestHeader](#@RequestHeader)
    - [Response Annotations](#Response-Annotations)
      - [@ResponseBody](#@ResponseBody)
      - [@ResponseStatus](#@ResponseStatus)
      - 

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

### Important Annotations RESTful Web services


### Parameter Annotations

#### @PathVariable
> - Binds a method parameter to a URI template variable.<br/>
> - Used to capture dynamic parts of the URI.<br/>
```java
@GetMapping("/users/{id}")
public User getUserById(@PathVariable Long id) {
    return userService.getUserById(id);
}
```
> - **Explanation:** In this example, {id} in the URL will be extracted and bound to the method parameter id. So, if the request URL is /users/123, the id parameter will receive the value 123.<br/>

> If the path variable name in the URI is different from the method parameter name, you can specify the exact name to use with `@PathVariable("paramName")`.<br/>
```java
@GetMapping("/users/{userId}")
public String getUserById(@PathVariable("userId") Long id) {
    return "User ID: " + id;
}
```

> - To make a path variable optional, you set `required = false`.<br/>
> - In this case, the variable will be optional, and you should provide a default value in the method if the variable is not present in the URL.<br/>
```java
@GetMapping(value = {"/users/{id}", "/users"})
public String getUserById(@PathVariable(value = "id", required = false) Long id) {
    if (id == null) {
        return "All users";
    }
    return "User ID: " + id;
}
```
#### @RequestParam
> - Extracts query parameters from the URL.<br/>
> - Useful for optional or filtering parameters.<br/>
```java
@GetMapping("/users")
public List<User> getUsersByStatus(@RequestParam String status) {
    return userService.getUsersByStatus(status);
}
```
> **Explanation:** In this example, if the request URL is /users?status=active, the status parameter will be bound to "active".<br/>

> When the query parameter name differs from the method parameter, specify the query parameter using value.<br/>
```java
@GetMapping("/search")
public String search(@RequestParam(value = "q") String query) {
    return "Search query: " + query;
}

//Request URL: /search?q=spring
//Result: "Search query: spring"
//Here, the query parameter q in the URL binds to the query method parameter
```

> Optional Parameter with required = false<br/>
> - Making a parameter optional allows for flexible endpoints.<<br/>
> - If the query parameter is absent, the method will not fail.<br/>
```java
@GetMapping("/search")
public String search(@RequestParam(value = "query", required = false) String query) {
    return query != null ? "Search query: " + query : "No query provided";
}
//Request URL: /search?query=spring
//Result: "Search query: spring"
//Request URL: /search
//Result: "No query provided"
```

> Specify a defaultValue to provide a fallback when the query parameter is missing. This is helpful to avoid null checks.<br/>
```java
@GetMapping("/search")
public String search(@RequestParam(value = "query", defaultValue = "default") String query) {
    return "Search query: " + query;
}
```

> - To accept multiple values for a query parameter, use List or Set as the parameter type.<br/>
> - Spring will automatically convert query parameters with the same name into a list or set.<br/>
```java
@GetMapping("/filter")
public String filter(@RequestParam List<String> categories) {
    return "Categories: " + String.join(", ", categories);
}
//Request URL: /filter?categories=sports&categories=music&categories=tech
//Result: "Categories: sports, music, tech"
```

#### @RequestBody
> - Maps the HTTP request body to a Java object, typically used in POST and PUT requests.<br/>
> - Automatically deserializes JSON into a Java object.<br/>
```java
@PostMapping("/users")
public User createUser(@RequestBody User user) {
    return userService.saveUser(user);
}
```
> **Explanation:** When a JSON request body is sent (e.g., { "name": "John", "email": "john@example.com" }), Spring automatically converts it into a User object and binds it to the user parameter.<br/>

> When Required is false<br/>
```java
public String createUser(@RequestBody(required = false) User user) {
    if (user == null) {
        return "No user data provided";
    }
    return "User created: " + user.getName();
}
```
> **Required Fields and Validation:** Combine @RequestBody with validation annotations (e.g., @Valid) to ensure that the input data meets certain criteria.<br/>
```java
@PostMapping("/create")
public ResponseEntity<String> createUser(@Valid @RequestBody User user) {
    return ResponseEntity.ok("User created: " + user.getName());
}
```

#### @RequestHeader
> - Binds a method parameter to a request header.<br/>
> - Useful for retrieving custom headers, like authorization tokens.<br/>
```java
@GetMapping("/users")
public User getUserByToken(@RequestHeader("Authorization") String token) {
    return userService.getUserByToken(token);
}
```

> You can use the `required attribute` to specify whether the header is mandatory and `defaultValue` to provide a default value if the header is missing.<br/>
```java
@GetMapping("/user")
    public String getUser(@RequestHeader(name = "Authorization", required = false, defaultValue = "No Authorization Token") String authorizationHeader) {
        return "Authorization header value: " + authorizationHeader;
    }
```

> You can also use @RequestHeader to bind `multiple headers` in a method. This is useful when you need to extract several headers at once.<br/>
```java
@GetMapping("/user")
    public String getUser(@RequestHeader("Authorization") String authorizationHeader, 
                          @RequestHeader("User-Agent") String userAgent) {
        return "Authorization header: " + authorizationHeader + ", User-Agent: " + userAgent;
    }
```


### Response Annotations

#### @ResponseBody
> - Used to send the response directly as an object (often serialized as JSON or XML).<br/>
> -  @RestController is a special convenience annotation that combines @Controller and @ResponseBody, so you don't need to explicitly annotate each method with @ResponseBody.<br/>
> - 
```java
@ResponseBody
@GetMapping("/users/{id}")
public User getUser(@PathVariable Long id) {
    return userService.getUserById(id);
}
```

#### @ResponseStatus
When you annotate a method with @ResponseStatus, you specify the HTTP status code to be returned when that method is invoked. This is helpful when you want to indicate that a specific operation has completed successfully or failed.
```java
 @PostMapping("/users")
    @ResponseStatus(HttpStatus.CREATED)  // 201 status code for successful resource creation
    public User createUser(@RequestBody User user) {
        // Logic to save user
        return user;  // The response will have status 201 Created
    }
```

One of the common use cases of @ResponseStatus is in exception handling. You can create custom exceptions and annotate them with @ResponseStatus to return a specific HTTP status code when that exception is thrown.
```java
@ResponseStatus(value = HttpStatus.NOT_FOUND, reason = "User not found")
public class UserNotFoundException extends RuntimeException {
    public UserNotFoundException(String message) {
        super(message);
    }
}
```

#### ResponseEntity

> - ResponseEntity is a powerful class used for handling HTTP responses in a flexible and detailed way. It allows you to control the full HTTP response, including the status code, headers, and body, making it highly useful for RESTful web services.







### GET

