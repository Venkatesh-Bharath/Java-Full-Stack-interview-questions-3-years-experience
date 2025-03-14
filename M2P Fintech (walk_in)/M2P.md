## **First Round (Virtual - Technical Assessment)**
---
1. **What are the key differences between @Component, @Repository, and @Service annotations in Spring Boot?**
   - `@Component`: Generic stereotype annotation for any Spring-managed component.
   - `@Repository`: Specialization of `@Component` used for DAO layer and exception translation.
   - `@Service`: Specialization of `@Component` used for service layer logic.

2. **Explain the concept of dependency injection in Spring Boot.**
   - Dependency Injection (DI) is a design pattern where Spring manages object dependencies.
   - It allows loose coupling by injecting dependencies at runtime.

3. **How does Spring Boot handle exception handling? Explain with an example.**
   - Spring Boot provides `@ControllerAdvice` and `@ExceptionHandler` to handle exceptions globally.
   - Example:
     ```java
     @ControllerAdvice
     public class GlobalExceptionHandler {
         @ExceptionHandler(ResourceNotFoundException.class)
         public ResponseEntity<String> handleNotFound(ResourceNotFoundException ex) {
             return new ResponseEntity<>(ex.getMessage(), HttpStatus.NOT_FOUND);
         }
     }
     ```

4. **What is the difference between @RestController and @Controller in Spring Boot?**
   - `@Controller`: Used for MVC applications; returns views.
   - `@RestController`: Combination of `@Controller` and `@ResponseBody`, used for REST APIs.

5. **How do you configure and use Spring Boot caching with Redis?**
   - Add Redis dependency in `pom.xml`.
   - Use `@EnableCaching` in the main class.
   - Configure Redis in `application.properties`.
   - Use `@Cacheable`, `@CachePut`, and `@CacheEvict` annotations.

6. **Explain the internal working of Spring Boot’s @Transactional annotation.**
   - Manages transactions declaratively.
   - Uses AOP proxies to begin, commit, or rollback transactions.
   - Works with Hibernate/JPA for database operations.

7. **What is the role of Spring Boot Actuator? Name some of its important endpoints.**
   - Provides production-ready features like health checks and metrics.
   - Important endpoints: `/actuator/health`, `/actuator/info`, `/actuator/metrics`

8. **What is Spring Boot Starter? How does it help in application development?**
   - Pre-configured dependency modules that simplify development.
   - Example: `spring-boot-starter-web`, `spring-boot-starter-data-jpa`.

9. **How can you secure a Spring Boot REST API using JWT authentication?**
   - Implement JWT filter.
   - Use `OncePerRequestFilter` to validate tokens.
   - Secure endpoints using `@PreAuthorize`.

10. **Explain how Circuit Breaker works in Spring Boot.**
    - Prevents system failures by breaking the connection if failures exceed a threshold.
    - Uses libraries like Resilience4j.

11. **Write a Java program to check if a given string is a valid IPv4 address without using any inbuilt methods.**
    ```java
    public class IPv4Validator {
        public static boolean isValidIPv4(String ip) {
            String[] parts = ip.split("\\.");
            if (parts.length != 4) return false;
            for (String part : parts) {
                try {
                    int num = Integer.parseInt(part);
                    if (num < 0 || num > 255) return false;
                } catch (NumberFormatException e) {
                    return false;
                }
            }
            return true;
        }
        public static void main(String[] args) {
            System.out.println(isValidIPv4("192.168.1.1"));
        }
    }
    ```

12. **Given an array of integers, return the indices of two numbers that add up to a specific target.**
    ```java
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[]{map.get(complement), i};
            }
            map.put(nums[i], i);
        }
        return new int[]{};
    }
    ```

13. **Write a program to reverse the words in a sentence while maintaining their order.**
    ```java
    public String reverseWords(String s) {
        String[] words = s.split(" ");
        StringBuilder result = new StringBuilder();
        for (String word : words) {
            result.append(new StringBuilder(word).reverse()).append(" ");
        }
        return result.toString().trim();
    }
    ```

14. **Implement a function to check if a string is a palindrome using recursion.**
    ```java
    public boolean isPalindrome(String s) {
        return isPalindromeHelper(s, 0, s.length() - 1);
    }
    private boolean isPalindromeHelper(String s, int left, int right) {
        if (left >= right) return true;
        return (s.charAt(left) == s.charAt(right)) && isPalindromeHelper(s, left + 1, right - 1);
    }
    ```

15. **Implement a custom functional interface and demonstrate its use with a lambda expression.**
    ```java
    @FunctionalInterface
    interface MathOperation {
        int operate(int a, int b);
    }
    public class LambdaExample {
        public static void main(String[] args) {
            MathOperation sum = (a, b) -> a + b;
            System.out.println(sum.operate(5, 3));
        }
    }
    ```

16. **Find the first non-repeated character in a given string using Java Streams.**
    ```java
    public Character firstNonRepeated(String s) {
        Map<Character, Long> charCount = s.chars().mapToObj(c -> (char) c)
                .collect(Collectors.groupingBy(Function.identity(), LinkedHashMap::new, Collectors.counting()));
        return charCount.entrySet().stream()
                .filter(entry -> entry.getValue() == 1)
                .map(Map.Entry::getKey)
                .findFirst()
                .orElse(null);
    }
    ```

17. **Implement a Least Recently Used (LRU) Cache in Java using LinkedHashMap.**
    ```java
    class LRUCache<K, V> extends LinkedHashMap<K, V> {
        private final int capacity;
        LRUCache(int capacity) {
            super(capacity, 0.75f, true);
            this.capacity = capacity;
        }
        @Override
        protected boolean removeEldestEntry(Map.Entry<K, V> eldest) {
            return size() > capacity;
        }
    }
    ```

18. **Given an array of numbers, find all unique triplets whose sum equals zero.**
    ```java
    // Code for 3Sum problem
    ```

19. **Implement a thread-safe Singleton class in Java.**
    ```java
    public class Singleton {
        private static volatile Singleton instance;
        private Singleton() {}
        public static Singleton getInstance() {
            if (instance == null) {
                synchronized (Singleton.class) {
                    if (instance == null) {
                        instance = new Singleton();
                    }
                }
            }
            return instance;
        }
    }
    ```
---

## **Second Round (Walk-In - L1 Technical Interview)**  

#### **1. Count of three-character palindromes in a string.**  
**Answer:**  
```java
import java.util.HashSet;
import java.util.Set;

public class UniqueThreeCharPalindromes {
    public static int countPalindromicSubsequences(String s) {
        Set<String> uniquePalindromes = new HashSet<>();

        for (char c = 'a'; c <= 'z'; c++) {
            int first = s.indexOf(c);
            int last = s.lastIndexOf(c);

            if (first != -1 && last != -1 && last - first > 1) {
                for (int i = first + 1; i < last; i++) {
                    uniquePalindromes.add("" + s.charAt(first) + s.charAt(i) + s.charAt(last));
                }
            }
        }
        return uniquePalindromes.size();
    }

    public static void main(String[] args) {
        System.out.println(countPalindromicSubsequences("aabca")); // Output: 3
        System.out.println(countPalindromicSubsequences("adc"));   // Output: 0
        System.out.println(countPalindromicSubsequences("bbcbaba")); // Output: 4
    }
}
```
---
#### **2. What is a circuit breaker in microservices?**  
**Answer:** A circuit breaker in microservices is a design pattern used to prevent a system from making repeated requests to a failing service. It detects failures and stops sending requests to prevent cascading failures. Once the service recovers, it resumes operations.  

---
#### **3. How does Netflix Hystrix work in Spring Boot?**  
**Answer:** Netflix Hystrix provides a circuit breaker mechanism to handle failures in microservices. It isolates failing components and provides fallbacks to prevent system-wide failures. In Spring Boot, it is implemented using `@HystrixCommand` to wrap service calls with circuit breaker functionality.  

---
#### **4. What are the different states of a circuit breaker?**  
**Answer:**  
1. **Closed** - Requests flow normally. If failures increase beyond a threshold, it transitions to Open.  
2. **Open** - Requests are blocked, and fallback mechanisms take over.  
3. **Half-Open** - A few requests are allowed to test if the service has recovered. If successful, it moves back to Closed; otherwise, it stays Open.  

---
#### **5. Explain API Gateway and its role in microservices.**  
**Answer:** An API Gateway acts as an entry point for microservices, handling authentication, request routing, rate limiting, and load balancing. It simplifies communication between clients and backend services by consolidating multiple APIs into a single endpoint.  

---
#### **6. What is service registry and discovery in microservices?**  
**Answer:** Service registry and discovery help microservices locate and communicate with each other dynamically. A service registry (e.g., Eureka) maintains a list of available services, and discovery mechanisms allow services to register and find each other without hardcoding URLs.  

---
#### **7. How does load balancing work in microservices?**  
**Answer:** Load balancing distributes incoming requests across multiple instances of a service to ensure high availability and scalability. It can be:  
1. **Client-Side Load Balancing** (e.g., Ribbon) - Clients choose a service instance from a list.  
2. **Server-Side Load Balancing** (e.g., Nginx, HAProxy) - A central load balancer directs traffic.  
3. **Service Mesh Load Balancing** (e.g., Istio) - Traffic is managed at the service level.  

---

## **Third Round (Walk-In - L2 Technical Interview)**  

#### **1. What is the difference between ArrayList and LinkedList?**  
| Feature       | ArrayList | LinkedList |
|--------------|-----------|------------|
| **Implementation** | Uses a dynamic array | Uses a doubly linked list |
| **Insertion/Deletion** | Slow (O(n) in worst case) due to shifting elements | Fast (O(1) at head/tail, O(n) at middle) |
| **Access Time** | Fast (O(1) for get) | Slow (O(n) for get) |
| **Memory Usage** | Less overhead, stores only data | More overhead, stores data and pointers |

---
#### **2. How does HashMap handle collisions internally?**  
**Answer:** HashMap in Java handles collisions using **chaining (linked list or tree nodes)**.  
- Each bucket in HashMap is a linked list (before Java 8) or a balanced tree (after Java 8, when size > 8).  
- If two keys produce the same hash, they are stored in the same bucket.  
- When a bucket’s size exceeds a threshold, Java 8 converts it into a Red-Black Tree for faster lookups.  

---
#### **3. How do you make a collection thread-safe in Java?**  
**Answer:** Collections can be made thread-safe using:  
1. **Synchronized Collections** - `Collections.synchronizedList(new ArrayList<>())`  
2. **Concurrent Collections** - `CopyOnWriteArrayList`, `ConcurrentHashMap`  
3. **Explicit Synchronization** - Using `synchronized` blocks  

---
#### **4. Implement ArrayList using an array with add and remove methods that automatically resize when needed.**  
```java
import java.util.Arrays;

class GenericArrayList<T> {
    private Object[] arr;
    private int size;
    private int capacity;

    public GenericArrayList() {
        capacity = 10;
        arr = new Object[capacity];
        size = 0;
    }

    public void add(T value) {
        if (size == capacity) {
            resize();
        }
        arr[size++] = value;
    }

    private void resize() {
        capacity *= 2;
        arr = Arrays.copyOf(arr, capacity);
    }

    @SuppressWarnings("unchecked")
    public T get(int index) {
        if (index < 0 || index >= size) {
            throw new IndexOutOfBoundsException("Invalid index");
        }
        return (T) arr[index];
    }

    public void remove(int index) {
        if (index < 0 || index >= size) {
            throw new IndexOutOfBoundsException("Invalid index");
        }
        for (int i = index; i < size - 1; i++) {
            arr[i] = arr[i + 1];
        }
        size--;
    }

    public int size() {
        return size;
    }

    public boolean isEmpty() {
        return size == 0;
    }

    public static void main(String[] args) {
        GenericArrayList<String> list = new GenericArrayList<>();
        list.add("Apple");
        list.add("Banana");
        list.add("Cherry");

        System.out.println(list.get(1)); // Output: Banana

        list.remove(1);
        System.out.println(list.get(1)); // Output: Cherry
    }
}

```

---
#### **5. Write an SQL query to find the 3rd highest salary from an Employee table.**  
```sql
SELECT DISTINCT salary 
FROM Employee 
ORDER BY salary DESC 
LIMIT 1 OFFSET 2;
```
OR  
```sql
SELECT salary 
FROM (SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk 
      FROM Employee) temp 
WHERE rnk = 3;
```

---
#### **6. How do you handle distributed transactions in microservices?**  
**Answer:** Distributed transactions can be handled using:  
1. **Two-Phase Commit (2PC):** Coordinating a commit across multiple services.  
2. **Saga Pattern:**  
   - **Choreography:** Each service triggers the next service in the transaction.  
   - **Orchestration:** A central orchestrator handles the transaction flow.  
3. **Event-Driven Approach:** Using Kafka or RabbitMQ for event-based transactions.  
4. **Compensating Transactions:** Implementing rollback logic when failure occurs.  

---

## **Fourth Round (Walk-In - L3 System Design Interview)**  

---

### **1. How would you design a scalable hotel search engine?**  
- **Architecture:** Use **microservices** with **event-driven architecture**.  
- **Database:** Use **NoSQL (MongoDB, Elasticsearch)** for fast queries, **SQL (PostgreSQL, MySQL)** for structured data.  
- **Search Optimization:** Use **Elasticsearch** for indexing.  
- **Load Balancing:** Deploy across multiple **regions** with **CDN caching**.  
- **API Gateway:** Use **GraphQL or REST APIs** with **rate-limiting**.  
- **Caching:** Implement **Redis** or **Memcached** for fast query results.  
- **Data Storage:** Store metadata in **S3** or **GCS**.  
- **Message Queue:** Use **Kafka** or **RabbitMQ** for async tasks like notifications.  
- **Scalability:** Use **Kubernetes** or **Docker** for containerization and auto-scaling.  

---

### **2. What are the key components needed to optimize search results in a hotel search system?**  
- **Indexing:** Store structured hotel data in **Elasticsearch**.  
- **Ranking Algorithm:** Use **Relevance Score (TF-IDF)** or **Machine Learning (ML)** models.  
- **Filters & Sorting:** Provide sorting by **price, rating, distance**.  
- **Geo-Spatial Search:** Optimize queries using **Geo-indexing**.  
- **Personalization:** Recommend hotels based on **user history** and **preferences**.  
- **Auto-Suggestions:** Use **n-grams or trie-based** search suggestions.  

---

### **3. How does indexing help in improving search performance?**  
- **Faster Lookups:** Indexing **reduces lookup time** from **O(n) → O(log n) or O(1)** (hash indexing).  
- **Better Query Execution:** Uses **B-Trees, Hash Indexing, Full-Text Search**.  
- **Optimized Sorting & Filtering:** Queries run on **precomputed indexes** instead of raw data scans.  
- **Efficient Range Queries:** Useful for **date range searches** (e.g., hotel availability).  
- **Inverted Index:** Used in **Elasticsearch** for **fast text-based queries**.  

---

### **4. What techniques would you use to handle high traffic in a hotel search engine?**  
- **Load Balancing:** Use **Nginx, HAProxy, or AWS ALB**.  
- **Database Optimization:** Use **read replicas**, **sharding**, and **caching**.  
- **CDN:** Serve static content via **Cloudflare, AWS CloudFront**.  
- **Asynchronous Processing:** Use **Kafka, RabbitMQ** for background tasks.  
- **Horizontal Scaling:** Scale by adding **more servers (Kubernetes, Auto Scaling Groups)**.  

---

### **5. How can Redis be used to improve search performance?**  
- **Caching:** Store **frequent search results**.  
- **Session Management:** Manage **user sessions** for faster response.  
- **Leaderboard & Ranking:** Store **hotel popularity ranking**.  
- **Rate Limiting:** Prevent **abuse of APIs**.  
- **Geo-Indexing:** Use Redis **GeoSpatial Indexing** for **location-based searches**.  

---

### **6. How would you design the database schema for a hotel search system?**  
#### **SQL Schema (Relational - PostgreSQL/MySQL)**
```sql
CREATE TABLE hotels (
    hotel_id SERIAL PRIMARY KEY,
    name VARCHAR(255),
    address TEXT,
    city VARCHAR(100),
    country VARCHAR(100),
    latitude DECIMAL(10, 6),
    longitude DECIMAL(10, 6),
    rating DECIMAL(2,1),
    price DECIMAL(10,2),
    available_rooms INT
);

CREATE TABLE bookings (
    booking_id SERIAL PRIMARY KEY,
    user_id INT,
    hotel_id INT,
    checkin_date DATE,
    checkout_date DATE,
    total_price DECIMAL(10,2),
    FOREIGN KEY (hotel_id) REFERENCES hotels(hotel_id)
);
```
#### **NoSQL Schema (Elasticsearch, MongoDB)**
```json
{
  "hotel_id": "123",
  "name": "Grand Palace",
  "location": { "lat": 40.7128, "lon": -74.0060 },
  "city": "New York",
  "rating": 4.5,
  "price": 120,
  "amenities": ["WiFi", "Pool", "Gym"],
  "available_rooms": 10
}
```

---

### **7. How do you handle real-time availability and pricing updates in the system?**  
- **Event-Driven Architecture:** Use **Kafka or RabbitMQ** to broadcast updates.  
- **Database Triggers:** Sync price updates with **MySQL/PostgreSQL triggers**.  
- **Distributed Caching:** Use **Redis or Memcached** to update price cache instantly.  
- **WebSockets:** For **real-time UI updates** when prices change.  

---

### **8. What caching strategies would you use to optimize search queries?**  
- **Write-Through Cache:** Updates cache **immediately** when DB changes.  
- **Read-Through Cache:** Data is **fetched from DB only when needed**.  
- **Time-Based Expiry:** Set **TTL (Time-To-Live)** for hotel pricing cache.  
- **LRU (Least Recently Used):** Removes **oldest cached items** to free memory.  
- **Cache Partitioning:** Separate **popular vs less popular queries**.  

---

### **9. What is sharding, and how can it be implemented in a hotel search system?**  
- **Sharding** is **splitting database data** across **multiple servers** to improve performance.  
- **Implementation:**
  - **Range-Based Sharding:** `Shard 1 → Hotels A-M`, `Shard 2 → Hotels N-Z`.  
  - **Geo-Based Sharding:** `Shard 1 → USA`, `Shard 2 → Europe`.  
  - **Hash-Based Sharding:** Hashing **hotel_id % number_of_shards**.  
  - **Customer-Based Sharding:** `Shard 1 → Premium Users`, `Shard 2 → Regular Users`.  

---

### **10. What load-balancing strategies would you use for the hotel search engine?**  
- **Round Robin Load Balancer:** Distributes **requests evenly** across servers.  
- **Least Connections Algorithm:** Routes traffic to the **least busy server**.  
- **GeoDNS Load Balancing:** Directs users to **nearest server location**.  
- **Weighted Load Balancing:** Allocates more **traffic to powerful servers**.  
- **Auto Scaling:** Adjusts **server count dynamically** using Kubernetes.  

---
## Fifth Round (Communication Round - Cancelled for Well-Performing Candidates)

---
## HR Round
