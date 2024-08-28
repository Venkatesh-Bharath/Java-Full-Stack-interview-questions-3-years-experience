
### 1. **Can you give a brief introduction about yourself, focusing on your recent projects and the technologies you’ve worked with?**

*Answer:*  
"I am a Java developer with extensive experience in building web applications using Spring Boot and Hibernate. Recently, I worked on a student management system where I implemented a REST API using Spring Boot. The project involved creating and managing student records with features such as validation and exception handling. I used JPA for database interactions and integrated global exception handling to manage validation errors efficiently. This project helped me refine my skills in building robust and scalable applications."

### 2. **What are the key features introduced in Java 8?**

*Answer:*
- **Lambda Expressions:** Allows concise representation of anonymous functions.
- **Functional Interfaces:** Interfaces with a single abstract method, used with lambda expressions.
- **Streams API:** Enables functional-style operations on collections.
- **Optional Class:** A container object that may or may not contain a non-null value.
- **Default Methods:** Methods in interfaces with default implementations.
- **Date and Time API:** Provides a comprehensive date-time library.

### 3. **Write a Java method to withdraw an amount from an account. If the amount is available, it should be withdrawn; otherwise, throw a custom exception `InsufficientBalanceException` and handle it appropriately.**

*Answer:*

```java
public class BankAccount {
    private double balance;

    public BankAccount(double balance) {
        this.balance = balance;
    }

    public void withdraw(double amount) throws InsufficientBalanceException {
        if (amount > balance) {
            throw new InsufficientBalanceException("Insufficient balance.");
        } else {
            balance -= amount;
            System.out.println("Withdrawal successful. Remaining balance: " + balance);
        }
    }

    public double getBalance() {
        return balance;
    }
}

class InsufficientBalanceException extends Exception {
    public InsufficientBalanceException(String message) {
        super(message);
    }
}
```

### 4. **Write a JUnit test case for the withdraw method you just implemented.**

*Answer:*

```java
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

public class BankAccountTest {

    @Test
    public void testWithdrawSuccess() throws InsufficientBalanceException {
        BankAccount account = new BankAccount(1000.0);
        account.withdraw(500.0);
        assertEquals(500.0, account.getBalance());
    }

    @Test
    public void testWithdrawFailure() {
        BankAccount account = new BankAccount(300.0);
        assertThrows(InsufficientBalanceException.class, () -> account.withdraw(500.0));
    }
}
```

### 5. **Using Java 8 Streams, how would you find the frequency of each character in a string?**

*Answer:*

```java
import java.util.Map;
import java.util.function.Function;
import java.util.stream.Collectors;

public class CharacterFrequency {
    public static void main(String[] args) {
        String str = "Java 8 Streams";
        Map<Character, Long> frequencyMap = str.chars()
                .mapToObj(c -> (char) c)
                .collect(Collectors.groupingBy(Function.identity(), Collectors.counting()));

        System.out.println(frequencyMap);
    }
}
```

### 6. **Have you completed any certifications? If so, which ones, and how have they helped you in your career?**

*Answer:*  
"I have completed certifications in Java SE 8 Programmer and Spring Professional. These certifications enhanced my understanding of core Java concepts and the Spring framework, which has been instrumental in my ability to build scalable and maintainable applications. The certifications provided me with deeper insights into Java 8 features and Spring Boot best practices, which I apply in my projects to deliver high-quality software."

### 7. **Which framework are you using to write test cases in your projects?**

*Answer:*  
"I use JUnit 5 for writing test cases, along with Mockito for mocking dependencies. JUnit 5 offers advanced features and better flexibility compared to its predecessors, and Mockito helps in isolating the units of code during testing."

### 8. **Can you explain the architecture and data flow of Spring MVC?**

*Answer:*
- **Model:** Represents the data and business logic. Managed by Spring, often using JPA entities.
- **View:** The presentation layer that displays data. Implemented using technologies like JSP or Thymeleaf.
- **Controller:** Handles incoming requests, processes them, and returns a view or data. Acts as an intermediary between Model and View.
- **DispatcherServlet:** The central servlet that handles all incoming requests and routes them to appropriate controllers.
- **Flow:** The user makes a request -> DispatcherServlet forwards it to the controller -> Controller interacts with the model and returns a view name -> DispatcherServlet resolves the view and sends the response to the user.

### 9. **How does JWT token-based authentication work?**

*Answer:*
- **User Authentication:** User logs in with credentials, and the server validates them.
- **Token Generation:** Upon successful login, the server generates a JWT containing user information and signs it with a secret key.
- **Token Storage:** The client stores the JWT, typically in local storage or cookies.
- **Token Usage:** For subsequent requests, the client sends the JWT in the Authorization header.
- **Token Validation:** The server verifies the token's signature and expiration. If valid, it processes the request; otherwise, it rejects it.

### 10. **Why is REST API considered stateless?**

*Answer:*
- REST APIs are stateless because each request from the client must contain all the necessary information for the server to fulfill the request. The server does not store any session state between requests. This allows for scalability and simplicity, as the server does not need to keep track of client states.
### 11. Create a Spring Boot project using Spring Initializer. Implement two APIs (GET and POST) and handle exceptions in the project.
#### **Project Structure**

1. **Controller**
2. **Service**
3. **Repository**
4. **Entity**
5. **Exception Handling**
6. **Application Properties**

---

#### **1. Create a Spring Boot Project Using Spring Initializer**

- **Go to Spring Initializer:** Open [Spring Initializr](https://start.spring.io/).
- **Project Setup:**
  - **Project:** Maven Project
  - **Language:** Java
  - **Spring Boot Version:** 3.x.x
  - **Group:** `com.example`
  - **Artifact:** `demo`
  - **Name:** `demo`
  - **Package Name:** `com.example.demo`
  - **Packaging:** Jar
  - **Java Version:** 17
- **Dependencies:**
  - **Spring Web**
  - **Spring Boot DevTools**
  - **Spring Data JPA**
  - **H2 Database**
- **Generate the Project:** Click "Generate" to download the project as a ZIP file.
- **Import into IDE:** Extract the ZIP file and import it into your IDE.

---

#### **2. Project Code**

#### **a. Entity**

Create the `Student` entity class:

```java
package com.example.demo.model;

import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Id;
import jakarta.validation.constraints.Min;

@Entity
public class Student {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    @Min(18)
    private int age;

    // Constructors, Getters, and Setters

    public Student() {}

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

#### **b. Repository**

Create the `StudentRepository` interface:

```java
package com.example.demo.repository;

import com.example.demo.model.Student;
import org.springframework.data.jpa.repository.JpaRepository;

public interface StudentRepository extends JpaRepository<Student, Long> {
}
```

#### **c. Service**

Create the `StudentService` interface and its implementation:

**StudentService Interface:**

```java
package com.example.demo.service;

import com.example.demo.model.Student;

import java.util.List;

public interface StudentService {
    Student saveStudent(Student student);
    List<Student> getAllStudents();
    Student getStudentById(Long id);
}
```

**StudentService Implementation:**

```java
package com.example.demo.service.impl;

import com.example.demo.model.Student;
import com.example.demo.repository.StudentRepository;
import com.example.demo.service.StudentService;
import org.springframework.stereotype.Service;

import java.util.List;

@Service
public class StudentServiceImpl implements StudentService {

    private final StudentRepository studentRepository;

    public StudentServiceImpl(StudentRepository studentRepository) {
        this.studentRepository = studentRepository;
    }

    @Override
    public Student saveStudent(Student student) {
        return studentRepository.save(student);
    }

    @Override
    public List<Student> getAllStudents() {
        return studentRepository.findAll();
    }

    @Override
    public Student getStudentById(Long id) {
        return studentRepository.findById(id).orElse(null);
    }
}
```

#### **d. Controller**

Create the `StudentController` class:

```java
package com.example.demo.controller;

import com.example.demo.model.Student;
import com.example.demo.service.StudentService;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

import javax.validation.Valid;
import java.util.List;

@RestController
@RequestMapping("/api/students")
public class StudentController {

    private final StudentService studentService;

    public StudentController(StudentService studentService) {
        this.studentService = studentService;
    }

    @GetMapping
    public ResponseEntity<List<Student>> getAllStudents() {
        return new ResponseEntity<>(studentService.getAllStudents(), HttpStatus.OK);
    }

    @PostMapping
    public ResponseEntity<Student> createStudent(@Valid @RequestBody Student student) {
        return new ResponseEntity<>(studentService.saveStudent(student), HttpStatus.CREATED);
    }
}
```

#### **e. Exception Handling**

Create global exception handling for validation errors:

```java
package com.example.demo.exception;

import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.MethodArgumentNotValidException;
import org.springframework.web.bind.annotation.ControllerAdvice;
import org.springframework.web.bind.annotation.ExceptionHandler;

import java.util.LinkedHashMap;
import java.util.Map;

@ControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(MethodArgumentNotValidException.class)
    public ResponseEntity<Map<String, String>> handleValidationException(MethodArgumentNotValidException ex) {
        Map<String, String> errors = new LinkedHashMap<>();
        ex.getBindingResult().getFieldErrors().forEach(error -> {
            errors.put(error.getField(), error.getDefaultMessage());
        });
        return new ResponseEntity<>(errors, HttpStatus.BAD_REQUEST);
    }
}
```

#### **f. Application Properties**

Configure H2 database and server port in `application.properties`:

```properties
server.port=8080
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=password
spring.h2.console.enabled=true
spring.jpa.hibernate.ddl-auto=update
```

#### **g. Main Application Class**

Your main application class should look like this:

```java
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class DemoApplication {

    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }
}
```

---

#### **3. Running the Application**

1. **Run** the application by executing the `main` method in the `DemoApplication` class.
2. **Test the APIs** using tools like Postman or `curl`:
   - **GET** `/api/students` - Retrieves all students.
   - **POST** `/api/students` - Creates a new student. Use JSON body like `{"name": "John Doe", "age": 22}`.

---
