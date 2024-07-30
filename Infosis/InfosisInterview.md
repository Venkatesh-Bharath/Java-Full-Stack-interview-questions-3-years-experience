#Technical Round
## Self-Introduction and Project Explanation

1. **Self-introduction with a brief explanation about your project.**
   - *"Hello, I’m [Your Name]. I have been working in software development for [X] years, specializing in Java and React. Currently, I am involved in a project that focuses on developing a [brief description of the project]."*

2. **Have you developed any project for your referencing purpose?**
   - *"Yes, I have worked on several projects for reference, including [briefly mention training projects or key projects you’ve worked on]. These projects helped me enhance my skills in [mention technologies or areas]."*

3. **Explain about your developed project. (Follow-up questions based on the project)**
   - *"My recent project involved [describe the scope of your project]. It was designed to [mention key objectives or features]. We utilized technologies such as [mention technologies] to achieve [mention goals or results]."*

4. **How do you monitor your project?**
   - *"I use various tools like New Relic and Grafana for monitoring application performance and logs. Additionally, I rely on automated tests and CI/CD pipelines to ensure the project’s stability."*

5. **Which database did you use?**
   - *"I used SQL for managing relational data due to its robust features and performance advantages."*

## Java
1. **What is a class loader?**
   - *A class loader is a part of the Java Runtime Environment (JRE) that loads Java classes into memory. It dynamically loads, links, and initializes classes as needed.*

2. **What is the Object class?**
   - *The Object class is the root class of the Java class hierarchy. Every class in Java inherits from Object, and it provides basic methods like `toString()`, `equals()`, and `hashCode()`.*

3. **What are the equals and hashCode methods in the Object class?**
   - *`equals()` is used to compare two objects for equality, while `hashCode()` returns a unique integer for each object. These methods are used in collections like HashMap.*

4. **Explain encapsulation.**
   - *Encapsulation is the concept of wrapping data (variables) and methods (functions) into a single unit or class. It restricts direct access to some of the object's components, which can help prevent accidental interference and misuse.*

5. **Give a real-time example of encapsulation.**
   - *A real-time example is a bank account class. The account details (balance, account number) are private, and access is provided through public methods (deposit, withdraw) to ensure controlled and secure manipulation of the data.*

6. **Compare static block vs static method.**
   - *A static block is used for initializing static variables or performing some initialization when the class is first loaded. A static method, on the other hand, can be called without creating an instance of the class and can only access static members.*

7. **Does a static block execute first or does a constructor execute first?**
   - *A static block executes before a constructor. It runs when the class is first loaded, whereas the constructor is executed when an instance of the class is created.*

8. **If I remove static from the main method, will it work?**
   - *No, the `main` method must be static because it is the entry point for the JVM to start the application. Without `static`, the JVM cannot call the method.*

9. **Write a code to move array elements with 0s to the last and explain. arr={1,0,1,1,0,0,1} output={1,1,1,1,0,0,0}**
```java
   public class MoveZeros {
       public static void moveZeros(int[] arr) {
           int count = 0; // Count of non-zero elements
           for (int i = 0; i < arr.length; i++) {
               if (arr[i] != 0) {
                   arr[count++] = arr[i]; // Move non-zero elements to the front
               }
           }
           while (count < arr.length) {
               arr[count++] = 0; // Fill remaining positions with zeros
           }
       }
   }
 ```
   - *This code iterates through the array, moving all non-zero elements to the front. After that, it fills the remaining positions with zeros.*

10. **Class Inheritance Issue:**
   ```java
   class A {
       public void sum() {}
   }
   class B extends A {
       public void sum() {}
   }
   // class C extends A, B {} // Compilation error
   ```
   - *Java does not support multiple inheritance directly. You need to refactor the code, perhaps using interfaces or abstract classes.*

11. **Interface Implementation Issue:**
   ```java
   interface A {
       void sum();
   }
   interface B{
    void sum();
   }
   class C implements A, B {
      // which sum method i want to implemet
   }
   ```
- *In Java, when a class implements multiple interfaces that declare methods with the same name and signature, you only need to provide one implementation for that method in the class. This single implementation will be used for both interfaces.*
```java
class C implements A, B {
    @Override
    public void sum() {
        // Single implementation of the sum method
        System.out.println("Sum method implemented in class C");
    }
}
```
12. **What is a functional interface?**
   - *A functional interface is an interface with a single abstract method. They are used as the target type for lambda expressions and method references. Examples include `Runnable` and `Callable`.*

13. **Write code to find the second largest number in the array `[1, 2, 3, 4, 5, 2, 4]` using Java 8.**
```java
 import java.util.Arrays;
import java.util.Comparator;

public class SecondLargestNumber {
    public static void main(String[] args) {
        int[] a = {3, 6, 32, 1, 8, 5, 31, 22};

        int secondLargest = Arrays.stream(a)
                                  .boxed()
                                  .sorted(Comparator.reverseOrder())
                                  .distinct()
                                  .skip(1)
                                  .findFirst()
                                  .orElseThrow(() -> new IllegalArgumentException("Array must contain at least two distinct elements"));

        System.out.println("Second Largest Number: " + secondLargest);
    }
}

```
   - *This code first removes duplicates, sorts the array, and then retrieves the second last element.*

14. **What is a HashMap?**
   - *HashMap is a collection that stores key-value pairs. It allows for efficient retrieval of values based on their keys.*

15. **Can a HashMap key be null?**
   - *Yes, HashMap allows one null key and multiple null values.*

16. **Explain the internal working process of a HashMap.**
   - *HashMap uses an array of buckets to store key-value pairs. The hash code of the key determines the bucket in which the entry is stored. Collisions are handled by linking entries in the same bucket.*

17. **What is the new change in Java 8 hashCode?**
   - *Java 8 introduced improvements to the `hashCode` method, particularly in hash-based collections. For example, `HashMap` uses a balanced tree structure for high collision scenarios.*

18. **What is the default size of a HashMap?**
   - *The default initial capacity of a HashMap is 16 buckets.*

19. **Explain fail-safe and fail-fast iterators.**
   - *Fail-fast iterators immediately throw `ConcurrentModificationException` if the collection is modified during iteration. Fail-safe iterators, like those in `CopyOnWriteArrayList`, work on a copy of the collection and do not throw exceptions if the collection is modified.*

-*[Reference code]*
*Code Example for Fail-Fast Iterators:*
```java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class FailFastExample {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        list.add("A");
        list.add("B");
        list.add("C");

        Iterator<String> iterator = list.iterator();
        
        // Modify the collection while iterating
        while (iterator.hasNext()) {
            String item = iterator.next();
            System.out.println(item);
            list.add("D"); // This will cause ConcurrentModificationException
        }
    }
}
```
*Code Example for Fail-Safe Iterators:*

```java
import java.util.List;
import java.util.concurrent.CopyOnWriteArrayList;

public class FailSafeExample {
    public static void main(String[] args) {
        List<String> list = new CopyOnWriteArrayList<>();
        list.add("A");
        list.add("B");
        list.add("C");

        for (String item : list) {
            System.out.println(item);
            list.add("D"); // This will not cause ConcurrentModificationException
        }

        // Print the list after modification
        System.out.println("List after modification: " + list);
    }
}
```

### Hibernate
1. **What is Hibernate?**
   - *Hibernate is an ORM (Object-Relational Mapping) framework that simplifies database interactions by mapping Java objects to database tables.*

2. **Does JPA implement Hibernate? (True or False and why)**
   - *False. JPA (Java Persistence API) is a specification for ORM in Java. Hibernate is an implementation of JPA.*

3. **If JDBC is there, why do we need Hibernate?**
   - *Hibernate provides a higher level of abstraction compared to JDBC. It handles complex database operations, caching, and object mapping more efficiently than raw JDBC.*

4. **Do you know SQL and NoSQL databases?**
   - *Yes, I am familiar with both SQL databases (e.g., PostgreSQL, MySQL) and NoSQL databases (e.g., MongoDB, Cassandra).*

### SQL
1. **What is the difference between HAVING and WHERE clause?**
   - *`WHERE` is used to filter rows before aggregation, while `HAVING` is used to filter groups after aggregation.*

2. **Can I use WHERE to filter a group of records?**
   - *No, `WHERE` filters rows, not groups. Use `HAVING` to filter groups.*

3. **What is an index in SQL?**
   - *An index is a database object that improves the speed of data retrieval operations on a table. It creates a separate data structure that allows for faster searches.*

### Spring Boot
1. **What is the difference between PUT and PATCH?**
   - *`PUT` is used to update an entire resource, while `PATCH` is used to update partial data of a resource.*

2. **Can we use PUT in place of POST? Will it work or not?**
   - *Yes, `PUT` can be used in place of `POST`, but they have different semantics. `PUT` is idempotent, meaning multiple identical requests have the same effect as a single request, while `POST` may result in different outcomes.*

3. **What is the difference between @RestController and @Controller?**
   - *`@RestController` is a specialized version of `@Controller` that combines `@Controller` and `@ResponseBody`, meaning it returns JSON/XML responses directly. `@Controller` is used for rendering views (like JSPs).*

4. **Why is REST API stateless?**
   - *REST APIs are stateless to ensure scalability and reliability. Each request from the client to the server must contain all the information needed to understand and process the request.*

### Additional Questions

1. **How do you know .NET?**
   - *[_____]*

2. **Can you give an example of where you have used all your technical skills?**
   - *[_____]*


# Manager Round

1. **Can you provide a brief explanation of your project?**
   - *[your self].*

2. **What specific work did you do with ReactJS in your project?**
   - *I worked on creating reusable components, implementing form validation with Formik, and managing state using React’s Context API. I also optimized the application's performance by using React hooks like `useMemo` and `useCallback`, and implemented lazy loading for certain components to enhance loading times.*

3. **On a scale of 1 to 10, how would you rate yourself in Java, Spring Boot, and microservices?**
   - *I would rate myself as follows: Java - 8, Spring Boot - 8, Microservices - 7.5. I have extensive experience in Java and Spring Boot, and I am comfortable developing and managing microservices architectures, though I continue to seek opportunities to deepen my expertise in microservices.*

4. **How did you learn .NET?**
   - *I learned .NET Core by working on a personal project and by following tutorials and courses available online. I also created content about .NET on my YouTube channel, which helped reinforce my learning by teaching the concepts to others. This approach allowed me to deepen my understanding and gain practical experience.*

5. **Which databases have you used in your projects?**
   - *I have used MySQL and H2 databases in my projects. MySQL was utilized for managing relational data due to its robustness and scalability, while H2 was used for in-memory data storage and testing purposes, which helped in speeding up the development and testing processes*

6. **What issues did you face in your first and second projects, and how did you overcome them?**
   - *In my first project, a bank application, I faced issues with data integrity, security, and performance. I resolved these by implementing strong transaction management, using Spring Security for authentication, and optimizing database queries. In my second project, I did not encounter significant issues.*

7. **How have you improved the performance of your code?**
   - *I have improved code performance by profiling and identifying bottlenecks, optimizing algorithms and data structures, and implementing caching strategies. Additionally, I have refactored code for better readability and maintainability, which also contributes to improved performance and reduced complexity.*
