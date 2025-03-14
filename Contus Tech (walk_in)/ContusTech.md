# *Contus Tech walk-in interview* 
# First Round
## Assessment - Spring Boot Application

# Technical Round
## Java Questions

### 1. What is the purpose of the `intern` method in Java?
   - The `intern` method ensures that all instances of a string with the same content share the same memory location. It returns a canonical representation of the string, which is useful for memory optimization and string comparison.

### 2. Explain the internal working process of `HashMap`.
   - `HashMap` uses a hash table to store key-value pairs. It calculates a hash code for each key and uses it to determine the index in an internal array. Collisions are handled using linked lists or balanced trees. When the load factor exceeds a threshold, the map is resized and rehashed.

### 3. What is the difference between mutable and immutable objects?
   - Mutable objects can be changed after they are created (e.g., `ArrayList`). Immutable objects cannot be changed after creation (e.g., `String`).

### 4. Why is `String` immutable in Java?
   - `String` is immutable for security, synchronization, and performance reasons. Immutable objects are inherently thread-safe and allow the reuse of string literals.

### 5. How can you create a mutable `String`?
   - Use `StringBuilder` or `StringBuffer`, which are mutable versions of `String`.
     ```java
     StringBuilder sb = new StringBuilder("Hello");
     sb.append(" World");
     String result = sb.toString(); // "Hello World"
     ```

### 6. What is a marker interface?
   - A marker interface is an interface with no methods or fields. It is used to indicate or mark a class for a specific purpose (e.g., `Serializable`, `Cloneable`).

### 7. What is a functional interface?
   - A functional interface has exactly one abstract method and may have multiple default or static methods. It is used as a target for lambda expressions and method references.
     ```java
     @FunctionalInterface
     public interface MyFunctionalInterface {
         void doSomething();
     }
     ```

### 8. What happens if a class contains two methods with the same name?
   - If the methods have different parameter lists, it is method overloading. If the methods have the same parameter list, it causes a compilation error.

### 9. What is a default method in Java?
   - A default method in an interface provides a default implementation. It allows you to add new methods to interfaces without breaking existing implementations.
     ```java
     public interface MyInterface {
         default void defaultMethod() {
             System.out.println("Default method");
         }
     }
     ```

### 10. How can we access an instance variable inside a static method? (Code)
  - Instance variables cannot be accessed directly from static methods. You need to create an instance of the class to access them.
      ```java
      public class MyClass {
          private int instanceVar = 10;

          public static void staticMethod() {
              MyClass obj = new MyClass();
              System.out.println(obj.instanceVar);
          }
      }
      ```

### 11. Explain the concept of a linked list
  - A linked list is a data structure where each element (node) contains a reference to the next node. It allows efficient insertion and deletion operations.

### 12. What is the difference between `LinkedList` and `ArrayList` in Java?
  - `ArrayList` is backed by a dynamic array, providing O(1) time complexity for access but O(n) for insertions and deletions. `LinkedList` is backed by a doubly linked list, providing O(1) time complexity for insertions and deletions but O(n) for access.

---

## Spring Boot Questions

### 1. How to use two different databases in a single Spring Boot project?
   - Configure multiple `DataSource` beans and specify the database details in `application.properties` or `application.yml`. Use `@Primary` annotation to mark the default `DataSource`. 
     ```java
     @Bean
     @Primary
     @ConfigurationProperties(prefix = "spring.datasource.primary")
     public DataSource primaryDataSource() {
         return DataSourceBuilder.create().build();
     }

     @Bean
     @ConfigurationProperties(prefix = "spring.datasource.secondary")
     public DataSource secondaryDataSource() {
         return DataSourceBuilder.create().build();
     }
     ```

### 2. How to handle exceptions in Spring Boot?
   - Use `@ControllerAdvice` to handle exceptions globally. Create methods with `@ExceptionHandler` to handle specific exceptions.
     ```java
     @ControllerAdvice
     public class GlobalExceptionHandler {
         @ExceptionHandler(Exception.class)
         public ResponseEntity<String> handleException(Exception ex) {
             return new ResponseEntity<>(ex.getMessage(), HttpStatus.INTERNAL_SERVER_ERROR);
         }
     }
     ```

### 3. How to handle a `NullPointerException` in Spring Boot?
   - Use `@ExceptionHandler` within a `@ControllerAdvice` to catch `NullPointerException` and return an appropriate response.
     ```java
     @ControllerAdvice
     public class GlobalExceptionHandler {
         @ExceptionHandler(NullPointerException.class)
         public ResponseEntity<String> handleNullPointerException(NullPointerException ex) {
             return new ResponseEntity<>("Null pointer exception occurred", HttpStatus.BAD_REQUEST);
         }
     }
     ```

### 4. How to fetch a list of DTO data?
   - Use a repository method to fetch data and map it to DTOs.
     ```java
     @Repository
     public interface MyRepository extends JpaRepository<MyEntity, Long> {
         @Query("SELECT new com.example.dto.MyDTO(e.field1, e.field2) FROM MyEntity e")
         List<MyDTO> fetchAllDTOs();
     }
     ```

### 5. How to provide access to a third-party client in Spring Boot?
   - Use OAuth or JWT for authentication. Configure security settings to handle access tokens and permissions.

### 6. How to enable CORS and where do you write the logic
   - Use `@CrossOrigin` annotation on controllers or configure it globally.
     ```java
     @Configuration
     public class WebConfig implements WebMvcConfigurer {
         @Override
         public void addCorsMappings(CorsRegistry registry) {
             registry.addMapping("/**").allowedOrigins("http://example.com");
         }
     }
     ```

### 7. How to enable centralized cross-policy?
   - Use `@ControllerAdvice` to handle cross-cutting concerns like error handling or logging.

### 8. What is the difference between JWT and OAuth?
   - JWT (JSON Web Token) is a token format used for securely transmitting information between parties. OAuth is an authorization framework that uses tokens (like JWT) for securing API access.

### 9. Explain the internal working process of JWT
   - JWT consists of a header, payload, and signature. The header and payload are base64-encoded and the signature is created using a secret key. It is used for stateless authentication.

### 10. What is Spring Security?
  - Spring Security is a framework that provides comprehensive security services for Java applications, including authentication, authorization, and protection against common security vulnerabilities.

### 11. What is the use of beans and where do you use them in your application?
  - Beans are managed objects within the Spring container. They are used for dependency injection and are configured in the application context.

### 12. What is the difference between `@Component`, `@Service`, `@Repository`, and `@Controller`, and what is the use of each?
  - `@Component`: Generic stereotype for any Spring-managed component.
  - `@Service`: Specialized component for service layer logic.
  - `@Repository`: Specialized component for data access logic.
  - `@Controller`: Specialized component for web controllers.

### 13. If you use `@Service` in place of `@Controller`, will it work or not?
  - It will work but is not recommended. `@Service` is for service layer beans, while `@Controller` is for handling web requests. Using the wrong annotation may lead to incorrect behavior or misconfigured components.

### 14. What are the different types of Spring Security?
  - Basic Authentication
  - Form-based Authentication
  - OAuth2
  - JWT-based Authentication

### 15. Where are you validating the JWT token in your project?
  - JWT tokens are typically validated in a custom filter or within a security configuration class. 

### 16. What architecture are you using to develop your project?
  - Describe the architecture such as Microservices, Monolithic, Layered Architecture, etc.

### 17. How to sort a list of data based on a field using JPA inbuilt methods?
  - Use `JpaRepository` methods like `findAll(Sort sort)`.
    ```java
      List<MyEntity> findAll(Sort sort);
    ```

### 18. How to fetch and sort a list of DTO data in Spring Boot?
   - Use repository methods with sorting options or fetch data and sort manually in service layer.
     ```java
      @Query("SELECT new com.example.dto.MyDTO(e.field1, e.field2) FROM MyEntity e ORDER BY e.field1")
      List<MyDTO> fetchAndSortDTOs();
     ```

### 19. How to provide third-party client access in Spring Boot?
  - Use OAuth2 or API keys to manage third-party client access.

### 20. Explain the use and application of `@Component`, `@Service`, `@Repository`, and `@Controller`.
  - `@Component` is used for generic components, `@Service` for business services, `@Repository` for data access, and `@Controller
` for web request handling.

### 21. Can you use `@Service` in place of `@Controller`? If yes, what happens?
  - Yes, but it is not recommended. `@Service` is intended for business logic and does not handle web requests, which is the role of `@Controller`.


# Final Round

### 1. What tools have you used in your project?
   -  In my project, I have used tools such as Git for version control, Jenkins for continuous integration and deployment, JIRA for task management, and Docker for containerization.

### 2.  Which database did you use in your project?
   -  We used PostgreSQL as our primary database due to its robustness and support for complex queries.

### 3.  How did you implement JWT authentication in your project?
   -  We implemented JWT authentication by creating a JWT token on user login, which includes user roles and expiration time. The token is then verified with each API request using a JWT filter in our Spring Boot application.

### 4.  How did you configure two different databases in your Spring Boot project?
   -  We configured two different databases by creating separate `DataSource` beans for each database and using `@Primary` annotation to specify the primary data source.

### 5.  Who provided the database structure in your project?
   -  The database structure was provided by our database architect, and the development team collaborated to finalize and optimize it.

### 6.  How were tasks assigned and managed in your project on a weekly basis?
 - Tasks were assigned and managed using JIRA. Each week, we conducted sprint planning meetings to assign tasks and track progress through daily stand-ups.

### 7.  How did you implement an API gateway in your microservices architecture?
   -  We implemented an API gateway using Spring Cloud Gateway, which routes requests to the appropriate microservices and handles cross-cutting concerns like authentication and rate limiting.

### 8.  How did you configure different services in the API gateway?
   -  We configured different services in the API gateway using route definitions in the `application.yml` file, specifying the paths and service URLs.

### 9. What is an Eureka Server?
- Eureka Server is a service registry used in microservices architecture for service discovery, allowing services to find and communicate with each other without hardcoding their locations.

### 10. How do you handle simultaneous requests from multiple users, and who determines request preference?
   - We handle simultaneous requests using load balancers to distribute the traffic across multiple instances of our services. Request preference is determined based on the priority of the request and the resources available.

### 11.  What does a Kafka server do?
   -  A Kafka server is used for real-time data streaming and message brokering, allowing our microservices to communicate asynchronously and handle large volumes of data efficiently.

### 12. How do you handle simultaneous requests from a large number of users?
 -  We handle simultaneous requests from a large number of users using a combination of load balancing, caching, and scalable microservices architecture to ensure high availability and performance.

### 13.  What issues did you recently encounter with Swagger, and how did you resolve them?
   - We encountered issues with Swagger not displaying certain endpoints correctly. We resolved them by ensuring all our controllers were properly annotated and by updating the Swagger configuration to correctly scan all packages.

### 14. How do you upgrade your project, and what technologies are used for upgrading?
 - We upgrade our project by following a continuous integration and deployment pipeline, using tools like Jenkins and Docker. We also perform thorough testing and use feature toggles to ensure smooth rollouts.

### 15. What are some issues you faced in your project, and how did you overcome them?
   - One issue we faced was database performance under high load. We overcame it by optimizing queries, indexing critical fields, and using caching mechanisms to reduce the load on the database.

### 16.Have you worked with Log4j? If so, what was your experience?
   -  Yes, I have worked with Log4j for logging in our Spring Boot applications. It has been effective in providing configurable logging levels and formats,

# HR Round
### Self ,Location, Salary etc.....
