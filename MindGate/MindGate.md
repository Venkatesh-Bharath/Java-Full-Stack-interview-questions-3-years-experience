# MindGate 
## L1 Interview
1. **Self-introduction based on your project.**
   - "I am ______ with 3 years of experience in Java and ReactJS. In my current project, I developed a customer registration service using ReactJS and Spring Boot, integrating with multiple microservices to ensure secure and efficient data handling."

2. **Explain microservices architecture.**
   - "Microservices architecture divides an application into small, independent services, each responsible for a specific business functionality. These services communicate over a network, allowing for decentralized development, scaling, and deployment."

3. **How do microservices communicate internally?**
   - "Microservices communicate internally using protocols like HTTP/REST, gRPC, or messaging systems like Kafka. Service discovery tools and load balancers help manage requests and ensure service availability."

4. **How does a JWT token work internally?**
   - "A JWT token encodes user information and is signed with a secret key. The token is sent to the client and included in subsequent requests. The server verifies the token's signature to authenticate the user."

5. **Explain the Collection hierarchy in Java.**
   - "The Collection hierarchy starts with `Iterable`, followed by `Collection`, branching into `List`, `Set`, and `Queue`. `Map` is a separate interface for key-value pairs, not extending `Collection`."

6. **If a `List` is declared as `final`, can we modify it?**
   - "Yes, a `final` `List` can have its contents modified, but its reference cannot be reassigned to another `List` object."

7. **Why does a `Set` not allow duplicates?**
   - "A `Set` does not allow duplicates because it uses the `equals()` and `hashCode()` methods to ensure all elements are unique."

8. **What is the difference between fail-safe and fail-fast iterators?**
   - "Fail-fast iterators throw a `ConcurrentModificationException` if the collection is modified during iteration. Fail-safe iterators work on a copy of the collection, allowing safe iteration."

9. **Explain `ConcurrentHashMap`.**
   - "`ConcurrentHashMap` is a thread-safe implementation of `Map` that allows concurrent read and write operations by dividing the map into segments, reducing contention."

10. **What happens when you use `HashMap` in a multithreaded environment?**
   - "Using `HashMap` in a multithreaded environment can lead to data corruption and unpredictable results due to concurrent modifications. `ConcurrentHashMap` should be used instead."

11. **Describe the Java thread lifecycle.**
   - "The Java thread lifecycle includes New, Runnable, Blocked, Waiting, Timed Waiting, and Terminated states. A thread transitions through these states based on its execution and synchronization."

12. **Write a custom `ArrayList` that does not allow duplicates.**
   ```java
   import java.util.ArrayList;

   public class UniqueArrayList<E> extends ArrayList<E> {
       @Override
       public boolean add(E e) {
           if (!contains(e)) {
               return super.add(e);
           }
           return false;
       }
   }
   ```

13. **How do you find the occurrences of words using `HashMap` in Java?**
   ```java
   import java.util.HashMap;
   import java.util.Map;

   public class WordCount {
       public static void main(String[] args) {
           String text = "apple apple banana apple orange banana";
           Map<String, Integer> wordCount = new HashMap<>();
           for (String word : text.split(" ")) {
               wordCount.put(word, wordCount.getOrDefault(word, 0) + 1);
           }
           for (Map.Entry<String, Integer> entry : wordCount.entrySet()) {
               System.out.println(entry.getKey() + ": " + entry.getValue());
           }
       }
   }
   ```

14. **Write an SQL query to print account names based on the currency name.**
   ```sql
   SELECT A.ACCNAME
   FROM ACCOUNT A
   JOIN COUNTRY C ON A.COUNTRYID = C.COUNTRYID
   JOIN CURRENCY CUR ON C.CURRID = CUR.CURRID
   WHERE CUR.CURRNAME = 'currency_name';
   ```

