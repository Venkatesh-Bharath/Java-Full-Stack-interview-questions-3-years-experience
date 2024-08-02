1. **What are the main features introduced in Java 8?**
   - Lambda Expressions
   - Functional Interfaces
   - Streams API
   - Default Methods in Interfaces
   - Optional Class
   - New Date and Time API (java.time)
   - Nashorn JavaScript Engine
   - Method References

2. **What are the key differences between an interface and an abstract class in Java?**
   - Interfaces can only have abstract methods (until Java 8, which introduced default and static methods), while abstract classes can have both abstract and concrete methods.
   - A class can implement multiple interfaces but can inherit from only one abstract class.
   - Interfaces cannot have instance variables, while abstract classes can.
   - Interfaces provide a form of multiple inheritance; abstract classes provide a form of single inheritance.

3. **How do you implement Executor Services in Java?**
   ```java
   import java.util.concurrent.ExecutorService;
   import java.util.concurrent.Executors;
   
   public class ExecutorServiceExample {
       public static void main(String[] args) {
           ExecutorService executor = Executors.newFixedThreadPool(5);
   
           for (int i = 0; i < 10; i++) {
               Runnable worker = new WorkerThread("" + i);
               executor.execute(worker);
           }
           executor.shutdown();
           while (!executor.isTerminated()) {
           }
           System.out.println("Finished all threads");
       }
   }
   
   class WorkerThread implements Runnable {
       private String command;
   
       public WorkerThread(String s) {
           this.command = s;
       }
   
       @Override
       public void run() {
           System.out.println(Thread.currentThread().getName() + " Start. Command = " + command);
           processCommand();
           System.out.println(Thread.currentThread().getName() + " End.");
       }
   
       private void processCommand() {
           try {
               Thread.sleep(5000);
           } catch (InterruptedException e) {
               e.printStackTrace();
           }
       }
   }
   ```

4. **Which databases have you used in your projects, and what was your experience with them?**
   - **MySQL:** Used for web applications; strong support for transactions and data integrity.
   - **PostgreSQL:** Preferred for complex queries and large datasets; excellent support for JSON data types and extensions.
   - **MongoDB:** Utilized for handling unstructured data and fast prototyping; great for horizontal scaling.
   - **Oracle:** Employed in enterprise-level applications requiring robust security and advanced features.

5. **How can you declare and use functional programming constructs in Java?**
   ```java
   // Lambda Expression
   List<String> names = Arrays.asList("John", "Jane", "Jack");
   names.forEach(name -> System.out.println(name));

   // Functional Interface Example
   @FunctionalInterface
   interface MathOperation {
       int operation(int a, int b);
   }

   MathOperation addition = (a, b) -> a + b;
   System.out.println("10 + 5 = " + addition.operation(10, 5));
   ```

6. **What are the differences between `@RestController` and `@Controller` in Spring Boot?**
   - `@RestController` is a combination of `@Controller` and `@ResponseBody`. It automatically serializes return objects into JSON or XML and writes them into the HTTP response.
   - `@Controller` is used to mark classes as Spring MVC controllers. Methods in these classes typically return view names and are resolved by view resolvers.

7. **How do you schedule tasks in Spring Boot?**
   ```java
   import org.springframework.scheduling.annotation.Scheduled;
   import org.springframework.stereotype.Component;
   
   @Component
   public class ScheduledTasks {
   
       @Scheduled(fixedRate = 5000)
       public void reportCurrentTime() {
           System.out.println("The time is now " + new Date());
       }
   }
   ```

8. **How is Jenkins integrated with Spring Boot? What dependencies or configuration files are needed?**
   - **Jenkinsfile:**
     ```groovy
     pipeline {
         agent any
         stages {
             stage('Build') {
                 steps {
                     sh './mvnw clean package'
                 }
             }
             stage('Test') {
                 steps {
                     sh './mvnw test'
                 }
             }
             stage('Deploy') {
                 steps {
                     sh 'docker build -t spring-boot-app .'
                     sh 'docker run -d -p 8080:8080 spring-boot-app'
                 }
             }
         }
     }
     ```
   - **Dependencies:**
     - Jenkins server
     - Maven or Gradle for build automation
     - Docker for containerization (if deploying with Docker)

9. **What is the difference between `HashMap` and `ConcurrentHashMap` in Java?**
   - `HashMap` is not synchronized and is not thread-safe.
   - `ConcurrentHashMap` is thread-safe and allows concurrent access to its segments.

10. **What are the key classes and interfaces in the `java.util.concurrent` package?**
    - **Key Classes:** `ExecutorService`, `ScheduledExecutorService`, `Future`, `CountDownLatch`, `CyclicBarrier`, `Semaphore`, `ConcurrentHashMap`, `CopyOnWriteArrayList`
    - **Key Interfaces:** `Executor`, `Callable`, `Future`, `BlockingQueue`

11. **Describe the collections framework in Java.**
    - **Core Interfaces:** `Collection`, `List`, `Set`, `Queue`, `Map`
    - **Implementations:** `ArrayList`, `LinkedList`, `HashSet`, `TreeSet`, `PriorityQueue`, `HashMap`, `TreeMap`
    - **Utilities:** `Collections`, `Arrays`

12. **How do you use profiles in Spring Boot?**
    ```yaml
    # application.yml
    spring:
      profiles:
        active: dev
    ---
    # application-dev.yml
    server:
      port: 8081
    ---
    # application-prod.yml
    server:
      port: 8082
    ```

13. **If both `application.properties` and `application.yaml` are present in a Spring Boot application, which one takes precedence?**
    - `application.properties` takes precedence over `application.yaml`.

14. **Explain the `@Autowired` annotation in Spring.**
    - `@Autowired` is used for automatic dependency injection. Spring's dependency injection mechanism uses this annotation to resolve and inject collaborating beans into the desired bean.

15. **Using a lambda expression, write a Java program to sum the elements of an array.**
    ```java
    import java.util.Arrays;
    public class SumArray {
    public static void main(String[] args) {
        int[] array = {1, 2, 3, 4, 5};

        // Using a lambda expression with Stream API
        int sum = Arrays.stream(array)
                         .reduce(0, (a, b) -> a + b);

        System.out.println("Sum: " + sum);
      }
    }
    ```

16. **Write a Java program to generate all permutations of an array using lambda expressions.**
    ```java
    import java.util.ArrayList;
    import java.util.List;
    import java.util.stream.Collectors;
    import java.util.stream.IntStream;

    public class Permutations {
        public static void main(String[] args) {
            int[] array = {1, 2, 3};
            List<List<Integer>> result = permute(array);
            result.forEach(System.out::println);
        }

        public static List<List<Integer>> permute(int[] nums) {
            return permute(IntStream.range(0, nums.length).boxed().collect(Collectors.toList()), nums);
        }

        private static List<List<Integer>> permute(List<Integer> indices, int[] nums) {
            if (indices.isEmpty()) {
                List<Integer> perm = new ArrayList<>();
                for (int num : nums) {
                    perm.add(num);
                }
                return List.of(perm);
            }

            return indices.stream()
                .flatMap(i -> {
                    List<Integer> remaining = new ArrayList<>(indices);
                    remaining.remove(Integer.valueOf(i));
                    return permute(remaining, swap(nums, i)).stream();
                })
                .collect(Collectors.toList());
        }

        private static int[] swap(int[] array, int i) {
            int[] newArray = array.clone();
            int temp = newArray[i];
            newArray[i] = newArray[0];
            newArray[0] = temp;
            return newArray;
        }
    }
    ```
**Etc...**
