
### 1. **What are the key features introduced in Java 8?**

**Answer:**  
- **Lambda Expressions**: Allows for concise representation of instances of single-method interfaces (functional interfaces).
- **Stream API**: Provides a new abstraction for processing sequences of elements, supporting operations like map, filter, and reduce.
- **Optional Class**: A container object which may or may not contain a value, used to avoid null references.
- **Default Methods**: Interfaces can now have methods with a body, allowing for backward compatibility.
- **Method References**: Shortcuts to call methods using the syntax `ClassName::methodName`.
- **New Date and Time API**: A new, comprehensive API for handling dates and times (`java.time` package).

### 2. **What are the built-in functional interfaces available in Java 8?**

**Answer:**
- **`Predicate<T>`**: Represents a boolean-valued function of one argument.
- **`Function<T, R>`**: Represents a function that takes an argument of type `T` and returns a result of type `R`.
- **`Consumer<T>`**: Represents an operation that accepts a single input argument and returns no result.
- **`Supplier<T>`**: Represents a supplier of results, providing instances of type `T`.
- **`UnaryOperator<T>`**: A specialized form of `Function` that takes a single argument and returns a result of the same type.
- **`BinaryOperator<T>`**: A specialized form of `Function` that takes two arguments of the same type and returns a result of the same type.

### 3. **What is a profile in Spring Boot, and how do you use it?**

**Answer:**  
- **Profile**: A feature that allows for the segregation of application configuration based on different environments (e.g., development, testing, production).
- **Usage**: Define profiles using the `@Profile` annotation in Spring components or specify them in `application.properties` or `application.yml`. Activate profiles via command-line arguments or environment variables (e.g., `--spring.profiles.active=dev`).

### 4. **What configurations can be managed within a Spring Boot profile?**

**Answer:**  
- **Data Source Configurations**: Define different database configurations for various environments.
- **Service Endpoints**: Configure different API endpoints or service URLs based on the active profile.
- **Logging Levels**: Set different logging levels or loggers for different environments.
- **Security Settings**: Adjust security configurations such as authentication mechanisms or access controls.

### 5. **What are the advantages of using microservices architecture?**

**Answer:**
- **Scalability**: Individual components can be scaled independently.
- **Flexibility**: Different services can be developed, deployed, and maintained separately.
- **Resilience**: Failure in one service does not necessarily impact others.
- **Technology Agnostic**: Different services can use different technologies or frameworks.
- **Faster Time to Market**: Smaller teams can develop and deploy services more quickly.

### 6. **How do you integrate microservices in a project?**

**Answer:**
- **API Gateway**: Use an API gateway to handle requests and route them to the appropriate microservices.
- **Service Registry**: Use tools like Eureka for service discovery and registration.
- **Inter-Service Communication**: Implement communication between services using REST APIs, messaging queues, or gRPC.
- **Configuration Management**: Use tools like Spring Cloud Config to manage configuration centrally.
- **Monitoring and Logging**: Implement centralized logging and monitoring using tools like ELK stack or Prometheus.

### 7. **What is a Eureka Server, and how is it used in microservices?**

**Answer:**  
- **Eureka Server**: A service discovery tool provided by Netflix, part of the Spring Cloud ecosystem.
- **Usage**: Services register themselves with the Eureka Server, and other services can discover and communicate with them using the server's registry. It helps in managing service instances and load balancing.

### 8. **Can you explain the internal working of a HashMap in Java?**

**Answer:**  
- **HashMap** stores key-value pairs. Internally, it uses an array of buckets, where each bucket is a linked list or a tree (if many entries hash to the same bucket).
- **Hashing**: Keys are hashed to determine their bucket location.
- **Collision Resolution**: If multiple keys hash to the same bucket, they are stored in a linked list or tree structure within that bucket.
- **Resizing**: When the number of entries exceeds a threshold, the HashMap resizes and rehashes all entries.

### 9. **Given a list of integers [1, 2, 4, 6, 8, 9], with the numbers 3, 5, and 7 missing, how would you print the missing numbers using Java Streams?**

**Answer:**
```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;
import java.util.stream.IntStream;

public class MissingNumbers {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 4, 6, 8, 9);
        int min = 1;
        int max = 9;

        List<Integer> missingNumbers = IntStream.rangeClosed(min, max)
            .filter(n -> !numbers.contains(n))
            .boxed()
            .collect(Collectors.toList());

        System.out.println("Missing numbers: " + missingNumbers);
    }
}
```

### 10. **Given a list of strings ["blue", "green", "red", "pink"], how would you find the longest string and print its length using Java Streams?**

**Answer:**
```java
import java.util.Arrays;
import java.util.List;
import java.util.Comparator;

public class LongestStringLength {
    public static void main(String[] args) {
        List<String> strings = Arrays.asList("blue", "green", "red", "pink");

        int maxLength = strings.stream()
            .sorted(Comparator.comparingInt(String::length).reversed())
            .findFirst()
            .map(String::length)
            .orElse(0);

        System.out.println("Length of the longest string: " + maxLength);
    }
}
```
