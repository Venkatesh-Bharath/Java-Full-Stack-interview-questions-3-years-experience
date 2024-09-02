# KVAS Technologies

# Technical Interview
---

### 1. **Introduce yourself with a focus on your recent projects and the technologies you've worked with.**

**Answer:**
I am BSK, a Java full stack developer with 3 years of experience in building scalable web applications. My recent project involved developing a  abc application  where I focused on the user registration page and transaction data handling. I used ReactJS for the frontend, Spring Boot for the backend, and implemented microservices architecture. My tech stack includes Java, Spring Boot, Hibernate, ReactJS, and MySQL.

### 2. **Describe a recent task or project you worked on. What challenges did you face and how did you overcome them?**

**Answer:**
In my recent project, I worked on a feature to implement real-time transaction monitoring. The challenge was ensuring the system could handle high-frequency transactions without performance degradation. I optimized the database queries, used Redis for caching frequently accessed data, and applied asynchronous processing for non-critical tasks. This improved the system's performance significantly.

### 3. **Why are you looking for a new job? What motivates your job search?**

**Answer:**
I am seeking new opportunities to expand my skill set and work on more challenging projects. I am particularly interested in roles that offer the chance to work with cutting-edge technologies and innovative solutions, which will help me grow both professionally and personally.

### 4. **Write a code example for Bubble Sort in Java.**

**Answer:**

```java
public class BubbleSort {
    public static void main(String[] args) {
        int[] arr = {3, 5, 1, 0, 4, 6};
        bubbleSort(arr);
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }

    public static void bubbleSort(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    // Swap arr[j] and arr[j+1]
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
    }
}
```

### 5. **What is the difference between PUT, PATCH, and POST in RESTful services?**

**Answer:**
- **PUT:** Used to update an existing resource or create a resource if it does not exist. It is idempotent, meaning multiple identical requests should yield the same result.
- **PATCH:** Used to apply partial updates to a resource. It is not necessarily idempotent.
- **POST:** Used to create a new resource. It is not idempotent, and repeated requests may create multiple resources.

### 6. **If an API takes a long time to respond, how do you handle it in your application?**

**Answer:**
To handle long API response times, I would implement asynchronous processing using the `@Async` annotation in Spring Boot or use techniques like caching, timeout settings, or a circuit breaker pattern to manage delayed responses and prevent performance bottlenecks.

### 7. **What is the @Async annotation in Spring Boot, and how does it work?**

**Answer:**
The `@Async` annotation in Spring Boot is used to run methods asynchronously in a separate thread. This allows the main thread to continue processing without waiting for the annotated method to complete, improving the application's performance.

### 8. **How do you write a native query in JPA with Spring Boot?**

**Answer:**
A native query in JPA can be written using the `@Query` annotation with the `nativeQuery` attribute set to `true`. For example:

```java
@Query(value = "SELECT * FROM users WHERE email = ?1", nativeQuery = true)
User findByEmail(String email);
```

### 9. **Explain what Dependency Injection is in Spring Boot.**

**Answer:**
Dependency Injection (DI) in Spring Boot is a design pattern where the framework injects dependencies (objects) into a class rather than the class creating them. This promotes loose coupling and enhances testability and modularity.

### 10. **Provide an example where Dependency Injection is used in a Spring Boot application.**

**Answer:**
In a Spring Boot application, a service class can be injected into a controller using `@Autowired`:

```java
@Service
public class UserService {
    // Business logic
}

@RestController
public class UserController {
    @Autowired
    private UserService userService;

    // Controller methods using userService
}
```

### 11. **In which scenarios would you use the @Autowired annotation in Spring Boot?**

**Answer:**
The `@Autowired` annotation is used in Spring Boot to inject dependencies, such as service or repository beans, into a class. It can be used in constructors, setters, or directly on fields.

### 12. **What are the different bean scopes available in Spring Boot?**

**Answer:**
The different bean scopes in Spring Boot are:
- **Singleton:** One instance per Spring container.
- **Prototype:** A new instance every time the bean is requested.
- **Request:** One instance per HTTP request.
- **Session:** One instance per HTTP session.
- **Application:** One instance per ServletContext.

### 13. **How does the request-response cycle work in a Spring Boot application?**

**Answer:**
In a Spring Boot application, a client sends an HTTP request, which is received by the DispatcherServlet. The request is then routed to the appropriate controller method, which processes the request and returns a response. The response is sent back to the client via the DispatcherServlet.

### 14. **How does the prototype scope work in Spring Boot?**

**Answer:**
In the prototype scope, a new instance of the bean is created each time it is requested from the Spring container. This is useful when you need multiple instances of a bean with different states.

### 15. **How does the singleton scope work in Spring Boot?**

**Answer:**
In the singleton scope, a single instance of the bean is created and shared across the entire Spring container. This is the default scope in Spring Boot and is used when you want a single shared instance.

### 16. **What are the @Primary and @Qualifier annotations in Spring Boot, and when would you use them?**

**Answer:**
- **@Primary:** Used to indicate the preferred bean when multiple beans of the same type exist.
- **@Qualifier:** Used to specify which bean should be injected when multiple beans of the same type exist and `@Primary` is not sufficient.

### 17. **Explain the different types of relationships in JPA (e.g., One-to-One, One-to-Many, Many-to-One, Many-to-Many).**

**Answer:**
- **One-to-One:** Each entity instance is associated with one instance of another entity.
- **One-to-Many:** An entity instance is associated with multiple instances of another entity.
- **Many-to-One:** Multiple instances of an entity are associated with one instance of another entity.
- **Many-to-Many:** Multiple instances of an entity are associated with multiple instances of another entity.

### 18. **How do you handle exceptions in a Spring Boot application?**

**Answer:**
In Spring Boot, exceptions can be handled using `@ExceptionHandler` in controllers or globally using `@ControllerAdvice`. This allows for centralized exception handling and custom error responses.

### 19. **What is the @ControllerAdvice annotation, and how does it work in Spring Boot?**

**Answer:**
`@ControllerAdvice` is used to define global exception handling for Spring MVC controllers. It allows you to write a single piece of code that handles exceptions across all controllers.

### 20. **What is Aspect-Oriented Programming (AOP), and how is it used in Spring Boot?**

**Answer:**
Aspect-Oriented Programming (AOP) allows you to separate cross-cutting concerns (e.g., logging, security) from the business logic. In Spring Boot, AOP is implemented using aspects and advice that can be applied declaratively to methods or classes.

### 21. **What approaches have you used for authentication in your Spring Boot projects?**

**Answer:**
In my projects, I have used JWT (JSON Web Token) for stateless authentication, as well as OAuth2 for secure access. Both approaches provide robust security and are easy to integrate with Spring Security.

### 22. **How does JWT token-based authentication work in Spring Boot?**

**Answer:**
In JWT token-based authentication, a token is generated after a user successfully logs in. This token is then included in the header of subsequent requests to authenticate the user. The server verifies the token's validity and extracts user information from it.

### 23. **What is role-based authentication, and how do you implement it in Spring Boot?**

**Answer:**
Role-based authentication restricts access to certain parts of the application based on user roles. In Spring Boot, it can be implemented using Spring Security by assigning roles to users and securing endpoints with `@PreAuthorize` or `@Secured`.

### 24. **How do you perform health checks in a Spring Boot application?**

**Answer:**
Health checks in Spring Boot can be performed using the Actuator module, which provides endpoints like `/actuator/health` to check the application's health and status.

### 25. **What is a YAML file in Spring Boot, and how is it used?**

**Answer:**
A YAML file in Spring Boot is an alternative to the `application.properties` file for configuring the application. It

 provides a more readable and hierarchical way to define configuration settings.

### 26. **Given a string `str` and a substring `str1`, count how many times `str1` appears in `str`.**

- **Example Input:**
  `str = "i am good boy"`  
  `str1 = "am"`
- **Example Output:**
  `1`

**Answer:**

```java
public class SubstringCount {
    public static void main(String[] args) {
        String str = "i am good boy";
        String str1 = "am";
        int count = countOccurrences(str, str1);
        System.out.println(count);
    }

    public static int countOccurrences(String str, String subStr) {
        int count = 0;
        int index = 0;
        while ((index = str.indexOf(subStr, index)) != -1) {
            count++;
            index += subStr.length();
        }
        return count;
    }
}
```

---
# HR Interview

### 1. Give a self-introduction and explain your project.
### 2. What tasks did you work on in your last project?
### 3. What are your salary expectations?
### 4. Are you interested in learning new technology?
### 5. Why are you looking for a new job? etc....
