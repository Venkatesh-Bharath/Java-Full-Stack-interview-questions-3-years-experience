 # Telepone Interview
 Here are the answers to your interview questions with real-time examples:

---

### **Java 8 & Streams:**

1. **How do Java 8 Futures work?**  
   **Answer:**  
   Java 8 `Future` represents the result of an asynchronous computation. You can use `CompletableFuture` for non-blocking asynchronous tasks.  
   **Example:**
   ```java
   import java.util.concurrent.*;

   public class FutureExample {
       public static void main(String[] args) throws ExecutionException, InterruptedException {
           ExecutorService executor = Executors.newSingleThreadExecutor();
           Future<Integer> future = executor.submit(() -> {
               Thread.sleep(2000);  // Simulate long computation
               return 123;
           });
           System.out.println("Result: " + future.get());  // Blocks until the result is available
           executor.shutdown();
       }
   }
   ```

2. **What is the difference between `parallel` and `parallelStream` in Java Streams?**  
   **Answer:**  
   `parallel` is a method available on a collection, while `parallelStream` is a method on the `Stream` interface. Both allow parallel processing of data but `parallelStream` is more convenient for stream-based operations.  
   **Example:**  
   ```java
   List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

   // Using parallelStream
   numbers.parallelStream().forEach(num -> System.out.println(num + " - " + Thread.currentThread().getName()));

   // Using parallel (with forEach)
   numbers.forEach(num -> System.out.println(num + " - " + Thread.currentThread().getName()));
   ```

3. **You have two lists: one to find even numbers and one to find odd numbers. How would you solve this using parallel streams?**  
   **Answer:**  
   We can use `parallelStream` to process both lists in parallel and then combine the results.
   **Example:**
   ```java
   List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9);

   List<Integer> evens = numbers.parallelStream()
                                 .filter(num -> num % 2 == 0)
                                 .collect(Collectors.toList());
   List<Integer> odds = numbers.parallelStream()
                                .filter(num -> num % 2 != 0)
                                .collect(Collectors.toList());
   
   System.out.println("Even numbers: " + evens);
   System.out.println("Odd numbers: " + odds);
   ```

4. **Can we implement a method in an interface?**  
   **Answer:**  
   Yes, starting from Java 8, interfaces can have default and static methods, which can contain a method body.  
   **Example:**
   ```java
   interface MyInterface {
       default void printMessage() {
           System.out.println("Hello from interface!");
       }
   }
   ```

5. **What loads first: static block or static method, and why? Why doesn't the `main` method load first, even though it's static?**  
   **Answer:**  
   The static block is executed first, before the `main` method, because it is used to initialize the class. The `main` method is executed when the class is invoked by the JVM.  
   **Example:**
   ```java
   class Test {
       static {
           System.out.println("Static block executed");
       }
       public static void main(String[] args) {
           System.out.println("Main method executed");
       }
   }
   ```

---

### **Microservices & Exception Handling:**

1. **How should we handle exceptions in microservices, especially with so many services?**  
   **Answer:**  
   We can handle exceptions globally using `@ControllerAdvice` or by using a centralized logging service like ELK stack (Elasticsearch, Logstash, Kibana).  
   **Example:**
   ```java
   @ControllerAdvice
   public class GlobalExceptionHandler {
       @ExceptionHandler(ResourceNotFoundException.class)
       public ResponseEntity<Object> handleResourceNotFound(ResourceNotFoundException ex) {
           return new ResponseEntity<>("Resource not found", HttpStatus.NOT_FOUND);
       }
   }
   ```

2. **What is the difference between `@ControllerAdvice` and `@ExceptionHandler`?**  
   **Answer:**  
   `@ControllerAdvice` is a global exception handler for controllers, whereas `@ExceptionHandler` handles exceptions for a specific controller or method.  
   **Example:**
   ```java
   @ControllerAdvice
   public class GlobalExceptionHandler {
       @ExceptionHandler(Exception.class)
       public ResponseEntity<Object> handleGlobalException(Exception ex) {
           return new ResponseEntity<>("Global exception occurred", HttpStatus.INTERNAL_SERVER_ERROR);
       }
   }
   ```

3. **What is the difference between global exceptions and normal exceptions?**  
   **Answer:**  
   Global exceptions are handled globally across all controllers (using `@ControllerAdvice`), while normal exceptions are handled within the specific controller method using `@ExceptionHandler`.  

4. **If two APIs are there and one fails, how should we know the API failed?**  
   **Answer:**  
   You can check the HTTP status code. If one API fails, the status code will be in the 4xx or 5xx range, which indicates a failure.  
   **Example:**  
   ```java
   ResponseEntity<String> response = restTemplate.exchange(url, HttpMethod.GET, request, String.class);
   if (response.getStatusCode().is4xxClientError() || response.getStatusCode().is5xxServerError()) {
       System.out.println("API call failed");
   }
   ```

5. **If one service calls another service and the second service fails, how should we handle it? Explain with code.**  
   **Answer:**  
   Use a retry mechanism, circuit breakers (e.g., using Spring Cloud Circuit Breaker), or fallback methods.  
   **Example:**
   ```java
   @CircuitBreaker(fallbackMethod = "fallbackMethod")
   public String callService() {
       return restTemplate.getForObject("http://service-url", String.class);
   }

   public String fallbackMethod(Exception e) {
       return "Service unavailable";
   }
   ```

6. **What is fallback mechanism in microservices?**  
   **Answer:**  
   A fallback mechanism ensures that if a service fails, a default response or an alternative method is executed to handle the failure gracefully. This can be achieved using tools like Hystrix or Resilience4j.  

---

### **Functional Interfaces & Annotations:**

1. **What is a marker interface? What is its use and why is it used?**  
   **Answer:**  
   A marker interface is an interface with no methods. It's used to signal to the JVM or a framework that a class has a specific property or behavior.  
   **Example:**  
   `Serializable` is a marker interface used to indicate that a class can be serialized.  

2. **What is a functional interface and why is it used?**  
   **Answer:**  
   A functional interface is an interface with a single abstract method, used primarily for lambda expressions.  
   **Example:**
   ```java
   @FunctionalInterface
   interface MyFunctionalInterface {
       void myMethod();
   }
   ```

3. **What is the difference between `@Configuration` and `@Component`?**  
   **Answer:**  
   `@Configuration` is used for classes that define Spring beans and contain bean definitions, whereas `@Component` is a generic annotation for Spring beans.  
   **Example:**  
   ```java
   @Configuration
   public class AppConfig {
       @Bean
       public MyBean myBean() {
           return new MyBean();
       }
   }
   ```

4. **What is the difference between `@Bean` and `@Configuration`?**  
   **Answer:**  
   `@Bean` is used to define a single bean, whereas `@Configuration` indicates that a class contains bean definitions.  
   **Example:**  
   `@Configuration` can contain multiple `@Bean` methods.

5. **Can we use `@Component` instead of `@Repository`?**  
   **Answer:**  
   Yes, `@Repository` is a specialization of `@Component` with additional behavior like exception translation. You can use `@Component` but `@Repository` is more semantically appropriate for persistence layers.

---

### **SQL:**

1. **How would you update the salary by 10% extra and 10% less in the same SQL query based on a condition?**  
   **Answer:**
   ```sql
   UPDATE employees
   SET salary = CASE
                   WHEN condition = 'increase' THEN salary * 1.10
                   WHEN condition = 'decrease' THEN salary * 0.90
                   ELSE salary
                 END;
   ```

2. **Can we use aggregate functions with `GROUP BY` in SQL?**  
   **Answer:**  
   Yes, aggregate functions like `SUM()`, `COUNT()`, `AVG()`, etc., can be used with `GROUP BY` to group the results by specific columns.  
   **Example:**  
   ```sql
   SELECT department, COUNT(*) 
   FROM employees 
   GROUP BY department;
   ```

3. **What are aggregate functions in SQL?**  
   **Answer:**  
   Aggregate functions perform calculations on a set of values and return a single value. Examples include `COUNT()`, `SUM()`, `AVG()`, `MIN()`, and `MAX()`.

4. **How do we filter data using `GROUP BY` in SQL?**  
   **Answer:**  
   We can use the `HAVING` clause to filter the results after applying `GROUP BY`.  
   **Example:**  
   ```sql
   SELECT department, COUNT(*) 
   FROM employees 
   GROUP BY department 
   HAVING COUNT(*) > 5;
   ```

---
