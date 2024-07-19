
# Assessment
2 DSA Coding
30 Multiple Choice Questions (MCQs)

# First Round Interview 
### 1. Self-introduction
- **Answer:** *********
### 2. Which version of Java are you using?

- **Answer:** I am using Java **.

### 3. Java 8 features

- **Answer:**
  
1. **Lambda Expressions**: Allows for more concise and readable code by enabling you to pass behavior as parameters. For example:
   ```java
   (a, b) -> a + b
   ```

2. **Streams API**: Provides a powerful way to process sequences of elements (like collections) in a functional style, supporting operations like filtering, mapping, and reducing. For example:
   ```java
   List<String> list = Arrays.asList("a1", "a2", "b1", "c2");
   list.stream()
       .filter(s -> s.startsWith("a"))
       .map(String::toUpperCase)
       .sorted()
       .forEach(System.out::println);
   ```

3. **New Date and Time API**: Introduces a new set of classes to handle date and time with better precision and immutability compared to the old `Date` and `Calendar` classes. For example:
   ```java
   LocalDate today = LocalDate.now();
   LocalDate tomorrow = today.plusDays(1);
   ```

4. **Default Methods in Interfaces**: Allows interfaces to have method implementations, which helps in extending interfaces without breaking existing implementations. For example:
   ```java
   interface MyInterface {
       default void defaultMethod() {
           System.out.println("Default implementation");
       }
       void abstractMethod();
   }
   ```

5. **Optional Class**: Provides a container object which may or may not contain a value, helping to avoid null checks and NullPointerExceptions. For example:
   ```java
   Optional<String> opt = Optional.of("Hello");
   opt.ifPresent(System.out::println);  // Prints "Hello"
   ```


### 4. Java 9 static method

- **Answer:** Java 9 introduced private methods in interfaces that can be static or non-static to share code between methods.

### 5. List.of method

- **Answer:** `List.of()` creates an immutable list with the provided elements. For example, 
   `List<String> list = List.of("A", "B", "C");`.

### 6. Functional interface and example

- **Answer:** A functional interface has exactly one abstract method. Example: `@FunctionalInterface public interface Calculator { int add(int a, int b); }`.

### 7. What is Supplier in functional programming

- **Answer:** `Supplier` is a functional interface that provides a result of type `T` without taking any input.

### 8. Create one functional interface containing add method, static sum method, default multiple method, and use in main class
- **Answer:**
   ```java
   @FunctionalInterface
   public interface Calculator {
       int add(int a, int b);
       
       static int sum(int a, int b) {
           return a + b;
       }
       
       default int multiply(int a, int b) {
           return a * b;
       }
   }

   public class Main {
       public static void main(String[] args) {
           Calculator calc = (a, b) -> a + b;
           System.out.println("Add: " + calc.add(5, 3));
           System.out.println("Sum: " + Calculator.sum(5, 3));
           System.out.println("Multiply: " + calc.multiply(5, 3));
       }
   }
   ```

### 9. Using streams, list of employees and count number of male and female employees
- **Answer:**
   ```java
      public Map<String, Long> countEmployeesByGender(List<Employee> employees) {
        return employees.stream()
                .collect(Collectors.groupingBy(Employee::getGender, Collectors.counting()));
    }
   ```

### 10. employees.stream().filter(e -> e.getAge() > 18).map(e -> e.remove()).count() what will be the output

- **Answer:** The output depends on whether `remove()` modifies the original list or not. If it does, it will be the count of items that are removed. If not, it will be 0.

### 11. What is terminal operations

- **Answer:** Terminal operations produce a result or a side-effect, and they mark the end of the stream pipeline. Examples include `collect()`, `count()`, and `forEach()`.

### 12. Spring Boot controller using all annotations POST & GET vehicle details
- **Answer:**
```java
  
@RestController
@RequestMapping("/vehicles")
public class VehicleController {

    @PostMapping
    public ResponseEntity<Vehicle> addVehicle(@RequestBody Vehicle vehicle) {
        // Save vehicle to database
        return ResponseEntity.status(HttpStatus.CREATED).body(vehicle);
    }

    @GetMapping("/{id}")
    public ResponseEntity<Vehicle> getVehicle(@PathVariable Long id) {
        // Fetch vehicle from database
        Vehicle vehicle = findVehicleById(id);
        return ResponseEntity.ok(vehicle);
    }
}

```

### 13. What are the issues you faced in Spring Boot development?

- **Answer:** Common issues include configuration errors, dependency conflicts, and difficulty in debugging complex applications.

### 14. Which version of Spring Boot are you using?

- **Answer:** I am using Spring Boot **.

### 15. Primary & Qualifier annotation in Spring Boot

- **Answer:** `@Primary` specifies the default bean when multiple beans of the same type exist. `@Qualifier` is used to specify which bean to inject when multiple candidates are available.

### 16. How to use two different databases in a single Spring Boot application

- **Answer:** Configure multiple `DataSource` beans and use `@Primary` to indicate the default `DataSource`. Use `@Qualifier` to inject the appropriate `DataSource` where needed.
  
```java
@Configuration
public class DataSourceConfig {

    @Bean
    @Primary
    @ConfigurationProperties("spring.datasource1")
    public DataSource dataSource1() {
        return DataSourceBuilder.create().build();
    }

    @Bean
    @ConfigurationProperties("spring.datasource2")
    public DataSource dataSource2() {
        return DataSourceBuilder.create().build();
    }
}

```
### 17. JPA methods and @Query

- **Answer:** JPA methods include `findAll()`, `findById()`, `save()`, and `delete()`. `@Query` allows defining custom JPQL or SQL queries.

### 18. How to get data for employee {id, name, address{id, location}} and fetch location based on employee data

- **Answer:**

  ```java
     public interface EmployeeRepository extends JpaRepository<Employee, Long> {

    // Exact match
    List<Employee> findByAddressLocation(String location);

    // Partial match
    List<Employee> findByAddressLocationContaining(String location);
   }
  ```

### 19. Why is React fast and what is virtual DOM

- **Answer:**  React is fast due to its use of the virtual DOM, which minimizes direct manipulation of the actual DOM, reducing performance overhead.

### 20. Virtual DOM internal structure

- **Answer:**  The virtual DOM is a lightweight copy of the real DOM. It represents the UI components as JavaScript objects, which React updates efficiently.

### 21. Which component do you use: functional or class-based

- **Answer:**  I use both functional and class-based components, but prefer functional components due to their simplicity and hooks support.

### 22. Other than useState and useEffect, which hooks do you use

- **Answer:**  I use `useContext`, `useReducer`, `useMemo`, and `useCallback` hooks.

23. What is useContext

- **Answer:**  `useContext` allows accessing context values in functional components, enabling state sharing across the component tree without prop drilling.

### 24. Context API alternate in React

- **Answer:**: Alternatives include Redux for state management or React's `useState` and `useReducer` for local state.

### 25. Hoisting in JavaScript

- **Answer:** Hoisting refers to JavaScript's behavior of moving variable and function declarations to the top of their containing scope during compilation.

### 26. What is prototype

- **Answer:** In JavaScript, `prototype` is an object from which other objects inherit properties and methods. Every JavaScript object has a prototype.

