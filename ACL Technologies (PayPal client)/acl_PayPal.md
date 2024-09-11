# Technical Round
1. **Explain your recent project.**
   - *Provide details about your recent project, including the technology stack, your role, the objectives, challenges faced, and how you overcame those challenges.*

2. **What are the new features in Java 8?**
   - *Java 8 introduced several new features, including:* 
     - *Lambda expressions*
     - *Functional interfaces*
     - *Stream API*
     - *New Date and Time API (java.time)*
     - *Default methods in interfaces*
     - *Method references*
     - *Optional class*

3. **What is a static method in Java?**
   - *A static method belongs to the class rather than instances of the class. It can be called without creating an instance of the class.*

4. **How can we use static methods in an interface?**
   - *Static methods in interfaces can be used to provide utility methods that are related to the interface but do not need an instance. They are called using the interface name.*

5. **How can we call a static method?**
   - *Static methods can be called using the class name or the interface name if defined in an interface, e.g., `ClassName.staticMethod()` or `InterfaceName.staticMethod()`.*

6. **How many ways can we call static methods?**
   - *Static methods can be called in two ways:* 
     - *Using the class name (e.g., `Math.sqrt(4)` for `Math.sqrt`)*
     - *Directly if in the same class (e.g., `staticMethod()`)*

7. **What is a default method in Java?**
   - *Default methods are methods in interfaces that have a body. They provide a default implementation that can be used by implementing classes.*

8. **What is the use of default methods in interfaces?**
   - *Default methods allow interfaces to evolve without breaking existing implementations. They enable the addition of new methods with default behavior.*

9. **What is a method reference in Java?**
   - *Method references are a shorthand notation for calling a method. They provide a way to refer to methods without invoking them.*

10. **How many ways can we create method references?**
    - *Method references can be created in the following ways:*
      - *Reference to a static method*
      - *Reference to an instance method of a specific object*
      - *Reference to an instance method of an arbitrary object*
      - *Reference to a constructor*

11. **Provide a customized example of a method reference with full code and explanation.**

    ```java
    import java.util.Arrays;
    import java.util.List;

    public class MethodReferenceExample {
        public static void main(String[] args) {
            List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

            // Using method reference to call static method
            names.forEach(MethodReferenceExample::printName);

            // Using method reference to call instance method
            MethodReferenceExample instance = new MethodReferenceExample();
            names.forEach(instance::printNameInstance);
        }

        // Static method
        public static void printName(String name) {
            System.out.println(name);
        }

        // Instance method
        public void printNameInstance(String name) {
            System.out.println(name);
        }
    }
    ```

12. **What is a stream in Java?**
    - *A stream in Java is a sequence of elements supporting sequential and parallel aggregate operations. It is used for processing collections of objects in a functional style.*

13. **What is a parallel stream?**
    - *A parallel stream is a type of stream that enables parallel processing of data by splitting the data into multiple chunks and processing them concurrently.*

14. **What is the difference between a stream and a parallel stream?**
    - *A stream processes data sequentially, while a parallel stream divides the data into multiple chunks and processes them concurrently using multiple threads.*

15. **How does the internal process work in parallel streams?**
    - *Parallel streams use the ForkJoinPool to split the data into smaller chunks, process them concurrently in multiple threads, and then merge the results.*

16. **How many ways can we create a thread in Java?**
    - *Threads can be created in two main ways:*
      - *By implementing the `Runnable` interface*
      - *By extending the `Thread` class*

17. **Provide example code for implementing the `Runnable` interface and explain how to use it.**

    ```java
    public class RunnableExample implements Runnable {
        @Override
        public void run() {
            System.out.println("Thread is running");
        }

        public static void main(String[] args) {
            RunnableExample runnable = new RunnableExample();
            Thread thread = new Thread(runnable);
            thread.start();
        }
    }
    ```

18. **If `MyThread` implements `Runnable`, and I create a thread like this: `Thread t = new Thread(new MyThread())`, how is this different from extending the `Thread` class?**
    - *Implementing `Runnable` allows you to use composition and separate the thread's job from its execution. Extending `Thread` tightly couples the thread's job with its execution, limiting flexibility.*

19. **What is `ExecutorService` in threads?**
    - *`ExecutorService` is a high-level replacement for managing and controlling thread execution. It provides methods for managing a pool of threads and scheduling tasks.*

20. **How many ways can we create an `ExecutorService`?**
    - *`ExecutorService` can be created using:* 
      - *`Executors.newFixedThreadPool(int nThreads)`*
      - *`Executors.newSingleThreadExecutor()`*
      - *`Executors.newCachedThreadPool()`*
      - *`Executors.newScheduledThreadPool(int corePoolSize)`*

21. **What is autowiring in Spring?**
    - *Autowiring is a feature in Spring that allows the framework to automatically inject dependencies into a bean.*

22. **How many modes of autowiring are there?**
    - *Autowiring modes include:* 
      - *`@Autowired` (by type)*
      - *`@Qualifier` (by name)*
      - *`@Resource` (by name)*
      - *`@Inject` (by type)*

24. **Explain `@Qualifier` and `@Inject`.**
    - *`@Qualifier` is used to provide specific beans when multiple candidates are available. `@Inject` is a Java standard annotation used to inject dependencies.*

25. **What is the difference between `@Autowired` and `@Qualifier`?**
    - *`@Autowired` is used for automatic injection by type, while `@Qualifier` is used in conjunction with `@Autowired` to specify which bean to inject when multiple beans are available.*

26. **Can we use `@Autowired` in place of `@Qualifier`?**
    - *`@Autowired` alone cannot specify which bean to inject if there are multiple candidates. `@Qualifier` is needed to resolve such ambiguities.*

27. **What are the limitations of autowiring?**
    - *Limitations include:* 
      - *Ambiguity when multiple beans of the same type are available.*
      - *Difficulty in identifying dependencies at runtime.*
      - *Inability to inject beans based on dynamic conditions.*

28. **What is Spring Security?**
    - *Spring Security is a framework that provides comprehensive security services for Java applications, including authentication, authorization, and protection against various security threats.*

29. **How do you configure Spring Security?**
    - *Spring Security can be configured using:* 
      - *Java configuration with `@EnableWebSecurity` and `SecurityConfig` classes.*
      - *XML configuration (less common in recent versions).*

30. **What is JWT token-based authentication?**
    - *JWT (JSON Web Token) token-based authentication is a method where authentication information is transmitted as a JSON object and is used to verify the identity of users.*

31. **How many ways can you configure custom security?**
    - *Custom security can be configured using:* 
      - *Java-based configuration with `SecurityConfigurerAdapter`*
      - *Custom filters and handlers*
      - *Spring Security extensions*

32. **What is an API gateway?**
    - *An API gateway is a server that acts as an API front-end, receiving API requests, enforcing throttling, routing requests, and aggregating results.*

33. **How to implement an API gateway? Which dependency is needed?**
    - *To implement an API gateway, you can use tools like Spring Cloud Gateway or Netflix Zuul. Dependencies needed include:* 
      - *`spring-cloud-starter-gateway` for Spring Cloud Gateway*
      - *`zuul` for Netflix Zuul*

34. **What is load balancing?**
    - *Load balancing distributes incoming network traffic across multiple servers to ensure no single server becomes overwhelmed, enhancing reliability and performance.*

35. **How do you implement load balancing in microservices?**
    - *Load balancing in microservices can be implemented using:* 
      - *Client-side load balancing with libraries like Ribbon*
      - *Server-side load balancing with tools like Nginx or HAProxy*

36. **What is fault tolerance?**
    - *Fault tolerance refers to the ability of a system to continue operating properly in the event of a failure of some of its components.*

37. **How do you handle fault tolerance?**
    - *Fault tolerance can be handled using:* 
      - *Redundancy and failover strategies*
      - *Circuit breakers (e.g., using Resilience4j)*
      - *Retry mechanisms and fallback methods*

38. **What is a circuit breaker

?**
    - *A circuit breaker is a design pattern that prevents a system from making calls to a failing service, allowing it to recover and preventing cascading failures.*

39. **How do you implement a circuit breaker?**
    - *A circuit breaker can be implemented using libraries like:* 
      - *Resilience4j*
      - *Hystrix*

40. **What is the design pattern for a circuit breaker?**
    - *The circuit breaker pattern consists of three states:* 
      - *Closed (normal operation)*
      - *Open (service is failing)*
      - *Half-Open (test if the service has recovered)*

41. **How do you handle limits in a circuit breaker?**
    - *Limits in a circuit breaker can be handled by:* 
      - *Setting thresholds for failure rates*
      - *Defining timeout durations for service calls*
      - *Configuring retry and fallback mechanisms*

42. **What are the features of RESTful web services?**
    - *Features include:* 
      - *Stateless communication*
      - *Resource-based URLs*
      - *Standard HTTP methods (GET, POST, PUT, DELETE)*
      - *JSON or XML responses*
      - *HTTP status codes for responses*

43. **What are the available HTTP status codes, and why are they important?**
    - *Common HTTP status codes include:* 
      - *200 OK*
      - *201 Created*
      - *204 No Content*
      - *400 Bad Request*
      - *401 Unauthorized*
      - *404 Not Found*
      - *500 Internal Server Error*
    - *They are important for indicating the result of an HTTP request and guiding client-side behavior.*

44. **Which database are you using?**
    - *Provide the name of the database you are using (e.g., MySQL, PostgreSQL, MongoDB) and any relevant details about its configuration and usage.*

45. **Write a query to get the username when the name starts with 'A' and ends with 'E'.**

    ```sql
    SELECT username 
    FROM users 
    WHERE name LIKE 'A%E';
    ```

46. **Write an SQL query to find the 2nd maximum salary.**

    ```sql
    SELECT MAX(salary) 
    FROM employees 
    WHERE salary < (SELECT MAX(salary) FROM employees);
    ```

47. **Write an SQL query to find the 10th maximum salary.**

    ```sql
    SELECT salary 
    FROM (
        SELECT DISTINCT salary 
        FROM employees 
        ORDER BY salary DESC 
        LIMIT 10
    ) AS temp 
    ORDER BY salary ASC 
    LIMIT 1;
    ```

48. **What is the difference between the `WHERE` and `HAVING` clauses?**
    - *The `WHERE` clause filters rows before any groupings are made, while the `HAVING` clause filters groups after the `GROUP BY` operation.*

49. **Give an example of using the `HAVING` clause.**

    ```sql
    SELECT department, COUNT(*) 
    FROM employees 
    GROUP BY department 
    HAVING COUNT(*) > 10;
    ```

50. **Can you use grouping in the `WHERE` clause?**
    - *No, grouping and aggregation functions must be used with the `HAVING` clause, not the `WHERE` clause.*

51. **Write a Java code snippet to find names starting with 'A' using streams.**

    ```java
    import java.util.Arrays;
    import java.util.List;
    import java.util.stream.Collectors;

    public class StreamExample {
        public static void main(String[] args) {
            List<String> names = Arrays.asList("Alice", "Bob", "Andrew", "Amanda", "George");

            List<String> result = names.stream()
                                       .filter(name -> name.startsWith("A"))
                                       .collect(Collectors.toList());

            System.out.println(result); // Output: [Alice, Andrew, Amanda]
        }
    }
    ```

52. **Given the number 6178, how many iterations are required to reach 1629 and 99? Write the code logic to solve this.**
Solution Explanation:
8716 - 6178 = 2538
8352 - 2538 = 5814
5814 - 4185 = 1629
9261 - 1629 = 7632
7632 - 2367 = 5265
5625 - 5265 = 0360
0360 - 0036 = 0324
0423 - 0324 = 0495
5490 - 0495 = 4995
5994 - 4995 = 099

    ```java
    import java.util.Arrays;

    public class KaprekarRoutine {
        public static void main(String[] args) {
            int number = 6178;
            int iterations = 0;

            while (number != 6174 && number != 99) {
                number = performKaprekarIteration(number);
                System.out.println("Current number: " + number);
                iterations++;
            }

            System.out.println("Total iterations: " + iterations);
        }

        private static int performKaprekarIteration(int number) {
            String numStr = String.format("%04d", number); // Pad with zeros if necessary
            char[] numChars = numStr.toCharArray();
            
            Arrays.sort(numChars); // Ascending order
            int smallNum = Integer.parseInt(new String(numChars));
            
            // Reverse the order for descending
            String largeStr = new StringBuilder(new String(numChars)).reverse().toString();
            int largeNum = Integer.parseInt(largeStr);
            
            return largeNum - smallNum;
        }
    }
    ```

# Client Round 

# PayPal client interview (L1):

---

### 1. **Self-introduction about your project:**
   - Briefly describe your project, its objective, technologies used (e.g., Java, Spring Boot, ReactJS), and your role (backend developer, full stack developer). Mention any key features, challenges faced, and how you solved them.

### 2. **Do you know SQL?**
   - Yes, SQL is a standard language used to manage and manipulate relational databases. I have experience with queries like `SELECT`, `INSERT`, `UPDATE`, `DELETE`, and handling joins, indexes, and stored procedures.

### 3. **Do you know Data Structures and Algorithms (LinkedList)?**
   - Yes, LinkedList is a data structure where each element (node) contains data and a reference (or pointer) to the next node. There are two types: singly linked and doubly linked lists.

### 4. **Do you know OOP concepts? Can you explain what they are?**
   - OOP (Object-Oriented Programming) concepts include:
     1. **Encapsulation:** Wrapping data (variables) and code (methods) together.
     2. **Abstraction:** Hiding complexity by providing a simplified interface.
     3. **Inheritance:** Deriving new classes from existing ones.
     4. **Polymorphism:** The ability to use the same function in different forms.

### 5. **What is polymorphism?**
   - Polymorphism allows one interface to be used for different data types. In Java, it can be achieved through method overloading and method overriding.

### 6. **What is method overloading, and what is method overriding?**
   - **Method Overloading:** Multiple methods with the same name but different parameters (within the same class).
   - **Method Overriding:** A subclass provides a specific implementation of a method already defined in its parent class.

### 7. **How can you declare your override?**
   - By using the `@Override` annotation before the method in the subclass.

### 8. **What are access modifiers?**
   - Access modifiers define the scope of access to classes, variables, and methods:
     - `private`: Accessible only within the same class.
     - `protected`: Accessible within the same package and subclasses.
     - `public`: Accessible everywhere.
     - (default): Accessible within the same package.

### 9. **Why use `private`?**
   - To restrict access to the class members and maintain encapsulation, ensuring controlled access through getters and setters.

### 10. **If you provide a variable as `private`, what happens? How can you set and get the value of that private variable?**
   - The variable will be inaccessible from outside the class. You can set and get the value using public getter and setter methods.

### 11. **Which OOP concept can achieve private variables?**
   - **Encapsulation** ensures private variables can be controlled through public methods like getters and setters.

### 12. **Do you know about `String`? Can you explain?**
   - A `String` in Java is an immutable sequence of characters. It is stored in the string pool for memory efficiency.

### 13. **What is the difference between `String`, `StringBuilder`, and `StringBuffer`?**
   - `String`: Immutable.
   - `StringBuilder`: Mutable and not thread-safe.
   - `StringBuffer`: Mutable and thread-safe (synchronized).

### 14. **What is the string constant pool?**
   - It's a special memory area in the Java heap where `String` literals are stored to optimize memory usage and avoid duplicate string objects.

### 15. **Given the pseudo-code `String str1="abc"`, `String str2="abc"`, `str1 == str2`, what will be the output?**
   - The output will be `true` because both `str1` and `str2` point to the same literal in the string constant pool.

### 16. **What is an inner class, and why is it useful?**
   - An inner class is a class defined within another class. It’s useful to logically group classes, improve encapsulation, and access outer class members.

### 17. **What is an anonymous class, and why is it used?**
   - An anonymous class is a class without a name, often used to instantiate a one-time object. It’s useful for event handling or passing functionality without creating separate named classes.

### 18. **Have you worked with multithreading?**
   - Yes, multithreading allows concurrent execution of two or more threads, improving the performance of tasks like I/O, database calls, etc.

### 19. **How many ways are there to create a thread?**
   - Two ways:
     1. By extending the `Thread` class.
     2. By implementing the `Runnable` interface.

### 20. **Have you used the `Future` class?**
   - Yes, the `Future` class in Java represents the result of an asynchronous computation, allowing you to check if the task is complete, retrieve the result, or cancel the task.

### 21. **Have you used `Callable`?**
   - Yes, `Callable` is an interface similar to `Runnable`, but it returns a result and can throw a checked exception.

### 22. **Which collections have you used?**
   - I've used various collections like `ArrayList`, `HashSet`, `HashMap`, `LinkedList`, and `TreeMap`.

### 23. **What is the retrieval time complexity of `HashMap`?**
   - The average time complexity for retrieving an element in a `HashMap` is O(1), assuming good hash function distribution.

### 24. **How does `HashMap` work internally?**
   - `HashMap` uses an array of buckets where each bucket is a linked list. The key's hashcode determines the bucket, and keys with the same hashcode are handled via linked lists (or trees in case of hash collision).

### 25. **What is hash collision?**
   - Hash collision occurs when two different keys generate the same hashcode. Java resolves this through linked lists or balanced trees inside the bucket.

### 26. **What is `final`, and how does it work with variables, methods, and classes?**
   - `final` prevents modification:
     - **Variable**: Value cannot be changed after initialization.
     - **Method**: Cannot be overridden.
     - **Class**: Cannot be extended.

### 27. **How can you handle exceptions? Have you used custom exceptions?**
   - Exceptions are handled using `try-catch` blocks. Yes, I have used custom exceptions to create application-specific error messages by extending the `Exception` class.

### 28. **Give me mostly used Spring Boot exceptions.**
   - Common exceptions include `DataIntegrityViolationException`, `HttpClientErrorException`, `HttpServerErrorException`, `EntityNotFoundException`.

### 29. **What is the difference between `throw` and `throws`?**
   - `throw`: Used to explicitly throw an exception.
   - `throws`: Declares that a method can throw one or more exceptions.

### 30. **What is the difference between checked and unchecked exceptions?**
   - **Checked exceptions** must be handled at compile-time (e.g., `IOException`).
   - **Unchecked exceptions** occur at runtime (e.g., `NullPointerException`).

### 31. **What are `try`, `catch`, and `finally`? When do we use them?**
   - `try` defines the code block to monitor for exceptions.
   - `catch` handles the exception.
   - `finally` executes code after `try-catch`, regardless of an exception.

### 32. **If `try` contains multiple catch blocks, which catch block will execute? If there is a `finally` block, what will be the output?**
   - The first matching `catch` block will execute. The `finally` block will always execute after the `catch` block, regardless of the exception.

### 33. **If a single `catch` can handle multiple exceptions, which exception will it handle?**
   - It will handle whichever exception occurs that is listed in the `catch` block. Java allows multi-catch blocks using `|`.

### 34. **Have you worked with Java 8?**
   - Yes, I have used features like Lambdas, Streams, Optional, and the Date-Time API.

### 35. **What are the Java 9 features?**
   - Key features include JShell (REPL), Module System, Factory Methods for Collections, Stream API improvements, and Private Interface Methods.

### 36. **If I provide the string "leetcode" and the character "e", can you find how many times "e" occurs using streams?**
   ```java
   long count = "leetcode".chars().filter(ch -> ch == 'e').count();
   ```

### 37. **Which data structure are you familiar with?**
   - I am familiar with LinkedList, ArrayList, HashMap, Stack, Queue, etc.

### 38. **Select any data structure: LinkedList, Stack, or Queue.**
   - Let's take LinkedList, which stores elements as nodes where each node points to the next node.

### 39. **Write code logic: If I provide the head of a linked list, determine if it is a cycle linked list or not.**
   ```java
   public boolean hasCycle(ListNode head) {
       if (head == null) return false;
       ListNode slow = head, fast =

 head.next;
       while (slow != fast) {
           if (fast == null || fast.next == null) return false;
           slow = slow.next;
           fast = fast.next.next;
       }
       return true;
   }
   ```

### 40. **What is the time complexity and space complexity of the code to detect a cycle in a linked list?**
   - **Time complexity:** O(n) - We traverse the linked list only once, making the time complexity linear.
   - **Space complexity:** O(1) - We use a constant amount of extra space (two pointers).

### 41. **What is the `Optional` class?**
   - The `Optional` class in Java is used to avoid `null` pointer exceptions by representing a value that may or may not be present. It provides methods like `isPresent()`, `get()`, `orElse()`, and `ifPresent()` to handle the value safely.

### 42. **What is a functional interface?**
   - A functional interface in Java is an interface that contains exactly one abstract method. It can have multiple default or static methods. Functional interfaces can be implemented using lambda expressions. Example: `Runnable`, `Callable`, `Comparator`.

### 43. **What are the built-in functional interfaces available in Java?**
   - Some of the built-in functional interfaces in Java are:
     - `Function<T, R>`: Takes one argument and returns a result.
     - `Consumer<T>`: Takes one argument and returns no result.
     - `Supplier<T>`: Takes no argument and returns a result.
     - `Predicate<T>`: Takes one argument and returns a boolean.
     - `BiFunction<T, U, R>`, `BiConsumer<T, U>`, `BiPredicate<T, U>`: Same as the above but with two arguments.

### 44. **How can we write methods in a functional interface, and how can we utilize those methods?**
   - You define a functional interface by declaring one abstract method, then implement it using a lambda expression. For example:
   ```java
   @FunctionalInterface
   interface MathOperation {
       int operate(int a, int b);
   }

   public class Main {
       public static void main(String[] args) {
           MathOperation addition = (a, b) -> a + b;
           System.out.println("Result: " + addition.operate(5, 3));
       }
   }
   ```

### 45. **Do you know `CompletableFuture`?**
   - Yes, `CompletableFuture` is a feature of Java 8 that is used to handle asynchronous programming. It allows you to run tasks asynchronously and chain multiple stages of computations. It supports combining multiple asynchronous computations and handling exceptions.

### 46. **Have you worked with Spring Boot?**
   - Yes, I have worked with Spring Boot extensively. It simplifies building stand-alone, production-grade Spring-based applications. It provides default configurations and a wide range of annotations to reduce boilerplate code.

### 47. **What is configuration and auto-configuration in Spring Boot?**
   - **Configuration** refers to the settings and beans required to run the Spring Boot application.
   - **Auto-configuration** is a feature in Spring Boot that automatically configures your application based on the dependencies in the classpath. It reduces the need for manual configuration.

### 48. **What is `@Component`?**
   - `@Component` is a Spring annotation used to indicate that a class is a Spring-managed bean. The Spring container automatically detects and registers beans marked with `@Component` for dependency injection.

### 49. **Can you explain `@Controller`, `@Service`, and `@Repository`?**
   - **`@Controller`**: Marks a class as a Spring MVC controller, typically used to handle web requests.
   - **`@Service`**: Indicates a service layer class that contains business logic. It is used for business operations and service orchestration.
   - **`@Repository`**: Marks a data access layer class that interacts with the database, translating exceptions into Spring’s DataAccessException.

### 50. **Do you know MVC?**
   - Yes, MVC (Model-View-Controller) is a software architectural pattern that separates an application into three main logical components:
     - **Model**: Manages the data and business logic.
     - **View**: Responsible for rendering the UI.
     - **Controller**: Handles user input and controls the flow of data between the Model and View.

### 51. **Can you explain the MVC architecture?**
   - In the MVC architecture:
     - **Model**: Represents the data and the business logic of the application.
     - **View**: Renders the UI, based on the data provided by the Model.
     - **Controller**: Handles the input from the user, updates the Model, and selects the View to display.

### 52. **What is the difference between SOAP and RESTful services?**
   - **SOAP** (Simple Object Access Protocol) is a protocol used for exchanging structured information in web services. It uses XML as its message format and operates over various protocols like HTTP, SMTP, etc.
   - **REST** (Representational State Transfer) is an architectural style for building web services, using standard HTTP methods (GET, POST, PUT, DELETE) and typically communicates using JSON or XML.

### 53. **What are the features of RESTful services?**
   - RESTful services are:
     - Stateless: Each request from the client must contain all the information required for the server to understand and process the request.
     - Cacheable: Responses can be marked as cacheable to improve performance.
     - Scalable: REST is designed to handle high-load scenarios efficiently.
     - Layered: RESTful systems allow layering of services.

### 54. **You mentioned you worked on microservices, so give me an example API you worked on (e.g., notification services). How does it work? How would you create it in code?**
   - Example: A notification service in a microservice architecture can be responsible for sending notifications (email, SMS, etc.) to users.
     1. **Controller**: The user triggers a notification request.
     2. **Service**: Business logic determines the notification type and message.
     3. **Repository**: Interacts with the database to fetch necessary data (like user preferences, templates).
     4. **External API**: Calls the external notification provider (e.g., email or SMS API).
   
   Here's an example Spring Boot API for sending email notifications:
   ```java
   @RestController
   @RequestMapping("/api/notification")
   public class NotificationController {
       @Autowired
       private NotificationService notificationService;

       @PostMapping("/send")
       public ResponseEntity<String> sendNotification(@RequestBody NotificationRequest request) {
           notificationService.sendNotification(request);
           return ResponseEntity.ok("Notification sent successfully");
       }
   }

   @Service
   public class NotificationService {
       public void sendNotification(NotificationRequest request) {
           // Logic to send notification (e.g., email, SMS)
       }
   }
   ```
---

# PayPal client interview (L2):

### 1. Self-introduction based on project
I have been working on a [your project name] for [duration], focusing on full-stack development with technologies like ReactJS on the front end and Spring Boot on the backend. The project involves creating customer registration services, handling transactions, and managing user data. I am responsible for developing APIs, integrating third-party services, and ensuring smooth user experiences. I've also worked on cloud deployments, particularly with GCP, where I implemented features such as auto-scaling and cloud storage integration.

### 2. Which GCP concepts have you used?
- Compute Engine for virtual machine management.
- Google Cloud Storage for object storage.
- Pub/Sub for messaging between services.
- Cloud SQL for managed relational databases.
- Cloud Load Balancing for distributing traffic.
- Stackdriver for monitoring and logging.

### 3. Are you compatible with Java 8 streams?
Yes, I am proficient with Java 8 streams. I use them for operations like filtering, mapping, reducing, and collecting data, which allows for a more functional programming approach.

### 4. You have one list; can you find how many times a given string occurs using streams?
```java
List<String> list = Arrays.asList("apple", "banana", "apple", "orange", "apple");
long count = list.stream().filter(s -> s.equals("apple")).count();
System.out.println(count);  // Output: 3
```

### 5. You have a list of strings; find the occurrence of each string using streams.
```java
List<String> list = Arrays.asList("apple", "banana", "apple", "orange", "banana");
Map<String, Long> result = list.stream()
    .collect(Collectors.groupingBy(Function.identity(), Collectors.counting()));
System.out.println(result);  // Output: {banana=2, orange=1, apple=2}
```

### 6. What is the difference between HashMap vs LinkedHashMap?
- **HashMap**: Does not maintain insertion order.
- **LinkedHashMap**: Maintains insertion order or access order.

### 7. You have `String s1="hello"` and `String s2="hellow"`. What happens when using `==` and `.equals()`?
- `==`: Compares reference, so `s1 == s2` returns `false` because they point to different objects.
- `.equals()`: Compares value, so `s1.equals(s2)` returns `false` because their content is different.

### 8. What are exceptions, and can you give types of exceptions?
Exceptions are events that disrupt normal program execution.
- **Checked Exceptions**: Must be handled or declared, e.g., `IOException`.
- **Unchecked Exceptions**: Include runtime exceptions like `NullPointerException`, `ArithmeticException`.

### 9. What is a checked exception and unchecked exception? Give an example.
- **Checked Exception**: Needs explicit handling.
  ```java
  try {
      FileReader file = new FileReader("file.txt");
  } catch (FileNotFoundException e) {
      e.printStackTrace();
  }
  ```
- **Unchecked Exception**: Occurs at runtime.
  ```java
  int a = 10 / 0;  // ArithmeticException
  ```

### 10. How strong are you in Java theory and programming? Give a rating out of 10.
I would rate myself 8 out of 10.

### 11. Which data structures are you familiar with?
Arrays, Lists, Maps, Sets, Stacks, Queues, and Trees.

### 12. What is the difference between Stack and Queue?
- **Stack**: Follows LIFO (Last In First Out).
- **Queue**: Follows FIFO (First In First Out).

### 13. Have you used try-with-resources? Give an example code.
```java
try (FileReader reader = new FileReader("file.txt")) {
    // Use the reader
} catch (IOException e) {
    e.printStackTrace();
}
```

### 14. When does a finally block never execute?
- When `System.exit()` is called.
- If a fatal JVM error occurs.

### 15. Given the code:
```java
int division(int a, int b) { 
    try {
        return a / b;
    } finally {
        System.out.print("finally");
    }
}
```
**Output**: It prints "finally" and returns `5` (for inputs `10, 2`).

### 16. How to create a custom exception? Give example code.
```java
class CustomException extends Exception {
    public CustomException(String message) {
        super(message);
    }
}
```

### 17. What is a static method?
A method that belongs to the class rather than any specific instance. It can be called without creating an object of the class.

### 18. If you have a class with a static method, is it possible to override it in a subclass?
No, static methods cannot be overridden, but they can be hidden in a subclass.

### 19. What is the diamond problem?
Occurs in languages that allow multiple inheritance, causing ambiguity. Java avoids this through interfaces with default methods.

### 20. What is the difference between a Java 7 interface and a Java 8 interface?
- **Java 7 Interface**: Only abstract methods.
- **Java 8 Interface**: Can have default and static methods.

### 21. You have an array `arr[]={2,4,6,8,9}`; how can you efficiently find the index of element 6? Write code logic and explain.
```java
import java.util.Arrays;

public class BinarySearchExample {
    public static void main(String[] args) {
        int[] arr = {2, 4, 6, 8, 9};
        int target = 6;

        int index = Arrays.binarySearch(arr, target);
        
        if (index >= 0) {
            System.out.println("Element found at index: " + index);
        } else {
            System.out.println("Element not found");
        }
    }
}

```

### 22. If you have a Java-based logic to fetch data from a database and use a join query to get data, which one is faster?
Fetching data using a join query in SQL is generally faster because the database engine is optimized for such operations.

### 23. How do you get data from the database in Spring Boot?
Using Spring Data JPA repositories:
```java
@Autowired
private UserRepository userRepository;

List<User> users = userRepository.findAll();
```

### 24. When you have a list containing data and want to remove data in the middle, which collection is best?
`LinkedList` is better because it allows faster insertions and deletions in the middle.

### 25. If you have one list and it's iteration time, can you remove an element?
Yes, using `Iterator.remove()` to avoid `ConcurrentModificationException`.

### 26. If you create a list using `List.of()` method, can you add data additionally?
No, `List.of()` creates an immutable list.

### 27. Do you know design patterns?
Yes, I am familiar with Singleton, Factory, Observer, and other design patterns.

### 28. What is the Singleton design pattern?
A design pattern that ensures a class has only one instance and provides global access to it.

### 29. Write a code logic for the Singleton design pattern.
```java
public class Singleton {
    private static Singleton instance;

    private Singleton() {}

    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

### 30. What is the default Spring Boot design pattern?
The default design pattern in Spring Boot is the **Dependency Injection** pattern.

### 31. If you have multiple catch blocks, how do you handle which exception? Give an example.
```java
try {
    // code
} catch (IOException e) {
    // handle IOException
} catch (Exception e) {
    // handle all other exceptions
}
```

### 32. If I catch a general exception and then catch an arithmetic exception, what will happen? Write code and explain.
The more specific exception (ArithmeticException) should be caught first.
```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Arithmetic Exception");
} catch (Exception e) {
    System.out.println("General Exception");
}
```
Output: "Arithmetic Exception".

### 33. How familiar are you with SQL queries?
I am quite familiar and can write complex queries with joins, subqueries, and aggregate functions.

### 34. What are the joins available in SQL?
- Inner Join
- Left Join (Left Outer Join)
- Right Join (Right Outer Join)
- Full Join (Full Outer Join)

### 35. Explain briefly about all SQL joins.
- **Inner Join**: Returns records that have matching values in both tables.
- **Left Join**: Returns all records from the left table and matched records from the right table.
- **Right Join**: Returns all records from the right table and matched records from the left table.
- **Full Join**: Returns all records when there is a match in either left or right table.

### 36. Why is the main method static?
The `main` method is static because it allows the JVM to invoke it without instantiating the class.

### 37. What is polymorphism?
Polymorphism allows one interface to be used for different data types, typically achieved through method overloading or overriding.

### 38. What is method overloading and method overriding? Give example code.
- **Method Overloading**: Same method name, different parameters.
- **Method Overriding**: Subclass redefines a method from the parent class.

Overloading:
```java
class Example {
    void print(int a) {}
    void print(String a

) {}
}
```

Overriding:
```java
class Parent {
    void show() {}
}

class Child extends Parent {
    @Override
    void show() {}
}
```

### 39. Based on the tables `menu -> mid, itemid`, `order -> oid, cid, orderdate`, `customer -> cid, cname, address`, find order ID based on customer name.
```sql
SELECT order.oid 
FROM order 
INNER JOIN customer ON order.cid = customer.cid 
WHERE customer.cname = 'customer_name';
```

### 40. Given employee data with id=1, sal=1000; id=2, sal=2000; id=3, sal=10000, find the second maximum salary.
```sql
SELECT MAX(salary) FROM employees WHERE salary < (SELECT MAX(salary) FROM employees);
```

### 41. What is dependency injection? Give an example.
Dependency Injection is a design pattern where an object's dependencies are provided rather than hard-coded within the object.
```java
@Service
public class MyService {
    private final MyRepository repository;

    @Autowired
    public MyService(MyRepository repository) {
        this.repository = repository;
    }
}
```

### 42. How many ways can dependency injection be done?
- Constructor Injection
- Setter Injection
- Field Injection (not recommended)

# HR  
--package, self
