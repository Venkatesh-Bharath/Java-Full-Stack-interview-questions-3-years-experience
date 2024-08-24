
1. **Brief about the project:**
   - The project is a real-time banking application designed to handle customer transactions and registration. It includes functionalities such as account management, transaction processing, and secure data handling using microservices architecture and deployed on Docker.

2. **Steps to deploy microservices to Docker:**
   - 1. **Dockerize each microservice** by creating a `Dockerfile`.
   - 2. **Build Docker images** using the `docker build` command.
   - 3. **Run containers** using `docker run`, specifying network configurations if needed.
   - 4. **Configure networking** (optional) with Docker Compose or custom networks.
   - 5. **Monitor and scale** using Docker commands or orchestration tools.

3. **Write a SQL query to retrieve first name, last name, age from the customer table, and item, amount from the item table where age is greater than 25:**
   ```sql
   SELECT c.first_name, c.last_name, c.age, i.item, i.amount
   FROM customer c
   JOIN item i ON c.customer_id = i.customer_id
   WHERE c.age > 25;
   ```

4. **Explain Actuator in Spring Boot:**
   - Actuator provides production-ready features in Spring Boot, such as monitoring and managing applications via endpoints like health, metrics, and environment information, making it easier to maintain and troubleshoot services.

5. **What are Servlet and JSP?**
   - **Servlet**: A Java class that handles HTTP requests and generates dynamic web content.
   - **JSP (JavaServer Pages)**: A technology that allows embedding Java code into HTML to create dynamic web pages, simplifying web development by separating business logic from presentation.

6. **Describe Java Streams and Lambda functions:**
   - **Streams**: A sequence of elements supporting functional-style operations to process collections, like filtering and mapping.
   - **Lambda Functions**: Anonymous functions used to implement functional interfaces, enabling concise and readable code, especially in stream operations.

7. **What are the steps to establish a JDBC connection?**
   - 1. **Load the JDBC driver** using `Class.forName()`.
   - 2. **Establish a connection** using `DriverManager.getConnection()`.
   - 3. **Create a statement object** using `connection.createStatement()`.
   - 4. **Execute SQL queries** with `statement.executeQuery()` or `executeUpdate()`.
   - 5. **Close the connection** using `connection.close()`.

8. **Difference between StringBuffer and StringBuilder:**
   - **StringBuffer**: Synchronized and thread-safe but slower due to overhead.
   - **StringBuilder**: Non-synchronized, faster, and preferable in single-threaded environments for string manipulation.

9. **How to document request and response options using Swagger, and how to convert to YAML?**
   - Swagger annotations in code (e.g., `@ApiOperation`, `@ApiResponse`) document API endpoints. Convert the generated Swagger JSON documentation to YAML using tools like Swagger Editor or online converters.

10. **How do you expose REST API call endpoints?**
    - Expose endpoints by annotating controller methods with `@GetMapping`, `@PostMapping`, etc., and defining the URI paths in Spring Boot applications.

11. **Which mechanism did you use to develop the project?**
    - The project was developed using a microservices architecture with Spring Boot for creating RESTful services, Docker for containerization, and a CI/CD pipeline for automated deployments.

12. **What are implicit objects in JSP?**
    - Implicit objects are pre-defined objects available in JSP for accessing various functionalities like `request`, `response`, `session`, `application`, `out`, and more, without explicit declaration.

13. **Create two lists: List 1 (java, aws, oracle, python), List 2 (java, oracle, jquery). Find common elements and unique elements using Streams in Java code:**

   ```java
   List<String> list1 = Arrays.asList("java", "aws", "oracle", "python");
   List<String> list2 = Arrays.asList("java", "oracle", "jquery");

   // Common elements
   List<String> common = list1.stream()
       .filter(list2::contains)
       .collect(Collectors.toList());

   // Unique elements
   List<String> unique = Stream.concat(list1.stream(), list2.stream())
       .distinct()
       .filter(e -> !(list1.contains(e) && list2.contains(e)))
       .collect(Collectors.toList());
   ```
