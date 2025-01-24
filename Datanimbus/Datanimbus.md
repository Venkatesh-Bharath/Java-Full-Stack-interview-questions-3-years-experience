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

### **1. Self-Introduction**  
"I am Venkatesh Bharath, with 3 years of experience in Java Full Stack Development. I specialize in developing scalable and maintainable applications using Spring Boot, Hibernate, and ReactJS. My expertise lies in microservices architecture, database optimization, and test-driven development. I have worked on projects like customer registration systems and transaction data handling, ensuring performance optimization and robust error handling."

---

### **2. Explain your last project and one task in detail**  
"I recently worked on a bank application focusing on user registration and transaction management. One specific task was implementing a batch process for validating and processing customer transactions.  
- **Steps I followed**:  
  1. Defined a `Job` using Spring Batch, including steps for reading, processing, and writing.  
  2. Configured `ItemReader` to fetch transactions from a database.  
  3. Applied business validation logic in `ItemProcessor`.  
  4. Updated valid transactions to the database using `ItemWriter`.  
  5. Set up scheduling using Quartz to run jobs at specific intervals.  
- **Technologies used**: Spring Boot, Spring Batch, and MySQL."

---

### **3. How do different databases connect internally?**  
"Spring Boot provides database connectivity using:  
1. **JDBC**: Uses `DriverManager` to establish connections.  
2. **Connection Pooling**: Tools like HikariCP manage multiple database connections efficiently.  
3. **JPA/Hibernate**: Abstraction layer to interact with the database using entities and queries, converting objects to SQL statements.  
4. **DataSource**: Acts as a bridge between the application and the database, managing connections internally."

---

### **4. What is Dependency Injection?**  
"Dependency Injection (DI) is a design pattern where objects (dependencies) are provided to a class rather than being instantiated within the class. Spring Boot implements DI using:  
1. **Constructor Injection**: Preferred for mandatory dependencies.  
2. **Setter Injection**: Useful for optional dependencies.  
3. **Field Injection**: Directly injects dependencies into class fields."

---

### **5. What is the `@Component` annotation in Spring Boot?**  
"`@Component` is a generic stereotype annotation that marks a class as a Spring-managed bean. Spring automatically detects these beans during component scanning.  
**Example**:  
```java
@Component
public class MyService {
    public void performTask() {
        System.out.println("Task performed.");
    }
}
```

---

### **6. What is a memory leak?**  
"A memory leak occurs when objects are no longer needed but are still referenced, preventing the garbage collector from reclaiming their memory."

---

### **7. How to handle memory leaks manually?**  
- **Close Resources**: Ensure streams, database connections, and files are closed after use.  
- **Avoid Static References**: Large objects held in static fields cause leaks.  
- **Weak References**: Use `WeakReference` for cache-like structures.  
- **Tools**: Use profilers like JVisualVM or Eclipse MAT to detect leaks."

---

### **8. What is Reflection in Java?**  
"Reflection allows inspection and manipulation of classes, methods, and fields at runtime.  
**Example**:  
```java
Class<?> cls = Class.forName("com.example.MyClass");
Method method = cls.getMethod("myMethod");
method.invoke(cls.newInstance());
```

---

### **9. Java Code: Find the length of the longest subarray with the same digit**  
```java
int[] array = {1, 1, 2, 2, 2, 4, 4, 4, 4, 1, 1, 1, 1, 1, 6, 6};
int maxLen = 0, currLen = 1;

for (int i = 1; i < array.length; i++) {
    if (array[i] == array[i - 1]) {
        currLen++;
    } else {
        maxLen = Math.max(maxLen, currLen);
        currLen = 1;
    }
}
maxLen = Math.max(maxLen, currLen); // Final check for last subarray
System.out.println("Longest subarray length: " + maxLen); // Output: 5
```

---

### **10. SQL Query: Find the second maximum age in the employee table**  
```sql
SELECT MAX(age) AS second_max_age 
FROM employees 
WHERE age < (SELECT MAX(age) FROM employees);
```

---

### **11. How to handle duplicate requests in Spring Boot API?**  
"To detect duplicate requests:  
1. Use a unique identifier (e.g., `requestId`) in the request payload.  
2. Store the `requestId` in a cache (e.g., Redis) with a TTL.  
3. Check the cache for duplicates before processing.  
**Example**:  
```java
if (cache.contains(requestId)) {
    throw new DuplicateRequestException("Duplicate request detected.");
} else {
    cache.put(requestId, true);
}
```

---

### **12. What is Parallel Processing?**  
"Parallel processing divides tasks into smaller parts and executes them concurrently across multiple threads or processors.  
**Example**: Java Streams with `.parallelStream()` for large data processing."

---

### **13. What is Spring Boot Actuator and how to implement it?**  
"Spring Boot Actuator provides production-ready features to monitor and manage applications.  
1. Add dependency:  
   ```xml
   <dependency>
       <groupId>org.springframework.boot</groupId>
       <artifactId>spring-boot-starter-actuator</artifactId>
   </dependency>
   ```  
2. Enable endpoints in `application.properties`:  
   ```properties
   management.endpoints.web.exposure.include=health,metrics
   ```  
3. Access endpoints like `/actuator/health` and `/actuator/metrics`."

---

### **14. What is Spring Boot Context?**  
"The Spring ApplicationContext is the central interface for accessing Spring-managed beans and their lifecycle. It initializes the container, resolves dependencies, and manages bean scopes. Example: `AnnotationConfigApplicationContext`."

---

### **15. How to optimize a single API?**  
- **Database Optimization**: Use indexes and optimize queries.  
- **Caching**: Implement Redis or Ehcache for frequently accessed data.  
- **Lazy Loading**: Fetch related data only when required.  
- **Compression**: Enable GZIP for API responses.  
- **Profiling Tools**: Use tools like JProfiler to identify bottlenecks.

--- 

## L3 Techhnical Interview

---

