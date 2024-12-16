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
      - [ResponseEntity class](#ResponseEntity-class)
  - [Important Methods of HTTP](Important-Methods-of-HTTP)
    - [GET](#GET)
    - [PUT](#PUT)
    - [PATCH](#Patch)
    - [DELETE](#DELETE)
- [Spring Data](#Spring-Data)

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


## Important Annotations RESTful Web services

### Parameter Annotations

#### @PathVariable
> - Binds a method parameter to a URI template variable.<br/>
> - Used to capture dynamic parts of the URI.<br/>

```java
@GetMapping("/users/{id}")
public User getUserById(@PathVariable Long id) {
    return userService.getUserById(id);
}
// Explanation: In this example, {id} in the URL will be extracted and bound to the method parameter id.
// So, if the request URL is /users/123, the id parameter will receive the value 123.
```


```java
// If the path variable name in the URI is different from the method parameter name, you can specify the exact name to use with `@PathVariable("paramName")`.

@GetMapping("/users/{userId}")
public String getUserById(@PathVariable("userId") Long id) {
    return "User ID: " + id;
}
```

To make a path variable optional, you set `required = false`.<br/>
In this case, the variable will be optional, and you should provide a default value in the method if the variable is not present in the URL.<br/>
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
// **Explanation:** In this example, if the request URL is /users?status=active, the status parameter will be bound to "active".<br/>
```

```java
// When the query parameter name differs from the method parameter, specify the query parameter using value.
@GetMapping("/search")
public String search(@RequestParam(value = "q") String query) {
    return "Search query: " + query;
}

//Request URL: /search?q=spring
//Result: "Search query: spring"
//Here, the query parameter q in the URL binds to the query method parameter
```

**Optional Parameter with required = false** <br/>
Making a parameter optional allows for flexible endpoints.<<br/>
If the query parameter is absent, the method will not fail.<br/>
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

Specify a defaultValue to provide a fallback when the query parameter is missing. This is helpful to avoid null checks.<br/>
```java
@GetMapping("/search")
public String search(@RequestParam(value = "query", defaultValue = "default") String query) {
    return "Search query: " + query;
}
```

To accept multiple values for a query parameter, use List or Set as the parameter type.<br/>
Spring will automatically convert query parameters with the same name into a list or set.<br/>
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
// When a JSON request body is sent (e.g., { "name": "John", "email": "john@example.com" }),
// Spring automatically converts it into a User object and binds it to the user parameter.
```

```java
//When Required is false

public String createUser(@RequestBody(required = false) User user) {
    if (user == null) {
        return "No user data provided";
    }
    return "User created: " + user.getName();
}
```

```java
// **Required Fields and Validation:** Combine @RequestBody with validation annotations (e.g., @Valid) to ensure that the input data meets certain criteria.<br/>

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

You can use the `required attribute` to specify whether the header is mandatory and `defaultValue` to provide a default value if the header is missing.<br/>
```java
@GetMapping("/user")
    public String getUser(@RequestHeader(name = "Authorization", required = false, defaultValue = "No Authorization Token") String authorizationHeader) {
        return "Authorization header value: " + authorizationHeader;
    }
```

You can also use @RequestHeader to bind `multiple headers` in a method. This is useful when you need to extract several headers at once.<br/>
```java
@GetMapping("/user")
    public String getUser(@RequestHeader("Authorization") String authorizationHeader, 
                          @RequestHeader("User-Agent") String userAgent) {
        return "Authorization header: " + authorizationHeader + ", User-Agent: " + userAgent;
    }
```


### Response Annotations

#### @ResponseBody
Used to send the response directly as an object (often serialized as JSON or XML).<br/>
@RestController is a special convenience annotation that combines @Controller and @ResponseBody, so you don't need to explicitly annotate each method with @ResponseBody.<br/>

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
**Commun HTTP status code** <br/>

200 OK: When a resource is successfully fetched or updated.<br/>
201 Created: When a resource is successfully created.<br/>
204 No Content: When an operation succeeds but does not return data.<br/>
400 Bad Request: When the client sends invalid data.<br/>
401 Unauthorized: When the client is not authenticated.<br/>
403 Forbidden: When the client does not have permission.<br/>
404 Not Found: When the resource is not found.<br/>
500 Internal Server Error: For unhandled server errors.<br/>

#### ResponseEntity
ResponseEntity is a powerful class used for handling HTTP responses in a flexible and detailed way. It allows you to control the full HTTP response, including the status code, headers, and body, making it highly useful for RESTful web services. <br/>
The ResponseEntity class is a flexible way to define and customize HTTP responses, including: **HTTP status codes**, **Response headers**, **Response bodies** <br/>

```java
@RestController
@RequestMapping("/api")
public class UserController {

    @GetMapping("/users/{id}")
    public ResponseEntity<User> getUserById(@PathVariable Long id) {
        User user = userService.findById(id);

        if (user == null) {
            return ResponseEntity.status(HttpStatus.NOT_FOUND).body(null);
            // Returns an HTTP 404 Not Found response with an empty body.
        }

        return ResponseEntity.ok(user); 
        // Returns an HTTP 200 OK response with the user object in the body.
    }

    @PostMapping("/users")
    public ResponseEntity<User> createUser(@RequestBody User user) {
        User createdUser = userService.save(user);

        URI location = ServletUriComponentsBuilder.fromCurrentRequest()
            .path("/{id}")
            .buildAndExpand(createdUser.getId())
            .toUri();

        return ResponseEntity.created(location).body(createdUser);
        // Returns an HTTP 201 Created response with a Location header pointing to the new resource and the createdUser object in the body.
    }
}
```




## Important Methods of HTTP

### GET
Retrieve data from the server. Does not modify the resource.
**Usage:**
Fetch a list of resources: /users
Fetch a specific resource: /users/{id}

```java
@GetMapping("/users/{id}")
public User getUserById(@PathVariable Long id) {
    return userService.findById(id);
}
```

### POST
Create a new resource on the server. Not safe: It modifies server state. Often returns 201 Created.
**Usage:**
Create a new resource: /users

```java
@PostMapping("/users")
public ResponseEntity<User> createUser(@RequestBody User user) {
    User createdUser = userService.save(user);
    return ResponseEntity.status(HttpStatus.CREATED).body(createdUser);
}
```

#### PUT
Update or create a resource by replacing it entirely. Not safe: It modifies server state. Often returns 200 OK or 204 No Content.
**Usage:**
Update a specific resource: /users/{id}

```java
@PutMapping("/users/{id}")
public ResponseEntity<User> updateUser(@PathVariable Long id, @RequestBody User user) {
    userService.update(id, user);
    return ResponseEntity.ok(user);
}
```


#### PATCH
Partially update a resource. Not safe: It modifies server state. Often returns 200 OK or 204 No Content.
**Usage:**
Update a specific field of a resource: /users/{id}

```java
@PatchMapping("/users/{id}")
public ResponseEntity<User> partialUpdateUser(@PathVariable Long id, @RequestBody Map<String, Object> updates) {
    User updatedUser = userService.partialUpdate(id, updates);
    return ResponseEntity.ok(updatedUser);
}
```

#### DELETE
Delete a resource from the server. Not safe: It modifies server state. Often returns 204 No Content.
**Usage:**
Delete a specific resource: /users/{id}

```java
@DeleteMapping("/users/{id}")
public ResponseEntity<Void> deleteUser(@PathVariable Long id) {
    userService.delete(id);
    return ResponseEntity.noContent().build();
}
```

# Spring Data
Spring Data is a part of the larger Spring framework, focused on simplifying data access layers in applications. It provides powerful abstractions and implementations for working with various data sources, including relational databases, NoSQL databases, and other storage systems.<br/>


## Hibernate and JPA: Key Points

### What is JPA?
- JPA (Java Persistence API) is a standard specification for managing relational data in Java applications.<br/>
- It defines annotations like @Entity, @Table, relations between tables, and standardizes how to map Java objects to database tables.<br/>
```java
@Entity
public class Person {
    @Id
    private Long id;
    private String name;
}
```
```java
// to specify another name of the Entity in @Entity 
@Entity(name = "employees")
public class Employee {
    @Id
    private Long id;
    private String name;
}
```
```java
@Entity
// to specify the name of the tale in database, the schema, and email should be unique, otherwise, the database will declare an error 
@Table(name = "students", schema = "school", uniqueConstraints = @UniqueConstraint(columnNames = {"email"}))
public class Student {
    @Id
    private Long id;
    private String firstName;
    private String lastName;
    private String email;
}
```

- the @Column annotation is used to specify the details of a column in a relational database that corresponds to a field in an entity class.<br/>
```java
@Column(name = "column_name", nullable = false, unique = true, length = 100)
private String field;
```

### What is Hibernate?
- Hibernate is an ORM framework that implements the JPA specification.<br/>
- It provides additional features like caching, advanced queries, and support for database-specific functions.

### Relationship Between JPA and Hibernate:
- Hibernate is a JPA implementation. It uses JPA annotations and APIs but also offers proprietary extensions.<br/>
- If you use JPA without explicitly choosing an implementation, Hibernate is often the default.<br/>

### Spring Data JPA:
- Spring Data JPA is a library that simplifies working with JPA by providing tools like repositories and query derivation.<br/>
- When you add the spring-boot-starter-data-jpa dependency, Hibernate is automatically included as the default JPA provider.<br/>
- **Switching JPA Implementations:** Hibernate can be replaced with other JPA implementations (e.g., EclipseLink, OpenJPA) by excluding Hibernate and adding the desired provider.<br/>

### impedance mismatch 
- describes the difficulties when translating between object-oriented and relational models, and frameworks like Hibernate (JPA) aim to minimize these issues by automating much of the mapping between objects and tables. <br/>

### Summary: 
JPA is a standard, and Hibernate is one of its most popular implementations. In Spring Boot, adding Spring Data JPA automatically includes Hibernate as the JPA provider.<br/>

## Spring boot validation
- validation refers to the process of ensuring that the input data provided by users meets certain rules or constraints before being persisted, processed, or returned in an application.<br/>
- Spring Boot integrates with the Java Bean Validation API to provide a declarative and flexible approach to validating data.<br/>
- Spring Boot automatically enables the validation mechanism when you include the `spring-boot-starter-validation` dependency.

```java
<!-- Maven -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-validation</artifactId>
</dependency>
```

### Common Validation Annotations

**@NotNull**: Ensures the value is not null.wbr/>
```java
@NotNull(message = "Name must not be null")
private String name;
```

**@Size(min = 5, max = 20)**: Ensures the string length is between 5 and 20.<br/>
```java
@Size(min = 5, max = 20)
private String username;
```

**@Email**: Ensures the string is a valid email address.<br/>
```java
@Email(message = "Email should be valid")
private String email;
```

**@Min and @Max**: Ensures a number is within a specific range.<br/>
```java
@Min(18)
@Max(100)
private int age;
```

**@NotBlank**: Ensures the string is not empty or null.<br/>
```java
@NotBlank(message = "Password cannot be blank")
private String password;
```

```java
@PostMapping("/create")
  public String createUser(@Valid @RequestBody User user) {
    userService.save(user);
    return "User created successfully!";
}
```

## Key Features of Spring Data

### Repository Abstractions
- Jpa provides CrudRepository, JpaRepository, and other repository interfaces to simplify CRUD (Create, Read, Update, Delete) operations. <br/>
- The JpaRepository implements indirectly the CrudRepository.<br/>
```java
public interface UserRepository extends JpaRepository<T, ID type> {...}
// where T is the type of the object, and the ID type is the type of the id of the object.
```


### Custom Query Methods

#### Derived Queries:
- Automatically generates queries based on method names (e.g., findByFirstName).<br/>
```java
public interface UserRepository extends JpaRepository<User, Long> {
    // Custom query methods
    List<User> findByLastName(String lastName);
    // the implementation is :
        //return entityManager.createQuery("select u from User u where u.lastName = :lastName", User.class)
          .setParameter("lastName", lastName) .getSingleResult();
}
```

#### Custom JPQL Queries:
- Supports JPQL queries.<br/>
- JPQL (Java Persistence Query Language): Standardized, portable, and works across all JPA implementations.<br/>

**With param** <br/>
```java
@Query("SELECT u FROM User u WHERE u.lastName = :lastName")
List<User> findUsersByLastName(@Param("lastName") String lastName);
```
**With JOIN:** <br/>
```java
public interface EmployeeRepository extends JpaRepository<Employee, Long> {
    @Query("SELECT e FROM Employee e JOIN e.department d WHERE d.name = :departmentName")
    List<Employee> findEmployeesByDepartmentName(@Param("departmentName") String departmentName);
}
```

**Native SQL Queries:** <br/>
- Supports also native SQL queries.<br/>
```java
@Query(value = "SELECT * FROM user WHERE last_name = ?1", nativeQuery = true)
List<User> findUsersByLastNameNative(String lastName);
```

#### Using JPQL or SQL?
**Using JPQL:** <br/>
- When you need database independence and portability for your application. <br>
- if we change the name of the table, we don't need to change the names in the queries. <br/>

## relationships between database tables

### One-to-One Relationship
Each record in Table A relates to exactly one record in Table B, and vice versa.

**Example:** <br/>
User table has a one-to-one relationship with the Profile table.
```java
@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    @OneToOne
    @JoinColumn(name = "profile_id", referencedColumnName = "id")
    private Profile profile;

    // @OneToOne: Defines the one-to-one relationship.
    // @JoinColumn: Specifies the foreign key column (profile_id in User). By default it's profile_id, we could not use JoinColumn annotation here
    // referencedColumnName specifies the column in the other table being referenced (id in Profile)
}
```

**Bidirectional Relationship** <br/>
If you need a reference to User in the Profile entity:
```java
@Entity
public class Profile {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String bio;

    @OneToOne(mappedBy = "profile")
    private User user;

    // mappedBy: Indicates the profile field in User owns the relationship.
}
```

### One-to-Many Relationship
A record in Table A can relate to multiple records in Table B. The reverse is a Many-to-One relationship. <br/>

Example:
A Department has many Employees.
```java
@Entity
public class Department {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    @OneToMany(mappedBy = "department")
    private List<Employee> employees = new ArrayList<>();

    // 
}
```
```java
@Entity
public class Employee {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    @ManyToOne
    @JoinColumn(name = "department_id", referencedColumnName = "id")
    private Department department;

    // ManyToOne: Used on the child entity to define the owning side.
}
```

### Many-to-Many Relationship
A record in Table A can relate to multiple records in Table B, and vice versa.

**Example:** <br/>
A Student can enroll in many Courses, and a Course can have many Students.
```java
@Entity
public class Student {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    @ManyToMany
    @JoinTable(
        name = "student_course",
        joinColumns = @JoinColumn(name = "student_id"),
        inverseJoinColumns = @JoinColumn(name = "course_id")
    )
    private List<Course> courses = new ArrayList<>();

    // @ManyToMany: Declares a many-to-many relationship.
    // @JoinTable: Specifies the join table name student_course that maps the relationship.
    // joinColumns: Defines the join column name for the owning entity (student_id).
    // inverseJoinColumns: Defines the join column name for the inverse entity (course_id).
}
```

```java
@Entity
public class Course {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String title;

    @ManyToMany(mappedBy = "courses")
    private List<Student> students = new ArrayList<>();

    // Getters and setters
}
```

### Cascade Types
`ALL`: Propagates all operations (persist, remove, merge, etc.).<br/>
`PERSIST`: Saves child entities when the parent is saved.<br/>
`REMOVE`: Deletes child entities when the parent is deleted.<br/>
`MERGE`: Merges changes of the child entities when the parent is merged.<br/>
`REFRESH`: Refreshes child entities when the parent is refreshed.<br/>
`DETACH`: Detaches child entities when the parent is detached.<br/>
**Declaration:**
```java
@OneToMany(cascade = CascadeType.PERSIST)
```

###  Fetch Types
Fetch types determine how related entities are loaded:<br/>

`EAGER`: Related entities are fetched immediately with the parent. By default for `@OneToOne` and `@ManyToOne`.<br/>
`LAZY`: Related entities are fetched on demand. By default for `@OneToMany` et `@ManyToMany`.<br/>
**Declaration:**
```java
@ManyToOne(fetch = FetchType.LAZY)
```









