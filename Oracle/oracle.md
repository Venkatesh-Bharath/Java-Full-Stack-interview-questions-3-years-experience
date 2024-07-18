### Oracle Interview Questions

## First Round
1. **Self-introduction**
2. **Coding Questions** -HackerRank coding
   - Code 1-Find higest and lowest Rank of Students
   - Code 2- Vending machine Problem
3. **SQL Queries**
   - Query 1- joins Based Query
   - Query 2- Pivot Based Query

## Second Round


### 1. Self-introduction based on project
   - **Answer**: Provide a concise overview of your current project, highlighting key technologies used, your role, and major achievements.
   - 
### 2. Write a Spring Boot project for login and register using JWT token through an online Java compiler
   - **Answer**:
     ```java
     @SpringBootApplication
     public class JwtDemoApplication {
         public static void main(String[] args) {
             SpringApplication.run(JwtDemoApplication.class, args);
         }
     }

     @RestController
     @RequestMapping("/auth")
     public class AuthController {

         @PostMapping("/register")
         public ResponseEntity<?> register(@RequestBody User user) {
             // Code to save user
             return ResponseEntity.ok("User registered successfully");
         }

         @PostMapping("/login")
         public ResponseEntity<?> login(@RequestBody AuthRequest authRequest) {
             // Code to authenticate user and generate JWT
             return ResponseEntity.ok(new AuthResponse(jwtToken));
         }
     }

     @Service
     public class JwtService {
         public String generateToken(UserDetails userDetails) {
             // Code to generate JWT
         }
     }
     ```

### 3. How to handle when microservices fail
   - **Answer**: Use fallback mechanisms, retry policies, and circuit breakers to handle microservice failures. Implementing a circuit breaker pattern using libraries like Resilience4j helps isolate failing services and prevent cascading failures.

### 4. How to implement circuit breakers in microservices
   - **Answer**: Use Resilience4j to implement circuit breakers:
     ```java
     @Service
     public class MyService {

         @CircuitBreaker(name = "myService", fallbackMethod = "fallbackMethod")
         public String performOperation() {
             // Code that may fail
         }

         public String fallbackMethod(Throwable t) {
             return "Fallback response";
         }
     }
     ```

### 5. Write a program to sort a string array without using any sort method or inbuilt functions
   - **Answer**:
     ```java
     public class StringArraySort {
         public static void main(String[] args) {
             String[] arr = {"banana", "apple", "cherry"};
             for (int i = 0; i < arr.length - 1; i++) {
                 for (int j = i + 1; j < arr.length; j++) {
                     if (compareStrings(arr[i], arr[j]) > 0) {
                         String temp = arr[i];
                         arr[i] = arr[j];
                         arr[j] = temp;
                     }
                 }
             }
             for (String str : arr) {
                 System.out.println(str);
             }
         }

         public static int compareStrings(String s1, String s2) {
             int len = Math.min(s1.length(), s2.length());
             for (int i = 0; i < len; i++) {
                 if (s1.charAt(i) != s2.charAt(i)) {
                     return s1.charAt(i) - s2.charAt(i);
                 }
             }
             return s1.length() - s2.length();
         }
     }
     ```

### 6. Internal working process of HashMap
   - **Answer**: HashMap works on the principle of hashing. It uses an array of buckets to store key-value pairs. The `hashCode()` method determines the bucket index. When collisions occur (i.e., multiple keys hash to the same index), they are stored in a linked list or tree structure within the bucket. When retrieving, the key's hash code and `equals()` method are used to find the correct value.

### 7. Scenario where overriding `hashCode` and `equals` is necessary in Java
   - **Answer**: When creating a custom object to be used as a key in a HashMap or other hash-based collections, you must override `hashCode` and `equals` to ensure correct behavior. For example:
     ```java
     public class Employee {
         private int id;
         private String name;

         @Override
         public boolean equals(Object o) {
             if (this == o) return true;
             if (o == null || getClass() != o.getClass()) return false;
             Employee employee = (Employee) o;
             return id == employee.id && Objects.equals(name, employee.name);
         }

         @Override
         public int hashCode() {
             return Objects.hash(id, name);
         }
     }
     ```

### 8. Difference between HashMap and Hashtable
   - **Answer**:
     - **HashMap**: Non-synchronized, allows one null key and multiple null values, generally faster.
     - **Hashtable**: Synchronized, does not allow null keys or values, generally slower due to synchronization overhead.

### 9. Difference between synchronized and non-synchronized with real-time examples
   - **Answer**:
     - **Synchronized**: Thread-safe, ensures only one thread can access a resource at a time. Example: `Hashtable` is synchronized.
     - **Non-synchronized**: Not thread-safe, multiple threads can access resources simultaneously. Example: `HashMap` is non-synchronized.

### 10. Write a program to make a HashMap synchronized
   **Answer**:
   
   ```java
      import java.util.Collections;
      import java.util.HashMap;
      import java.util.Map;
      public class SyncHashMapExample {
          public static void main(String[] args) {
              Map<String, String> map = new HashMap<>();
              map.put("1", "One");
              map.put("2", "Two"); 
              Map<String, String> syncMap = Collections.synchronizedMap(map);
              
              synchronized (syncMap) {
                  for (Map.Entry<String, String> entry : syncMap.entrySet()) {
                      System.out.println(entry.getKey() + ": " + entry.getValue());
                  }
              }
          }
      }
  ```

## Final Round
1. **Self-introduction**
2. **About qualification**
3. **About project**
4. **How you learned coding and family details**
5. **Which technology you know**
6. **If we offer you new technology, which technology would you choose?**
7. **In your developing project, which is your most struggling phase?**
8. **How did you overcome that?**
... **Etc...**
