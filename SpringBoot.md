## Spring Boot developer interview questions:

### Basic Questions

1. **What is Spring Boot, and how is it different from the Spring Framework?**
   - **Response**: Spring Boot is an extension of the Spring Framework that simplifies the setup and development of new Spring applications. It provides defaults for code and annotation configuration to drastically reduce the setup time.
   - **Example**: Unlike the Spring Framework which requires extensive configuration, Spring Boot uses `@SpringBootApplication` to auto-configure most of the application.

2. **What are the advantages of using Spring Boot?**
   - **Response**: Spring Boot offers rapid application development with minimal configuration, embedded servers, auto-configuration, production-ready features like metrics and health checks, and an opinionated approach to configuration.

3. **How do you create a Spring Boot application?**
   - **Response**: You can create a Spring Boot application using Spring Initializr, IDEs, or manually by adding dependencies to your `pom.xml` or `build.gradle` file.
   - **Example**: 
     ```java
     @SpringBootApplication
     public class MyApplication {
         public static void main(String[] args) {
             SpringApplication.run(MyApplication.class, args);
         }
     }
     ```

4. **What is a Spring Boot starter?**
   - **Response**: A Spring Boot starter is a set of convenient dependency descriptors you can include in your application. For example, `spring-boot-starter-web` includes all dependencies to create a web application.

5. **What are Spring Boot starters and why are they useful?**
   - **Response**: Spring Boot starters simplify dependency management by providing a comprehensive list of libraries needed for a specific function, such as web development or JPA.
   - **Example**: Adding `spring-boot-starter-web` to your project includes dependencies like Spring MVC, Jackson, and embedded Tomcat.

6. **Explain the concept of auto-configuration in Spring Boot.**
   - **Response**: Auto-configuration in Spring Boot attempts to automatically configure your Spring application based on the jar dependencies you have added. It reduces the need for manual configurations.

7. **How do you define properties in a Spring Boot application?**
   - **Response**: Properties can be defined in `application.properties` or `application.yml` files in the `src/main/resources` directory.
   - **Example**: `application.properties`
     ```properties
     server.port=8080
     spring.datasource.url=jdbc:mysql://localhost:3306/mydb
     ```

8. **What is `application.properties` or `application.yml` in Spring Boot?**
   - **Response**: These files are used to define configuration properties for your Spring Boot application. They allow you to externalize configuration so that you can easily change settings without modifying code.

9. **What are profiles in Spring Boot?**
   - **Response**: Profiles allow you to segregate parts of your application configuration and make it available only in certain environments. For example, you can have different properties for development and production environments.
   - **Example**: `application-dev.properties`, `application-prod.properties`.

10. **How do you implement exception handling in Spring Boot?**
    - **Response**: Exception handling in Spring Boot can be implemented using `@ControllerAdvice` and `@ExceptionHandler`.
    - **Example**: 
      ```java
      @ControllerAdvice
      public class GlobalExceptionHandler {
          @ExceptionHandler(Exception.class)
          public ResponseEntity<String> handleException(Exception e) {
              return new ResponseEntity<>(e.getMessage(), HttpStatus.INTERNAL_SERVER_ERROR);
          }
      }
      ```

### Configuration and Setup

11. **How do you configure a DataSource in Spring Boot?**
    - **Response**: You can configure a DataSource by specifying properties in `application.properties` or `application.yml`.
    - **Example**:
      ```properties
      spring.datasource.url=jdbc:mysql://localhost:3306/mydb
      spring.datasource.username=root
      spring.datasource.password=password
      ```

12. **What are the different ways to configure Spring Boot properties?**
    - **Response**: Properties can be configured using `application.properties` or `application.yml`, command-line arguments, environment variables, and custom configuration files.

13. **How can you enable HTTPS in a Spring Boot application?**
    - **Response**: HTTPS can be enabled by configuring the keystore in `application.properties`.
    - **Example**:
      ```properties
      server.port=8443
      server.ssl.key-store=classpath:keystore.p12
      server.ssl.key-store-password=changeit
      server.ssl.keyStoreType=PKCS12
      server.ssl.keyAlias=tomcat
      ```

14. **How do you configure logging in Spring Boot?**
    - **Response**: Logging in Spring Boot can be configured using `application.properties` or `logback.xml`.
    - **Example**:
      ```properties
      logging.level.org.springframework=DEBUG
      logging.file.name=app.log
      ```

15. **What is `@SpringBootApplication` annotation?**
    - **Response**: `@SpringBootApplication` is a convenience annotation that combines `@Configuration`, `@EnableAutoConfiguration`, and `@ComponentScan`.

16. **What is the purpose of `@EnableAutoConfiguration` annotation?**
    - **Response**: `@EnableAutoConfiguration` tells Spring Boot to start adding beans based on classpath settings, other beans, and various property settings.

17. **How do you externalize configuration in Spring Boot?**
    - **Response**: Configuration can be externalized using properties files, YAML files, environment variables, and command-line arguments.

18. **What is a `CommandLineRunner` in Spring Boot?**
    - **Response**: `CommandLineRunner` is an interface used to execute code after the Spring Boot application has started.
    - **Example**:
      ```java
      @SpringBootApplication
      public class MyApplication implements CommandLineRunner {
          public static void main(String[] args) {
              SpringApplication.run(MyApplication.class, args);
          }

          @Override
          public void run(String... args) throws Exception {
              System.out.println("Application started!");
          }
      }
      ```

19. **How do you configure multiple data sources in Spring Boot?**
    - **Response**: Multiple data sources can be configured by defining multiple `DataSource` beans and using `@Primary` for the main data source.
    - **Example**:
      ```java
      @Bean(name = "dataSource1")
      @ConfigurationProperties(prefix = "spring.datasource1")
      public DataSource dataSource1() {
          return DataSourceBuilder.create().build();
      }

      @Primary
      @Bean(name = "dataSource2")
      @ConfigurationProperties(prefix = "spring.datasource2")
      public DataSource dataSource2() {
          return DataSourceBuilder.create().build();
      }
      ```

20. **What is the difference between `application.properties` and `bootstrap.properties`?**
    - **Response**: `bootstrap.properties` is used for setting up the context, particularly for initializing Spring Cloud Config, while `application.properties` is used for application-specific configurations.

### Dependency Injection and Beans

21. **What is dependency injection in Spring Boot?**
    - **Response**: Dependency injection is a design pattern in which an object receives other objects it depends on. In Spring Boot, it is handled by the Spring container.

22. **What are Spring Beans, and how are they managed in Spring Boot?**
    - **Response**: Spring Beans are objects managed by the Spring container. They are instantiated, configured, and wired by Spring.

23. **How do you define a Spring Bean?**
    - **Response**: Beans can be defined using `@Component`, `@Service`, `@Repository`, or `@Bean` annotations.
    - **Example**:
      ```java
      @Component
      public class MyComponent {
          // Bean definition
      }

      @Bean
      public MyBean myBean() {
          return new MyBean();
      }
      ```

24. **What is the role of the `@Autowired` annotation?**
    - **Response**: `@Autowired` is used to automatically inject dependencies into a Spring Bean.
    - **Example**:
      ```java
      @Component
      public class MyComponent {
          private final MyService myService;

          @Autowired
          public MyComponent(MyService myService) {
              this.myService = myService;
          }
      }
      ```

25. **How do you create a custom Spring Boot starter?**
    - **Response**: A custom Spring Boot starter involves creating a library project with necessary dependencies and providing auto-configuration classes.
    - **Example**: 
      ```java
      @Configuration
      @ConditionalOnClass(MyService.class)
      public class MyServiceAutoConfiguration {
          @Bean
          public MyService myService() {
              return new MyService();
          }
      }
      ```

26. **What is the difference between `@Component`, `@Service`, `@Repository`, and `@Controller`?**
    - **Response**: `@Component` is a generic stereotype for any Spring-managed component. `@Service` indicates a service layer component. `@Repository` indicates a data access component. `@Controller` indicates a web controller.

27. **How do you create a custom annotation in Spring Boot?**
    - **Response**: Custom annotations can be created using `@interface`.
    - **Example**:
      ```java
      @Target(ElementType.METHOD)
      @Retention(RetentionPolicy.RUNTIME)
      public @interface MyCustomAnnotation {
          String value();
      }
      ```

28. **What is the use of `@Configuration` annotation?**
    - **Response**: `@Configuration` indicates that a class declares one or more `@Bean` methods and can be processed by the Spring container to generate bean definitions.

29. **How do you use `@Bean` annotation?**
    - **Response**: `@Bean` is used to indicate that a method produces a bean to be managed by the Spring container.
    - **Example**:
      ```java
      @Configuration
      public class AppConfig {
          @Bean
          public MyService myService() {
              return new MyServiceImpl();
          }
      }
      ```

30. **Explain the difference between `@Primary` and `@Qualifier` annotations.**
    - **Response**: `@Primary` is used to give a bean preference when multiple beans of the same type exist. `@Qualifier` is used to specify which bean should be injected when multiple candidates are present.

### REST and Web Development

31. **How do you create a RESTful web service in Spring Boot?**
    - **Response**: By using `@RestController` and `@RequestMapping` annotations.
    - **Example**:
      ```java
      @RestController
      @RequestMapping("/api")
      public class MyController {
          @GetMapping("/greeting")
          public String greeting() {
              return "Hello, World!";
          }
      }
      ```

32. **What is `@RestController` annotation?**
    - **Response**: `@RestController` is a convenience annotation that combines `@Controller` and `@ResponseBody`. It eliminates the need to annotate each method with `@ResponseBody`.

33. **What are the HTTP methods supported by Spring Boot?**
    - **Response**: Spring Boot supports GET, POST, PUT, DELETE, PATCH, OPTIONS, and HEAD methods.

34. **How do you handle exceptions in a Spring Boot RESTful service?**
    - **Response**: Exceptions can be handled using `@ControllerAdvice` and `@ExceptionHandler`.
    - **Example**:
      ```java
      @ControllerAdvice
      public class GlobalExceptionHandler {
          @ExceptionHandler(ResourceNotFoundException.class)
          public ResponseEntity<String> handleResourceNotFound(ResourceNotFoundException ex) {
              return new ResponseEntity<>(ex.getMessage(), HttpStatus.NOT_FOUND);
          }
      }
      ```

35. **What is the difference between `@RequestBody` and `@ResponseBody`?**
    - **Response**: `@RequestBody` is used to bind the request body to a method parameter, whereas `@ResponseBody` is used to bind a method return value to the response body.

36. **How do you validate a request in Spring Boot?**
    - **Response**: By using `@Valid` or `@Validated` annotations along with `@RequestBody`.
    - **Example**:
      ```java
      @PostMapping("/user")
      public ResponseEntity<User> createUser(@Valid @RequestBody User user) {
          // save user
          return ResponseEntity.ok(user);
      }
      ```

37. **What is `@PathVariable` annotation?**
    - **Response**: `@PathVariable` is used to extract values from the URI template.
    - **Example**:
      ```java
      @GetMapping("/users/{id}")
      public ResponseEntity<User> getUserById(@PathVariable Long id) {
          User user = userService.findById(id);
          return ResponseEntity.ok(user);
      }
      ```

38. **What is `@RequestParam` annotation?**
    - **Response**: `@RequestParam` is used to extract query parameters from the request.
    - **Example**:
      ```java
      @GetMapping("/search")
      public ResponseEntity<List<User>> searchUsers(@RequestParam String name) {
          List<User> users = userService.findByName(name);
          return ResponseEntity.ok(users);
      }
      ```

39. **How do you implement pagination in Spring Boot?**
    - **Response**: Pagination can be implemented using `Pageable` and `Page` interfaces from Spring Data.
    - **Example**:
      ```java
      @GetMapping("/users")
      public Page<User> getUsers(Pageable pageable) {
          return userRepository.findAll(pageable);
      }
      ```

40. **How do you handle CORS in Spring Boot?**
    - **Response**: CORS can be handled using `@CrossOrigin` annotation or by configuring `WebMvcConfigurer`.
    - **Example**:
      ```java
      @RestController
      @CrossOrigin(origins = "http://example.com")
      @RequestMapping("/api")
      public class MyController {
          @GetMapping("/data")
          public ResponseEntity<String> getData() {
              return ResponseEntity.ok("Data");
          }
      }
      ```


### Spring Data and JPA

41. **What is Spring Data JPA?**
42. **How do you configure JPA in Spring Boot?**
43. **What is a repository in Spring Data JPA?**
44. **What is the difference between `CrudRepository`, `JpaRepository`, and `PagingAndSortingRepository`?**
45. **How do you define a custom query in Spring Data JPA?**
46. **What is the purpose of the `@Query` annotation?**
47. **How do you handle transactions in Spring Boot?**
48. **What is the role of the `@Entity` annotation?**
49. **What is the difference between `@Table` and `@Entity`?**
50. **How do you perform CRUD operations in Spring Data JPA?**

### Security

51. **What is Spring Security, and how does it integrate with Spring Boot?**
52. **How do you secure a Spring Boot application?**
53. **What is `@EnableWebSecurity` annotation?**
54. **How do you implement OAuth2 in Spring Boot?**
55. **How do you handle authentication and authorization in Spring Boot?**
56. **What is the role of the `SecurityConfigurerAdapter` class?**
57. **How do you implement JWT authentication in Spring Boot?**
58. **How do you configure CORS in Spring Security?**
59. **What are security filters in Spring Boot?**
60. **How do you encrypt passwords in Spring Boot?**

### Testing

61. **How do you write unit tests in Spring Boot?**
62. **What is the role of `@SpringBootTest` annotation?**
63. **How do you test RESTful web services in Spring Boot?**
64. **What is the use of `MockMvc` in Spring Boot testing?**
65. **How do you perform integration testing in Spring Boot?**
66. **What are `@MockBean` and `@SpyBean` annotations?**
67. **How do you test a Spring Data JPA repository?**
68. **How do you test Spring Boot services?**
69. **What is `@DataJpaTest` annotation?**
70. **How do you write a test for a Spring Boot controller?**

### Microservices and Cloud

71. **What is Spring Cloud, and how does it relate to Spring Boot?**
72. **How do you create a microservice using Spring Boot?**
73. **What is service discovery, and how do you implement it in Spring Boot?**
74. **What is the role of Eureka in Spring Cloud?**
75. **How do you configure load balancing in Spring Boot?**
76. **What is Spring Cloud Config?**
77. **How do you handle distributed tracing in Spring Boot?**
78. **What is the use of Spring Cloud Gateway?**
79. **How do you implement API Gateway in Spring Boot?**
80. **What is Hystrix, and how does it work in Spring Boot?**

### Miscellaneous

81. **What are the key components of a Spring Boot application?**
82. **How does Spring Boot handle application properties and configuration?**
83. **What are actuators in Spring Boot, and why are they important?**
84. **How do you monitor a Spring Boot application?**
85. **What is Spring Boot Admin?**
86. **What is the role of `@SpringBootApplication` annotation?**
87. **How do you deploy a Spring Boot application?**
88. **What are the different ways to package a Spring Boot application?**
89. **What is the role of `SpringApplication` class?**
90. **How do you handle application migrations in Spring Boot?**

### Advanced Topics

91. **What is Spring Boot DevTools, and how do you use it?**
92. **How do you handle versioning in a Spring Boot REST API?**
93. **What are the common pitfalls in Spring Boot development?**
94. **How do you optimize the performance of a Spring Boot application?**
95. **What are the best practices for Spring Boot development?**
96. **How do you use `Liquibase` or `Flyway` with Spring Boot?**
97. **How do you configure caching in Spring Boot?**
98. **What is `Spring Session`, and how do you use it?**
99. **How do you handle file uploads in Spring Boot?**
100. **What are the new features introduced in the latest versions of Spring Boot?**
