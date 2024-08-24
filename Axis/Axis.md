# Axis L1
### 1. What are streams in Java, and how are they used?

**Answer:**

Java Streams are part of the `java.util.stream` package and were introduced in Java 8. They provide a high-level abstraction for processing sequences of elements, such as collections, in a functional and declarative way.

- **Key Features:**
  - **Functional Operations:** Streams support operations like `filter`, `map`, `reduce`, `collect`, and `forEach` that can be chained together.
  - **Lazy Evaluation:** Intermediate operations are lazily evaluated, meaning computations are deferred until a terminal operation is invoked.
  - **Parallel Processing:** Streams can be processed in parallel to leverage multi-core processors.

**Example Usage:**

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class StreamExample {
    public static void main(String[] args) {
        List<String> words = Arrays.asList("apple", "banana", "cherry", "date");
        List<String> filteredWords = words.stream()
                                          .filter(word -> word.startsWith("b"))
                                          .map(String::toUpperCase)
                                          .collect(Collectors.toList());
        System.out.println(filteredWords); // Output: [BANANA]
    }
}
```

### 2. Explain lambda expressions in Java with an example.

**Answer:**

Lambda expressions in Java provide a concise way to express instances of functional interfaces (interfaces with a single abstract method). They consist of a parameter list, an arrow (`->`), and a body.

**Syntax:**

```java
(parameters) -> expression
```

**Example:**

```java
import java.util.Arrays;
import java.util.List;

public class LambdaExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
        
        names.forEach(name -> System.out.println(name)); // Output: Alice Bob Charlie
    }
}
```

In this example, `name -> System.out.println(name)` is a lambda expression that prints each name in the list.

### 3. What is reactive programming, and where is it used?

**Answer:**

Reactive programming is a programming paradigm that deals with asynchronous data streams and the propagation of changes. It allows systems to react to data changes or events in a non-blocking and efficient manner.

**Use Cases:**
- **Real-Time Systems:** Handling real-time data streams, such as stock market data or sensor data.
- **User Interfaces:** Building responsive UIs that react to user inputs or data changes.
- **Microservices:** Managing asynchronous communication between services and handling high-load data processing.

**Key Libraries/Frameworks:**
- **RxJava:** A library for composing asynchronous and event-based programs using observable sequences.
- **Project Reactor:** A reactive programming library for building non-blocking applications on the JVM.

### 4. Describe the architecture of microservices and how services communicate with each other.

**Answer:**

**Architecture:**
- **Microservices Architecture** involves breaking down a monolithic application into small, independent services that focus on specific business functions. Each service is developed, deployed, and scaled independently.

**Communication Methods:**
- **HTTP/REST:** Services expose RESTful APIs over HTTP for communication.
- **gRPC:** A high-performance, language-agnostic RPC framework.
- **Message Brokers:** Services communicate asynchronously through message brokers like Kafka, RabbitMQ, or ActiveMQ.
- **Service Discovery:** Tools like Eureka or Consul are used for locating services dynamically.

**Example Diagram:**
```
+-------------------+      +-------------------+
|    Service A      | ---> |    Service B      |
| (REST API)        |      | (Message Queue)   |
+-------------------+      +-------------------+
```

### 5. Explain the architecture of the Spring Framework and the role of the IoC container.

**Answer:**

**Architecture:**
- **Core Container:** Provides the foundation for dependency injection (DI) and bean lifecycle management.
- **AOP (Aspect-Oriented Programming):** Supports cross-cutting concerns like logging and transactions.
- **Data Access/Integration:** Simplifies data access with JDBC and ORM support.
- **Web:** Provides support for building web applications, including RESTful APIs.

**IoC Container:**
- **Role:** Manages the lifecycle and configuration of application objects (beans). It uses Dependency Injection (DI) to decouple the creation of objects from their usage.
- **Types of IoC Containers:** `BeanFactory` (basic container) and `ApplicationContext` (more advanced container).

**Example:**
```java
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class Main {
    public static void main(String[] args) {
        ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);
        MyService myService = context.getBean(MyService.class);
        myService.performAction();
    }
}
```

### 6. What is Docker, and how does it relate to Kubernetes?

**Answer:**

**Docker:**
- **Definition:** Docker is a platform for developing, shipping, and running applications in containers. Containers are lightweight, portable, and include everything needed to run an application.

**Kubernetes:**
- **Relation:** Kubernetes is an orchestration platform that manages the deployment, scaling, and operation of containerized applications across a cluster of machines. It provides automated scheduling, scaling, and management of Docker containers.

**Example Workflow:**
1. **Develop:** Write application code and Dockerize it.
2. **Deploy:** Use Kubernetes to deploy and manage the Docker containers.

### 7. Explain the architecture of a Kafka cluster.

**Answer:**

**Architecture:**
- **Brokers:** Kafka brokers store and manage data. Each broker handles a subset of partitions and replicas.
- **Topics:** Data is organized into topics. Each topic can be divided into multiple partitions for parallel processing.
- **Producers:** Publish messages to topics.
- **Consumers:** Subscribe to topics and consume messages.
- **Zookeeper:** Manages broker metadata, leader elections, and configuration.

**Diagram:**
```
+-----------------+    +-----------------+    +-----------------+
|   Kafka Broker  |    |   Kafka Broker  |    |   Kafka Broker  |
+-----------------+    +-----------------+    +-----------------+
        |                    |                      |
        |                    |                      |
+-----------------+    +-----------------+    +-----------------+
|   Producer      |    |   Consumer      |    |   Zookeeper     |
+-----------------+    +-----------------+    +-----------------+
```

### 8. What is a Security Context in Spring Security, and how does it work?

**Answer:**

**Security Context:**
- **Definition:** A Security Context is a container that holds the authentication and authorization information for the currently authenticated user.
- **Usage:** It is stored in a `ThreadLocal` and provides access to the current user's roles and permissions.

**How it Works:**
1. **Authentication:** Upon successful login, Spring Security creates a `SecurityContext` that holds an `Authentication` object.
2. **Authorization:** The `SecurityContext` is used throughout the application to check if the user has the necessary permissions to access resources.

**Example:**
```java
import org.springframework.security.core.Authentication;
import org.springframework.security.core.context.SecurityContextHolder;

public class SecurityUtils {
    public static String getCurrentUsername() {
        Authentication auth = SecurityContextHolder.getContext().getAuthentication();
        return auth != null ? auth.getName() : "Anonymous";
    }
}
```

### 9. How do you implement JWT token-based authentication?

**Answer:**

**Implementation Steps:**
1. **Generate Token:** After successful authentication, generate a JWT token containing user details.
2. **Send Token:** Send the token to the client, typically in the response header.
3. **Authenticate Requests:** Include the token in the Authorization header of subsequent requests. Verify the token and extract user information.

**Example Code (Java):**

```java
import io.jsonwebtoken.Jwts;
import io.jsonwebtoken.SignatureAlgorithm;

public class JwtUtil {
    private static final String SECRET_KEY = "your-secret-key";

    public static String generateToken(String username) {
        return Jwts.builder()
                   .setSubject(username)
                   .signWith(SignatureAlgorithm.HS256, SECRET_KEY)
                   .compact();
    }
}
```

### 10. How do you use salt and hash in JWT to secure tokens?

**Answer:**

**Salt and Hash:**
- **Salt:** A random value added to the token before hashing to enhance security and prevent precomputed attacks.
- **Hash:** A cryptographic function applied to the salted token to ensure its integrity.

**Steps:**
1. **Generate Salt:** Create a unique salt for each token.
2. **Hash Token:** Combine the token with the salt and apply a hash function.
3. **Store and Validate:** Store the salted and hashed token. During validation, combine the incoming token with the salt and hash it to compare with the stored value.

**Example Code (Java):**

```java
import java.security.MessageDigest;
import java.security.NoSuchAlgorithmException;
import java.security.SecureRandom;

public class TokenUtil {
    private static final SecureRandom random = new SecureRandom();

    public static String generateSalt() {
        byte[] salt = new byte[16];
        random.nextBytes(salt);
        return new String(salt);
    }

    public static String hashToken(String token, String salt) throws NoSuchAlgorithmException {
        MessageDigest md = MessageDigest.getInstance("SHA-256");
        md.update((token + salt).getBytes());
        byte[] hashedBytes = md.digest();
        return new String(has

hedBytes);
    }
}
```

### 11. Write a code to find the longest palindrome substring length in a string.

**Answer:**

Here is an example code to find the length of the longest palindrome substring:

**Code:**

```java
public class LongestPalindromeLength {

    private static int expandAroundCenter(String s, int left, int right) {
        while (left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
            left--;
            right++;
        }
        return right - left - 1;
    }

    public static int longestPalindromeLength(String s) {
        if (s == null || s.length() == 0) return 0;

        int maxLength = 0;

        for (int i = 0; i < s.length(); i++) {
            int len1 = expandAroundCenter(s, i, i); // Odd length palindromes
            int len2 = expandAroundCenter(s, i, i + 1); // Even length palindromes
            int len = Math.max(len1, len2);
            maxLength = Math.max(maxLength, len);
        }

        return maxLength;
    }

    public static void main(String[] args) {
        String input = "babad";
        System.out.println("Length of longest palindrome substring: " + longestPalindromeLength(input));
    }
}
```

**Example:**
- **Input:** `"babad"`
- **Output:** `3` (The longest palindromes are `"bab"` or `"aba"`, both with a length of 3)
