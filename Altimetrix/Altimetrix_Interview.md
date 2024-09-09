# Altimetrix Company

1. **Briefly explain the project you are currently working on.**
   - I am currently working on a microservices-based banking application that handles user registration and transaction data. The project uses Spring Boot for the backend, ReactJS for the frontend, and JPA for database interactions. We also implement security using Spring Security and JWT for authentication.

2. **What is Jenkins, and how do you use it in your project?**
   - Jenkins is a continuous integration/continuous deployment (CI/CD) tool used to automate the build and deployment process. In my project, Jenkins is configured to build the application automatically whenever there is a new commit to the Git repository. It also runs unit tests, integration tests, and deploys the application to the staging/production environment.

3. **Which tools do you use for monitoring purposes in Spring Boot?**
   - We use tools like **Prometheus** and **Grafana** for monitoring metrics, **Spring Boot Actuator** for exposing health and metrics endpoints, and **ELK Stack (Elasticsearch, Logstash, Kibana)** for logging and real-time monitoring.

4. **What Git commands do you commonly use in your project?**
   - Common Git commands include:
     - `git clone`: Clone a repository
     - `git pull`: Fetch and merge changes from the remote repository
     - `git push`: Push local changes to the remote repository
     - `git branch`: Create, list, or switch branches
     - `git checkout`: Switch between branches or restore files
     - `git merge`: Merge branches
     - `git commit -m "message"`: Commit changes with a message
     - `git stash`: Temporarily save changes not ready to commit

5. **What is Agile methodology? Explain your experience working in Agile.**
   - Agile methodology is an iterative approach to software development where requirements and solutions evolve through collaboration between cross-functional teams. I have experience working in Agile, specifically using **Scrum**. We follow sprints, conduct daily standups, sprint planning, and retrospective meetings. This approach allows us to quickly adapt to changes and deliver incremental updates.

6. **What is the difference between shallow copy and deep copy?**
   - **Shallow Copy**: Creates a new object, but copies the references to the same memory addresses of the objects inside. Changes to the internal objects affect both copies.
   - **Deep Copy**: Creates a new object and recursively copies all objects within it, meaning both the original and copied objects are independent of each other.

7. **How many ways can you create an object in Java?**
   - There are several ways to create an object in Java:
     1. Using the `new` keyword.
     2. Using reflection (`Class.newInstance()` or `Constructor.newInstance()`).
     3. Using **clone()** (if the class implements `Cloneable`).
     4. Using **serialization** and **deserialization**.
     5. Using the `Factory` or `Builder` design pattern.

8. **Why is the main method in Java static?**
   - The main method is static because it can be called without creating an instance of the class. This allows the JVM to call it directly to start the program.

9. **What is a deadlock in Java?**
   - A deadlock occurs when two or more threads are blocked forever, waiting for each other to release a lock they need to proceed. Each thread holds a resource the other thread requires, leading to a cycle of dependency.

10. **How can we avoid deadlock in Java?**
    - To avoid deadlock:
      1. Always acquire locks in a consistent order.
      2. Use a **timeout** for acquiring locks.
      3. Use fewer synchronized blocks or locks, and keep them as short as possible.
      4. Use **lock hierarchy** or **deadlock detection algorithms**.

11. **Do you know any design patterns?**
    - Yes, I am familiar with several design patterns like **Singleton**, **Factory**, **Builder**, **Observer**, **Strategy**, and **Decorator**.

12. **What is the Factory Design Pattern?**
    - The **Factory Design Pattern** is a creational pattern that provides an interface for creating objects in a super class, but allows subclasses to alter the type of objects that will be created. It promotes loose coupling and is used when the object creation process involves some logic.

13. **Check if a given string containing brackets is balanced.**
    - Approach: Use a stack to track the open brackets and check for matching closing brackets.
    ```java
    public boolean isBalanced(String str) {
        Stack<Character> stack = new Stack<>();
        for (char ch : str.toCharArray()) {
            if (ch == '(' || ch == '{' || ch == '[') {
                stack.push(ch);
            } else if (ch == ')' && (stack.isEmpty() || stack.pop() != '(')) {
                return false;
            } else if (ch == '}' && (stack.isEmpty() || stack.pop() != '{')) {
                return false;
            } else if (ch == ']' && (stack.isEmpty() || stack.pop() != '[')) {
                return false;
            }
        }
        return stack.isEmpty();
    }
    ```

14. **Find the most repeated IP address.**
    - Approach: Use a HashMap to count the occurrences of each IP.
    ```java
    public String findMostRepeatedIP(List<String> logs) {
        Map<String, Integer> ipCount = new HashMap<>();
        for (String log : logs) {
            String ip = log.split(" ")[0];
            ipCount.put(ip, ipCount.getOrDefault(ip, 0) + 1);
        }
        return Collections.max(ipCount.entrySet(), Map.Entry.comparingByValue()).getKey();
    }
    ```

15. **How do you communicate between two microservices?**
    - Communication between microservices can be done using **REST APIs** (synchronous) or **message brokers** like RabbitMQ or Kafka (asynchronous). REST APIs use HTTP requests, while message brokers allow communication through event-driven architecture.

16. **How do you secure communication between microservices?**
    - You can secure communication using:
      1. **JWT** (JSON Web Tokens) for authentication and authorization.
      2. **OAuth2** for secure access delegation.
      3. **SSL/TLS** for encrypted communication.
      4. **API Gateway** with security filters to control traffic and access.

17. **Have you worked with JPA (Java Persistence API)?**
    - Yes, I have used JPA in my projects for managing database entities, relationships, and queries using **Hibernate** as the JPA provider. I also work with annotations like `@Entity`, `@OneToMany`, `@ManyToOne`, and `@Query`.

18. **What is the N+1 select problem in JPA, and how do you handle it?**
    - The **N+1 select problem** occurs when a query retrieves an entity, but subsequent queries are made to load related entities one by one. It can be handled using:
      - **FetchType.LAZY** or **FetchType.EAGER**.
      - Using **JOIN FETCH** queries to load related entities in a single query.

19. **Have you worked on writing unit test cases? How do you approach it?**
    - Yes, I write unit test cases using **JUnit** and **Mockito**. My approach is to test individual methods, mock external dependencies, and ensure high code coverage by writing tests for both positive and negative scenarios.

20. **How do you mock private methods in unit testing?**
    - Private methods can be mocked using **PowerMock** along with Mockito, which allows for mocking private, static, and final methods.

# Altimetrix Client L1
___soon
