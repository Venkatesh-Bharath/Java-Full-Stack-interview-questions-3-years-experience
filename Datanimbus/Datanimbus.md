# Datanimbus Java Developer Role

## L1 Techhnical Interview
---

### 1. **Introduce yourself**  
"I am Venkatesh Bharath, with 3 years of experience in Java Full Stack Development. I specialize in Spring Boot, Microservices, Hibernate, and ReactJS. I have worked on projects like customer registration systems, batch processing for large datasets, and transaction data handling. My expertise includes implementing REST APIs, working with state management in ReactJS, and ensuring robust test coverage with JUnit and Mockito."

---

### 2. **What are the steps in Spring Batch processing?**  
- **Job**: The batch process's overall definition, containing steps.  
- **Step**: Represents a stage (Reader → Processor → Writer).  
- **ItemReader**: Reads input data.  
- **ItemProcessor**: Processes/transforms data.  
- **ItemWriter**: Writes processed data.  
- **JobRepository**: Stores metadata about the batch.  
- **JobLauncher**: Launches the batch job.  

---

### 3. **What is the difference between JDK, JVM, and JRE?**  
- **JDK (Java Development Kit)**: Includes tools like compilers and debuggers for Java development.  
- **JVM (Java Virtual Machine)**: Executes bytecode. It’s platform-specific.  
- **JRE (Java Runtime Environment)**: Contains JVM and runtime libraries to run Java applications.

---

### 4. **What have you worked on in Spring Batch?**  
"I implemented a batch job for processing transaction records. It included custom `ItemReader`, which fetched data from a database, and a `Processor`, which validated and transformed data. The `Writer` updated another database. I also configured error handling and logging for job monitoring."

---

### 5. **Have you worked on Kafka in Spring Batch?**  
"Yes, I integrated Kafka as a messaging system for batch job communication. Data was read from a Kafka topic, processed in chunks, and written back to another topic, ensuring reliable and asynchronous data flow."

---

### 6. **What are job schedulers in Spring Boot?**  
Job schedulers automate running tasks at specific intervals. Examples:  
- **Spring Task Scheduler**: Lightweight, uses cron expressions.  
- **Quartz Scheduler**: Advanced scheduling with persistence.

---

### 7. **Difference between static block and static variable?**  
- **Static Block**: Runs once during class loading. Used for initialization logic.  
- **Static Variable**: Shared by all instances. Its value can be updated.

---

### 8. **How does parallel processing work, and where is it used?**  
Parallel processing divides tasks into smaller subtasks, executed concurrently across multiple threads.  
**Use Case**: Processing large datasets or running independent tasks (e.g., using parallel streams in Java).

---

### 9. **What is `CompletableFuture` in Java?**  
An API for asynchronous programming. It allows chaining tasks, combining results, and handling exceptions without blocking the main thread.

---

### 10. **Provide a real-time example of `CompletableFuture`.**  
Fetching user details from one service and user transactions from another concurrently, then combining them into a single response for the client.

---

### 11. **Have you worked on microservices?**  
"Yes, I developed microservices for user management and transaction handling, following RESTful principles. Each service had its own database, and they communicated via REST and Kafka."

---

### 12. **How do microservices communicate?**  
- **Synchronous**: REST (HTTP/HTTPS).  
- **Asynchronous**: Messaging queues like Kafka or RabbitMQ.

---

### 13. **Explain creating a POST API step-by-step**  
1. Annotate the class with `@RestController`.  
2. Create a method with `@PostMapping`.  
3. Accept a DTO for the request.  
4. Inject a service class.  
5. Implement logic in the service and save using `JpaRepository`.  
6. Return appropriate HTTP status codes.

---

### 14. **Difference between `Comparable` and `Comparator`**  
- **Comparable**: Defines natural order in the class (`compareTo`).  
- **Comparator**: External comparison logic (`compare`).  
**Example**: Sorting employees by age (Comparator) vs. by ID (Comparable).

---

### 15. **Difference between `StringBuilder` and `StringBuffer`**  
- **StringBuilder**: Faster, non-thread-safe.  
- **StringBuffer**: Thread-safe, synchronized.  
Use **StringBuilder** unless thread safety is needed.

---

### 16. **What is the `volatile` keyword?**  
Ensures visibility of a variable’s updates across threads. Prevents caching issues but does not guarantee atomicity.

---

### 17. **Java code for even number sum using streams**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);
int sum = numbers.stream().filter(n -> n % 2 == 0).mapToInt(Integer::intValue).sum();
```

---

### 18. **Difference between Serialization and Deserialization**  
- **Serialization**: Converts an object to bytes for storage.  
- **Deserialization**: Reconstructs the object from bytes.

---

### 19. **What is the `Optional` class?**  
Used to avoid `NullPointerException`. It represents a value that can be null and provides methods to handle it gracefully.

---

### 20. **How to handle exceptions globally in Spring Boot?**  
Use `@ControllerAdvice` with `@ExceptionHandler`. Example:  
```java
@ControllerAdvice
public class GlobalExceptionHandler {
    @ExceptionHandler(Exception.class)
    public ResponseEntity<String> handleException(Exception e) {
        return new ResponseEntity<>(e.getMessage(), HttpStatus.INTERNAL_SERVER_ERROR);
    }
}
```

---

### 21. **What is a memory leak, and how to avoid it in Java?**  
- **Memory Leak**: Unreferenced objects not garbage collected.  
- **Avoidance**: Close resources, use weak references, and avoid static fields referencing large objects.

---

### 22. **How to monitor Spring Boot applications?**  
Use **Spring Actuator** for endpoints like `/health` and `/metrics`. Combine with tools like Prometheus and Grafana for monitoring.

---

### 23. **How does a HashMap work internally?**  
Keys are hashed into buckets. Each bucket holds an entry list. If two keys map to the same bucket, a linked list or tree structure handles collisions.

---

### 24. **What is a hash collision?**  
Occurs when two keys have the same hash. Resolved using chaining or open addressing.

---

### 25. **What happens if a duplicate key is added to a HashMap?**  
The old value is replaced with the new value.

---

### 26. **Difference between `@Controller` and `@RestController`**  
- **@Controller**: Used for MVC. Returns views.  
- **@RestController**: Used for REST APIs. Combines `@Controller` and `@ResponseBody`.

---

### 27. **What is `@Primary` and `@Qualifier`?**  
- **@Primary**: Marks the default bean.  
- **@Qualifier**: Specifies which bean to use when multiple beans exist.

---

### 28. **What is `@SpringBootApplication`?**  
A meta-annotation combining:  
1. `@Configuration`  
2. `@EnableAutoConfiguration`  
3. `@ComponentScan`

---

### 29. **What is ApplicationContext?**  
The Spring container that manages beans and their life cycle.

---

### 30. **What is Dependency Injection?**  
A design pattern where Spring injects objects a class depends on, instead of the class creating them.

---

### 31. **Life Cycle of Beans**  
1. Instantiate.  
2. Populate properties.  
3. `@PostConstruct`.  
4. Use.  
5. `@PreDestroy`.

---

### 32. **What are interceptors?**  
Pre- and post-process requests in Spring MVC. Used for logging, authentication, etc.

---

### 33. **Difference between `map` and `flatMap`?**  
- **map**: Transforms data.  
- **flatMap**: Flattens nested structures.

---

### 34. **What is the `this` keyword?**  
Refers to the current instance of a class.

---

### 35. **Autoboxing vs. Unboxing**  
- **Autoboxing**: Converts primitive to wrapper (`int` → `Integer`).  
- **Unboxing**: Converts wrapper to primitive (`Integer` → `int`).

---

### 36. **SQL query to join 2 tables without JOIN keyword**  
```sql
SELECT a.*, b.* FROM TableA a, TableB b WHERE a.id = b.id;
```

---

### 37. **How to avoid memory leaks in production?**  
Use tools like **JVisualVM** or **Heap Dump Analyzer**. Optimize code by closing resources, using thread pools, and monitoring object allocation.

---

### 38. **Explain Spring dependency injection and its uses**  
Dependency Injection (DI) decouples object creation. Spring manages dependencies using constructor, setter, or field injection.

---

### 39. **How does `HashMap` handle duplicate keys?**  
If the key already exists, the old value is replaced with the new one.

---

### 40. **How do `@Primary` and `@Qualifier` resolve conflicts?**  
- **@Primary**: Default preference when multiple beans exist.  
- **@Qualifier**: Explicitly specifies which bean to use.  

---

## L2 Techhnical Interview

---
