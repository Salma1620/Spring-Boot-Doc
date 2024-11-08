# Spring-Boot-Doc

# Table of content
- [Introduction](#Introduction)
  - [Diffrence between Spring and Spring boot](#Diffrence-between-Spring-and-Spring-boot)
  - [the advantages of using Spring Boot](#the-advantages-of-using-Spring-Boot)
  

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










