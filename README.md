# A little bit of fresh air for Java Web development

This is a sample project showing how simple it is to implement an AngularJS application using Spring Boot as a backend, and Bootstrap as a CSS framework.
It is freely inspired from the ASP.NET Web API example built by Mathieu and available here: https://github.com/mathieubrun/Samples.AngularBootstrapWebApi

## Build and run
Package and run as standalone application:

    $ mvn clean package
    $ java -jar target/AngularBootstrapSpringBoot-0.1.0.jar

Run inplace and leverage on hot reloading of resources for frontend development:

    $ mvn spring-boot:run

## Configure
Configure application in application.properties in resources folder (in classpath). This file can be overridden with
a copy and specific properties in current dir, config folder in classpath or config folder under current dir. It also supports
Spring environment profiles.
More info in [spring-boot readme](http://projects.spring.io/spring-boot/docs/spring-boot/README.html#toc_6).

### Nice to have properties
- Disable thymleaf cache to allow hot reloading of changes in templates:

    spring.thymeleaf.cache = false

## TODOs
* using webjars instead of static files
* thymlead example page
* unit and integration tests
* tomcat 8
* spring-boot-starter
* enable csrf (find a good way to include token in angularjs requests)

## Tips

### Java 8

#### List of new features
* Mostly lambdas and everything around this (interfaces improvements, functions, streams, enhancement of collection and nio apis)
* New date & time API
* Nashorn JavaScript engine
* Guava inspired stuff like Optional (yes I know), StringJoiner, Comparator chain
* See here for a good overview: http://www.techempower.com/blog/2013/03/26/everything-about-java-8/

#### Set maven compiler
    <plugin>
        <artifactId>maven-compiler-plugin</artifactId>
        <configuration>
            <source>1.8</source>
            <target>1.8</target>
        </configuration>
    </plugin>

#### Lambdas of course...
* See some examples in code
* Read Java 8 in Action: http://www.manning.com/urma/

#### Date & time API
* The official stuff: https://jcp.org/en/jsr/detail?id=310
* A nice overview: http://www.javacodegeeks.com/2014/03/a-deeper-look-into-the-java-8-date-and-time-api.html
* Jackson support already available: https://github.com/FasterXML/jackson-datatype-jsr310
** Customize ObjectMapper in spring boot to register JSR310 module: https://github.com/spring-projects/spring-boot/blob/master/docs/howto.md#customize-the-jackson-objectmapper

#### java.util.Objects
* Compare and equality on nullable objects
* Use it to build equals and hashCode methods

### Spring Boot
* [Official site and documentation]http://projects.spring.io/spring-boot/
* [Presentation by Dave Syer, one author]http://presos.dsyer.com/decks/spring-boot-intro.html
* [Spring MVC]http://docs.spring.io/spring/docs/current/spring-framework-reference/html/spring-web.html

#### @RestController
Same as @Controller and @ResponseBody

#### Actuators
* http://projects.spring.io/spring-boot/docs/spring-boot-actuator/docs/Features.html
* Add Maven dependency spring-boot-starter-actuator
* management.port = 8081
* http://localhost:8081/configprops

#### Data validation
* Enabled automatically if hibernate-validator in the classpath (see in pom)
* @Valid on controller inputs

#### Security
* See WebSecurityConfig

### Thymleaf
* Java XML / XHTML / HTML5 template engine
* http://www.thymeleaf.org/
* Integration with SpringMVC
* Provide an elegant and well-formed way of creating templates that can be correctly displayed by browsers and therefore work also as static prototypes

#### Script inlining
* http://www.thymeleaf.org/doc/html/Using-Thymeleaf.html#script-inlining-javascript-and-dart
* Allows to integrate server side data in javascript
* Supports JS and Dart
* Intelligent evaluation (object are transformed to JSON)
