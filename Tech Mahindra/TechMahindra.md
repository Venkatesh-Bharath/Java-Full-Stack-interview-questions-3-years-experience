
# Tech Mahindra
## Java Questions

### 1. What are the new features in Java 8?
   - Lambda Expressions
   - Stream API
   - Optional Class
   - Default Methods in Interfaces
   - Method References
   - New Date and Time API (java.time)
   - Nashorn JavaScript Engine

### 2. What is batch processing in Java?
   - Batch processing refers to executing a series of jobs without manual intervention. It can be implemented using frameworks like Spring Batch, which provides reusable functions that process large volumes of data.

### 3. What is job scheduling in Java?
   - Job scheduling involves setting up tasks to run at specified times or intervals. Java provides APIs like `java.util.Timer` and `java.util.concurrent.ScheduledExecutorService`. Additionally, libraries like Quartz Scheduler offer more advanced features.

### 4. What are the inbuilt Java functional interfaces?
   - `Predicate<T>`
   - `Function<T, R>`
   - `Supplier<T>`
   - `Consumer<T>`
   - `BiFunction<T, U, R>`

### 5. What is the difference between an interface and a functional interface?
   - An interface can have any number of abstract methods.
   - A functional interface has exactly one abstract method and can have any number of default or static methods. It is used as the assignment target for lambda expressions.

### 6. Explain the Singleton design pattern.
   - The Singleton design pattern ensures that a class has only one instance and provides a global point of access to it. It is typically implemented by making the constructor private and providing a static method that returns the instance.

### 7. How can you break the Singleton design pattern?
   - Using reflection to call the private constructor.
   - Using serialization and deserialization.
   - Using cloning.

### 8. What is a default method in Java and what is its use?
   - A default method in an interface provides a default implementation that can be overridden by implementing classes. It allows interfaces to evolve without breaking existing implementations.

### 9. How do you handle errors in Java?
   - Using try-catch blocks to catch and handle exceptions.
   - Using `throws` keyword to declare exceptions.
   - Using custom exception classes for specific error handling.

### 10. **How many types of exceptions are there in Java?
  - Checked exceptions (subclasses of `Exception` except `RuntimeException`)
  - Unchecked exceptions (subclasses of `RuntimeException`)
  - Errors (subclasses of `Error`)

### 11. Explain checked and unchecked exceptions.
  - Checked exceptions must be declared in a method or constructor's `throws` clause if they can be thrown by the execution of the method or constructor and propagated outside the method or constructor boundary.
  - Unchecked exceptions do not need to be declared in a `throws` clause and can be thrown at any time during the execution of the program.

### 12. What is the difference between shallow copy and deep copy?
  - Shallow copy copies the object's fields as they are, so if the field is a reference to another object, only the reference is copied.
  - Deep copy creates a new instance of each object, recursively copying all nested objects.

### 13. If you throw an IOException inside a try block, can you handle it in a catch block with a runtime exception? Will it work or not and why?
  - No, it will not work. An IOException is a checked exception and must be caught or declared to be thrown. A catch block for a runtime exception (unchecked exception) will not handle it.

### 14. What is serialization and deserialization?
   - Serialization is the process of converting an object into a byte stream for storage or transmission.
   - Deserialization is the process of converting a byte stream back into an object.

15. Implement a generic double linked list with a method to remove an element based on the index in Java.
   ```java
    public class DoublyLinkedList<T> {
        class Node {
            T data;
            Node prev, next;

            Node(T data) {
                this.data = data;
            }
        }

        private Node head, tail;

        public void remove(int index) {
            if (index < 0) return;
            Node current = head;
            for (int i = 0; i < index && current != null; i++) {
                current = current.next;
            }
            if (current == null) return;

            if (current.prev != null) {
                current.prev.next = current.next;
            } else {
                head = current.next;
            }
            if (current.next != null) {
                current.next.prev = current.prev;
            } else {
                tail = current.prev;
            }
        }
    }
   ```

### 16. Given two arrays, combine them into a single sorted array.
   ```java
  int[] solution(int[] list1, int[] list2) {
        
        int i = 0, j = 0, a = list1.length - 1, b = list2.length - 1;
        int[] ans = new int[a+1 + b+1];
        int k = 0;
        while (i <= a || j <= b) {
            if (i <= a && j <= b) {
                if (list1[i] <= list2[j]) {
                    ans[k++] = list1[i++];
                } else {
                    ans[k++] = list2[j++];
                }
            } else if (i <= a) {
                ans[k++] = list1[i++];
            } else if (j <= b) {
                ans[k++] = list2[j++];
            }
        }
        return ans;
    }

   ```

### 17. Ladder array code in Java.
  ```java
    public void printLadderArray(int n) {
        int[][] ladder = new int[n][];
        for (int i = 0; i < n; i++) {
            ladder[i] = new int[i + 1];
            for (int j = 0; j < i + 1; j++) {
                ladder[i][j] = j + 1;
            }
        }
        for (int[] row : ladder) {
            System.out.println(Arrays.toString(row));
        }
    }
  ```

## Spring Boot Questions

### 1. What are profiles in Spring Boot?
   - Profiles in Spring Boot are a way to segregate parts of your application configuration and make it only available in certain environments. You can activate profiles using the `--spring.profiles.active` command-line argument or by setting the `spring.profiles.active` property in application properties.

### 2. How do you provide security in Spring Boot?
   - By using Spring Security, which provides authentication and authorization. Common methods include in-memory authentication, JDBC authentication, and LDAP authentication.

### 3. Explain the process of JWT token-based authentication.
   - The client sends a login request with credentials.
   - The server validates the credentials and generates a JWT token.
   - The client stores the token and includes it in the Authorization header of subsequent requests.
   - The server validates the token and processes the request if the token is valid.

### 4. What classes do you use in JWT token security?
   - `JwtTokenProvider` for token generation and validation.
   - `JwtAuthenticationFilter` to filter and validate requests.
   - `JwtAuthenticationEntryPoint` for handling authentication errors.

### 5. Why do you need the UserDetails class in Spring Security?
   - The `UserDetails` class represents a core user information. It provides necessary information like username, password, and authorities for authentication and authorization.

### 6. How do you handle exceptions in Spring Boot?
   - Using `@ControllerAdvice` and `@ExceptionHandler` to handle exceptions globally.
   - Customizing the error response by defining a `ResponseEntity` with appropriate status and message.

## Microservices Questions

### 1. What is fault tolerance in microservices?
   - Fault tolerance is the ability of a system to continue operating properly in the event of the failure of some of its components. This can be achieved using patterns like circuit breaker, retry mechanisms, and fallback methods.

### 2. What is logging and distributed tracing in microservices?
   - Logging involves recording information about the system's operation. Distributed tracing helps in tracking and analyzing requests as they propagate through a distributed system. Tools like ELK stack, Zipkin, and Jaeger are used for this purpose.

### 3. How do you communicate between one microservice and another microservice?
   - Using REST APIs over HTTP.
   - Using messaging queues like RabbitMQ or Kafka.
   - Using gRPC for efficient communication.

### 4. How do you limit requests in microservices?
   - Using rate limiting techniques, such as token bucket algorithm or leaky bucket algorithm.
   - Implementing API gateway tools like Netflix Zuul or Spring Cloud Gateway to enforce rate limiting.

### 5. What is a Kafka server?
   - Kafka is a distributed event streaming platform capable of handling high throughput and low-latency data streams. It is used for building real-time data pipelines and streaming applications.

### 6. Explain Jenkins and its use in microservices.
   - Jenkins is a continuous integration and continuous delivery tool. It automates the building, testing, and deploying of applications. In microservices, Jenkins can manage the pipelines for each microservice, ensuring that changes are integrated and deployed smoothly.
