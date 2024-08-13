
# L1 Interview Questions
## Java Questions

1. **Briefly describe your project experience and the versions of languages you used.**
   - I have 3 years of experience in full-stack development using Java 8 and ReactJS. I've worked on customer registration services and transaction data handling in a bank application. For backend development, I utilized Spring Boot, Hibernate, and JPA. Additionally, I've worked on implementing unit tests using JUnit and Mockito.

2. **What are the features of Java 8?**
   - Java 8 introduced several key features, including lambda expressions, the Stream API, default methods in interfaces, the new java.time API for date and time, Optional class, and improvements in the Collections API.

3. **What is a lambda expression?**
   - A lambda expression is a concise way to represent a method interface using an expression. It provides a clear and concise way to write inline implementations of functional interfaces.

4. **What is a functional interface?**
   - A functional interface is an interface with exactly one abstract method. It can have multiple default or static methods. Functional interfaces are used as the types for lambda expressions and method references.

5. **What is a normal interface?**
   - A normal interface can have multiple abstract methods. It serves as a contract for implementing classes to provide specific behaviors.

6. **What is the difference between a functional interface and a normal interface?**
   - A functional interface has only one abstract method, making it suitable for lambda expressions, while a normal interface can have multiple abstract methods.

7. **Can I use lambda expressions in normal methods?**
   - Yes, lambda expressions can be used in any context where a functional interface is expected, including in normal methods.

8. **What is the difference between HashMap and ConcurrentHashMap?**
   - HashMap is not thread-safe and can have performance issues in a concurrent environment. ConcurrentHashMap is thread-safe, allowing concurrent read and write operations without blocking.

9. **Can multiple threads access ConcurrentHashMap?**
   - Yes, ConcurrentHashMap allows multiple threads to read and write simultaneously without locking the entire map.

10. **If I use ConcurrentHashMap and perform get and put operations at the same time, will it work?**
    - Yes, ConcurrentHashMap is designed to handle concurrent read and write operations safely and efficiently.

11. **How does HashMap work internally?**
    - HashMap uses an array of buckets, where each bucket is a linked list or tree. It calculates the hash code of the key, determines the index of the bucket, and stores the key-value pair in the appropriate bucket.

12. **What is a bucket in HashMap?**
    - A bucket is a slot in the HashMap's internal array, used to store key-value pairs that have the same hash code.

13. **What is the difference between map and flatMap?**
    - `map` transforms each element in the stream, while `flatMap` transforms each element to a stream and flattens the resulting streams into a single stream.

14. **What is the difference between throw and throws?**
    - `throw` is used to explicitly throw an exception in the code, while `throws` is used in the method signature to declare that the method can throw certain exceptions.

15. **What is the ternary operator in Java?**
    - The ternary operator is a concise way to express conditional logic. It takes the form `condition ? ifTrue : ifFalse`.

16. **Write a code to find the 3rd non-repeated character in the string "hi am Bharath".**
    ```java
    import java.util.LinkedHashMap;
    import java.util.Map;

    public class NonRepeatedCharacter {
        public static void main(String[] args) {
            String str = "hi am Bharath";
            System.out.println(getThirdNonRepeatedCharacter(str));
        }

        public static Character getThirdNonRepeatedCharacter(String str) {
            Map<Character, Integer> charCount = new LinkedHashMap<>();
            for (char c : str.toCharArray()) {
                charCount.put(c, charCount.getOrDefault(c, 0) + 1);
            }

            int count = 0;
            for (Map.Entry<Character, Integer> entry : charCount.entrySet()) {
                if (entry.getValue() == 1) {
                    count++;
                    if (count == 3) {
                        return entry.getKey();
                    }
                }
            }
            return null; // or throw an exception if you prefer
        }
    }
    ```

17. **Write a code to count every characters in the string "hi am Bharath".**
    ```java
    import java.util.HashMap;
    import java.util.Map;

    public class CharacterCount {
        public static void main(String[] args) {
            String str = "hi am Bharath";
            Map<Character, Integer> charCount = countCharacters(str);
            charCount.forEach((k, v) -> System.out.println(k + ": " + v));
        }

        public static Map<Character, Integer> countCharacters(String str) {
            Map<Character, Integer> charCount = new HashMap<>();
            for (char c : str.toCharArray()) {
                charCount.put(c, charCount.getOrDefault(c, 0) + 1);
            }
            return charCount;
        }
    }
    ```

18. **Given list1 = [1,2,4,6,7] and list2 = [3,5,4,6], print elements from list1 that are not present in list2.**
    ```java
    import java.util.Arrays;
    import java.util.List;
    import java.util.stream.Collectors;

    public class ListDifference {
        public static void main(String[] args) {
            List<Integer> list1 = Arrays.asList(1, 2, 4, 6, 7);
            List<Integer> list2 = Arrays.asList(3, 5, 4, 6);

            List<Integer> result = list1.stream()
                                        .filter(e -> !list2.contains(e))
                                        .collect(Collectors.toList());

            System.out.println(result);
        }
    }
    ```

19. **What is the Lombok dependency?**
    - Lombok is a Java library that helps reduce boilerplate code. It provides annotations to automatically generate getters, setters, constructors, equals, hashCode, toString, and other methods.

20. **What is a no-argument constructor in Lombok?**
    - In Lombok, the `@NoArgsConstructor` annotation generates a no-argument constructor for the class.

21. **What is serialization and where have you used it?**
    - Serialization is the process of converting an object into a byte stream for storage or transmission. I have used serialization in a bank project to serialize transaction statements for storage and retrieval.

22. **What is a serialization ID?**
    - A serialization ID (serialVersionUID) is a unique identifier for a Serializable class. It is used during deserialization to verify that the sender and receiver of a serialized object maintain compatibility.

23. **If two objects have the same serialization ID, what happens when calling another microservice with both serialized objects?**
    - If two objects have the same serialization ID, they are considered compatible for deserialization. However, it is crucial that their class definitions are compatible to avoid `InvalidClassException`.

24. **What is a String?**
    - A `String` is an immutable sequence of characters in Java. It is an instance of the `java.lang.String` class.

25. **What is a String pool?**
    - The String pool is a special memory region where Java stores interned strings. When a string is created, the JVM checks the pool first to see if the string already exists. If it does, the reference to the existing string is returned; otherwise, a new string is added to the pool.

26. **What does the @Qualifier annotation mean?**
    - The `@Qualifier` annotation is used to resolve ambiguity in Spring's dependency injection when multiple beans of the same type are present. It specifies which bean should be injected.

27. **Give an example of @Qualifier in real-time.**
    ```java
    @Service
    public class NotificationService {
        private final MessageService messageService;

        @Autowired
        public NotificationService(@Qualifier("emailService") MessageService messageService) {
            this.messageService = messageService;
        }

        public void sendNotification(String message) {
            messageService.sendMessage(message);
        }
    }

    @Service("emailService")
    public class EmailService implements MessageService {
        @Override
        public void sendMessage(String message) {
            System.out.println("Sending email: " + message);
        }
    }

    @Service("smsService")
    public class SMSService implements MessageService {
        @Override
        public void sendMessage(String message) {
            System.out.println("Sending SMS: " + message);
        }
    }
    ```

28. **What is @Primary and give a real-time example.**
    - The `@Primary` annotation indicates which bean should be preferred when multiple candidates qualify for autowiring.

    ```java
    @Configuration
    public class AppConfig {

        @Bean
        @Primary
        public MessageService primaryMessageService() {
            return new EmailService();
        }

        @Bean
        public MessageService secondaryMessageService() {
            return new SMSService();
        }
    }
    ```

29. **What are collections in Java?**
    - Collections in Java are frameworks that provide an architecture to store and manipulate a group of objects. They include interfaces like List, Set, and Map, and classes like ArrayList, HashSet, and HashMap.

30. **Is Set an interface or a class?**
    - `Set` is an interface in Java.

31. **Is LinkedList an interface or a class?**
    - `LinkedList` is a class in Java.

## Spring Boot Questions

32. **What is the difference between Spring and Spring Boot?**
    - Spring is a comprehensive framework for enterprise Java development. Spring Boot simplifies the setup and development of new Spring applications with default configurations, embedded servers, and minimal configuration.

33. **Why use Spring Boot?**
    - Spring Boot is used for its ease of setup, embedded servers, reduced boilerplate code, auto-configuration, and rapid development capabilities.

34. **What is AOP in Spring Boot?**
    - AOP (Aspect-Oriented Programming) in Spring Boot is a programming paradigm that aims to increase modularity by allowing the separation of cross-cutting concerns, such as logging, transaction management, and security.

35. **Explain microservices architecture.**
    - Microservices architecture is a design approach where an application is composed of small, loosely coupled, and independently deployable services. Each service handles a specific business function and communicates with other services through APIs.

36. **What is @Autowired?**
    - `@Autowired` is a Spring annotation used for automatic dependency injection. It can be applied to constructors, fields, and setter methods to inject the required beans.

37. **What is the difference between @PathVariable and @RequestParam?**
    - `@PathVariable` is used to extract values from the URI path, while `@RequestParam` is used to extract query parameters from the request.

38. **What is the difference between POST and PUT?**
    - POST is used to create new resources, while PUT is used to update existing resources or create a resource if it does not exist.

39. **Which HTTP method do we use for creating resources?**
    - The POST method is used for creating resources.

40. **Can we use PUT for creating resources?**
    - Yes, PUT can be used to create resources if the resource does not already exist.

41. **What are HTTP status codes?**
    - HTTP status codes are standard response codes given by web servers on the internet. They indicate the result of the client's request, such as 200 (OK), 404 (Not Found), and 500 (Internal Server Error).

42. **What is fail-safe and fail-fast?**
    - Fail-safe iterators allow modifications to the collection while iterating without throwing an exception. Fail-fast iterators throw a `ConcurrentModificationException` if the collection is modified during iteration.

43. **Explain JWT token-based authentication.**
    - JWT (JSON Web Token) is a compact, URL-safe means of representing claims to be transferred between two parties. It is used for stateless authentication by encoding user information in a token, which is then used to verify the user's identity.

44. **What is the @Transactional annotation?**
    - `@Transactional` is used to manage transaction boundaries in Spring. It ensures that a method or a block of code is executed within a transaction, providing rollback and commit mechanisms.

## SQL Questions

45. **Write an SQL query to find the Nth maximum salary.**
    ```sql
    SELECT DISTINCT salary
    FROM employee
    ORDER BY salary DESC
    LIMIT 1 OFFSET N-1;
    ```

    For example, to find the 3rd maximum salary:
    ```sql
    SELECT DISTINCT salary
    FROM employee
    ORDER BY salary DESC
    LIMIT 1 OFFSET 2;
    ```
    
# L2 Interview Questions

1. **Self introduction based on project.**

   Answer: " about your project"

2. **Which Java version are you using?**

   Answer: "Before, I was using Java 8, which introduced several important features such as lambda expressions, the Stream API, the new Date-Time API, and the Optional class. These features significantly improved the way we write Java code. Currently, I am using Java 17. Java 17 includes several new features such as pattern matching for switch expressions, sealed classes, records, and the new Date-Time API enhancements. These features provide more concise and expressive syntax, better performance, and enhanced security."

3. **Where did you generate the JWT token?**

   Answer: "In my current project, we generate the JWT token during the user authentication process. The token is generated in the backend service using a secure secret key and is then sent to the client. The client includes this token in the Authorization header of subsequent requests to access protected resources."

4. **How do you provide JWT security in Spring Boot?**

   Answer: "In Spring Boot, we provide JWT security by using Spring Security along with a custom filter that validates the JWT token. The filter intercepts incoming requests, extracts the token from the Authorization header, and validates it. If the token is valid, the filter sets the authentication in the security context, allowing the request to proceed. Additionally, we configure the security settings to protect specific endpoints and ensure only authenticated users can access them."

# Given Code
```java
class Employee {
    private String name;
    private int id;
    private String department;
    private double salary;
 
    public Employee(String name, int id, String department, double salary) {
        this.name = name;
        this.id = id;
        this.department = department;
        this.salary = salary;
    }
 
    public String getName() {
        return name;
    }
 
    public int getId() {
        return id;
    }
 
    public String getDepartment() {
        return department;
    }
 
    public double getSalary() {
        return salary;
    }
 
    @Override
    public String toString() {
        return "Employee{name='" + name + "', id=" + id + ", department='" + department + "', salary=" + salary + "}";
    }
}

		ArrayList<Employee> employees = new ArrayList<>();         
		employees.add(new Employee("Alice", 101, "HR", 50000));     
		employees.add(new Employee("Bob", 102, "Engineering", 60000));        
		employees.add(new Employee("Charlie", 103, "Finance", 55000));        
		employees.add(new Employee("Diana", 104, "Engineering", 62000));
		
		

```
5. **How do you override the hashCode and equals methods in Java?**
```java
 @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        Employee employee = (Employee) obj;
        return id == employee.id &&
               Double.compare(employee.salary, salary) == 0 &&
               Objects.equals(name, employee.name) &&
               Objects.equals(department, employee.department);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, id, department, salary);
    }
```
6. **Find department-wise names using streams.**

   ```java
   Map<String, List<String>> departmentWiseNames = employees.stream()
       .collect(Collectors.groupingBy(
           Employee::getDepartment,
           Collectors.mapping(Employee::getName, Collectors.toList())
       ));

   departmentWiseNames.forEach((department, names) -> {
       System.out.println("Department: " + department);
       System.out.println("Names: " + names);
   });
   ```

7. **Find the second highest salary employee using streams.**

   ```java
   Employee secondHighestSalaryEmployee = employees.stream()
       .sorted(Comparator.comparingDouble(Employee::getSalary).reversed())
       .skip(1)
       .findFirst()
       .orElse(null);
   System.out.println("Second Highest Salary Employee: " + secondHighestSalaryEmployee);
   ```

## String Comparison
8. **What will be the output of the following code?**

   ```java
   public class Test {
       public static void main(String[] args) {
           String s1 = "hello";
           String s2 = "hello";
           String s3 = new String("hello");
   
           System.out.println(s1 == s2); 
           System.out.println(s1 == s3);
           System.out.println(s1.equals(s3)); 
       }
   }
   ```
   Answer:
   - `System.out.println(s1 == s2); ` - This is true because `s1` and `s2` refer to the same string literal in the string pool.
   - `System.out.println(s1 == s3); ` - This is false because `s3` is created using the `new` keyword, resulting in a different object in memory.
   - `System.out.println(s1.equals(s3));` - This is true because `equals` compares the content of the strings, which are the same.

9. **What will be the output of the following code?**

   ```java
   public class Test {
       public static void main(String[] args) {
           String s1 = "hello";
           String s2 = "hello";
           String s3 = new String("hello");
           String s4 = s3.intern();
   
           System.out.println(s1 == s2); 
           System.out.println(s1 == s3); 
           System.out.println(s1.equals(s3));
           System.out.println(s1 == s4); 
       }
   }
   ```

   Answer:
   - `System.out.println(s1 == s2); ` - This is true because `s1` and `s2` refer to the same string literal in the string pool.
   - `System.out.println(s1 == s3); ` - This is false because `s3` is created using the `new` keyword, resulting in a different object in memory.
   - `System.out.println(s1.equals(s3)); ` - This is true because `equals` compares the content of the strings, which are the same.
   - `System.out.println(s1 == s4); ` - This is true because `s4` is the interned version of `s3`, which points to the string literal in the string pool, the same as `s1`.
   - ` System.out.println(s3 == s4)` This is false because `s3` is a new String object created with `new String()`, while `s4` is a reference to the string literal in the pool. Therefore, they are different objects.


# Manager Round Interview Questions
1.**Can you briefly describe your current project and walk me through your daily responsibilities and tasks?**

2.**Question** Imagine you are tasked with enhancing a microservice for a library system that allows users to check out books. The new feature involves handling the scenario where multiple users attempt to check out the last copy of a particular book simultaneously.
 
You are provided with the following basic structure for the Checkout entity:
 
java
Copy code
public class Checkout {
   private Long id;
   private Long bookId;
   private String checkedOutBy; // This could be a user ID or username
   private LocalDateTime checkedOutOn;
   // getters and setters
}
Please address the following requirements in your solution:
Develop an API endpoint to facilitate book checkout.
Ensure that the checkout operation is atomic and thread-safe, preventing the last copy of a book from being checked out by multiple users at the same time.
If the checkout is successful, the response should include checkout details and an HTTP status code indicating success.
If all copies of the book are already checked out, the service should return an appropriate error message and HTTP status code.
Propose an approach for handling and logging exceptions that may occur during the checkout process, considering different types of failures that could happen (e.g., database errors, network issues).
Describe how you would structure the API responses to provide a consistent client experience, regardless of success or error conditions.

- **Answer**
```java
@RestController
@RequestMapping("/api/checkout")
public class CheckoutController {

    @Autowired
    private CheckoutService checkoutService;

    @PostMapping("/{bookId}")
    public ResponseEntity<?> checkoutBook(@PathVariable Long bookId, @RequestParam String userId) {
        try {
            Checkout checkout = checkoutService.checkoutBook(bookId, userId);
            return ResponseEntity.status(HttpStatus.OK).body(checkout);
        } catch (BookUnavailableException e) {
            return ResponseEntity.status(HttpStatus.CONFLICT).body(e.getMessage());
        } catch (Exception e) {
            return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR).body("An error occurred during checkout.");
        }
    }
}

@Service
public class CheckoutService {

    @Autowired
    private CheckoutRepository checkoutRepository;

    @Autowired
    private BookRepository bookRepository;

    @Transactional
    public Checkout checkoutBook(Long bookId, String userId) throws BookUnavailableException {
        synchronized (bookId) {
            int availableCopies = bookRepository.getAvailableCopies(bookId);
            if (availableCopies <= 0) {
                throw new BookUnavailableException("No copies of the book are currently available.");
            }

            // Reduce the available copies by 1
            bookRepository.decrementAvailableCopies(bookId);

            // Create and save the checkout record
            Checkout checkout = new Checkout();
            checkout.setBookId(bookId);
            checkout.setCheckedOutBy(userId);
            checkout.setCheckedOutOn(LocalDateTime.now());
            return checkoutRepository.save(checkout);
        }
    }
}

@Repository
public interface CheckoutRepository extends JpaRepository<Checkout, Long> {
}

@Repository
public interface BookRepository {

    @Query("SELECT b.availableCopies FROM Book b WHERE b.id = :bookId")
    int getAvailableCopies(@Param("bookId") Long bookId);

    @Modifying
    @Query("UPDATE Book b SET b.availableCopies = b.availableCopies - 1 WHERE b.id = :bookId AND b.availableCopies > 0")
    int decrementAvailableCopies(@Param("bookId") Long bookId);
}

@ResponseStatus(HttpStatus.CONFLICT)
public class BookUnavailableException extends RuntimeException {
    public BookUnavailableException(String message) {
        super(message);
    }
}
```
# HR
