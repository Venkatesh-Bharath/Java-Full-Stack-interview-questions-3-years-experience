# HCL L1 

1. **Brief about the project:**
   - The project is focused on developing a distributed banking application that handles real-time transactions using microservices architecture. It includes features like customer registration, account management, and secure transaction processing. Technologies like Spring Boot, Kafka, Docker, and React are used, ensuring high scalability and reliability.

2. **Explain Kafka architecture:**
   - Kafka architecture consists of Producers, Consumers, Brokers, Topics, and Zookeeper. Producers send data to Kafka topics, while Consumers read data from these topics. Kafka Brokers manage the storage and retrieval of messages, and Zookeeper handles metadata, including leader election and partition management, ensuring Kafka's fault tolerance and distributed nature.

3. **What is Jenkins and how do you use it?**
   - Jenkins is an open-source automation server used for continuous integration and continuous delivery (CI/CD). It automates the build, test, and deployment processes, enabling faster and more reliable software delivery. I use Jenkins to trigger automated builds on code commits, run tests, and deploy applications to different environments.

4. **What are the features of Java 17?**
   - Java 17 includes several new features such as sealed classes, pattern matching for switch (preview), new macOS rendering pipeline, enhanced pseudo-random number generators, and the removal of the experimental AOT and JIT compilers. It also includes long-term support (LTS) for stability in enterprise applications.

5. **What are the features of Java 8?**
   - Java 8 introduced several major features, including Lambda expressions, the Stream API for functional-style operations on collections, the new Date and Time API (java.time), default methods in interfaces, and the Optional class to handle null values more gracefully.

6. **Create a single thread in Java using different approaches (code):**
   ```java
   // Using Thread class
   Thread thread1 = new Thread() {
       public void run() {
           System.out.println("Thread using Thread class");
       }
   };
   thread1.start();

   // Using Runnable interface
   Runnable runnable = () -> System.out.println("Thread using Runnable interface");
   Thread thread2 = new Thread(runnable);
   thread2.start();

   // Using ExecutorService
   ExecutorService executor = Executors.newSingleThreadExecutor();
   executor.submit(() -> System.out.println("Thread using ExecutorService"));
   executor.shutdown();
   ```

7. **Create a text input and password input in React and display them when a button is clicked using functional components:**
   ```javascript
   import React, { useState } from 'react';

   function App() {
       const [text, setText] = useState('');
       const [password, setPassword] = useState('');
       const [show, setShow] = useState(false);

       const handleClick = () => {
           setShow(true);
       };

       return (
           <div>
               <input 
                   type="text" 
                   placeholder="Enter text" 
                   value={text} 
                   onChange={(e) => setText(e.target.value)} 
               />
               <input 
                   type="password" 
                   placeholder="Enter password" 
                   value={password} 
                   onChange={(e) => setPassword(e.target.value)} 
               />
               <button onClick={handleClick}>Show</button>
               {show && (
                   <div>
                       <p>Text: {text}</p>
                       <p>Password: {password}</p>
                   </div>
               )}
           </div>
       );
   }

   export default App;
   ```

8. **Explain your weekly tasks:**
   - My weekly tasks typically involve developing new features, fixing bugs, and optimizing existing code for better performance. I collaborate with team members in daily stand-up meetings, work on writing unit and integration tests, and participate in code reviews. Additionally, I contribute to the continuous integration pipeline and ensure smooth deployments.

9. **What is Agile methodology?**
   - Agile methodology is an iterative approach to software development and project management. It emphasizes collaboration, flexibility, and customer feedback, allowing teams to deliver small, functional pieces of software incrementally. Agile promotes adaptive planning, evolutionary development, early delivery, and continuous improvement.

10. **What is Jira and how do you use it?**
    - Jira is a project management tool used for tracking tasks, bugs, and issues. It supports Agile methodologies like Scrum and Kanban. I use Jira to manage and prioritize tasks, track progress through sprints, create and assign issues, and document project workflows. Jira also integrates with CI/CD pipelines for automated updates.


# HCL L2

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

# HR 
1. **self-salary etc..**
