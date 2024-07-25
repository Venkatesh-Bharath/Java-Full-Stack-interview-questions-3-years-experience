
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

- **Answer:** A functional interface has exactly one abstract method.
- Example: `@FunctionalInterface public interface Calculator { int add(int a, int b); }`.

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

- **Answer:** `@Primary` specifies the default bean when multiple beans of the same type exist.
-  `@Qualifier` is used to specify which bean to inject when multiple candidates are available.

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


# Second Round Interview -Pair Programming

### 1 Implement `POST` and `GET` APIs for a Vehicle resource in Spring Boot. Provide the code for repository, service, and controller layers. Include JUnit test cases for the `POST` and `GET` methods.

**Answer:**

- **Repository Layer:**

    ```java
    import org.springframework.data.jpa.repository.JpaRepository;

    public interface VehicleRepository extends JpaRepository<Vehicle, Long> {
    }
    ```

- **Service Layer:**

    ```java
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.stereotype.Service;

    import java.util.List;

    @Service
    public class VehicleService {

        @Autowired
        private VehicleRepository vehicleRepository;

        public List<Vehicle> getAllVehicles() {
            return vehicleRepository.findAll();
        }

        public Vehicle saveVehicle(Vehicle vehicle) {
            return vehicleRepository.save(vehicle);
        }
    }
    ```

- **Controller Layer:**

    ```java
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.http.HttpStatus;
    import org.springframework.http.ResponseEntity;
    import org.springframework.web.bind.annotation.*;

    import java.util.List;

    @RestController
    @RequestMapping("/vehicles")
   @CrossOrigin(origins = "http://localhost:3000") 
    public class VehicleController {

        @Autowired
        private VehicleService vehicleService;

        @GetMapping
        public ResponseEntity<List<Vehicle>> getAllVehicles() {
            List<Vehicle> vehicles = vehicleService.getAllVehicles();
            return new ResponseEntity<>(vehicles, HttpStatus.OK);
        }

        @PostMapping
        public ResponseEntity<Vehicle> createVehicle(@RequestBody Vehicle vehicle) {
            Vehicle savedVehicle = vehicleService.saveVehicle(vehicle);
            return new ResponseEntity<>(savedVehicle, HttpStatus.CREATED);
        }
    }
    ```

- **JUnit Test Cases:**

### 1. Repository Layer Test

Since the repository layer interacts directly with the database, you typically use an in-memory database or a test configuration to test repository methods. For JPA repositories, the most common approach is to use an embedded H2 database or similar for integration tests.

**`VehicleRepositoryTest.java`**

```java
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.orm.jpa.DataJpaTest;
import org.springframework.test.context.ActiveProfiles;

import java.util.List;

import static org.assertj.core.api.Assertions.assertThat;

@DataJpaTest
public class VehicleRepositoryTest {

    @Autowired
    private VehicleRepository vehicleRepository;

    @BeforeEach
    public void setUp() {
        vehicleRepository.deleteAll();
    }

    @Test
    public void testSaveVehicle() {
        Vehicle vehicle = new Vehicle();
        vehicle.setMake("Ford");
        vehicle.setModel("Focus");
        vehicle.setYear(2021);

        Vehicle savedVehicle = vehicleRepository.save(vehicle);
        assertThat(savedVehicle).isNotNull();
        assertThat(savedVehicle.getId()).isNotNull();
    }

    @Test
    public void testFindAllVehicles() {
        Vehicle vehicle1 = new Vehicle();
        vehicle1.setMake("Toyota");
        vehicle1.setModel("Corolla");
        vehicle1.setYear(2020);
        vehicleRepository.save(vehicle1);

        Vehicle vehicle2 = new Vehicle();
        vehicle2.setMake("Honda");
        vehicle2.setModel("Civic");
        vehicle2.setYear(2019);
        vehicleRepository.save(vehicle2);

        List<Vehicle> vehicles = vehicleRepository.findAll();
        assertThat(vehicles).hasSize(2);
    }
}
```

### 2. Service Layer Test

The service layer test verifies that the service methods are functioning correctly. This typically involves mocking the repository and ensuring that the service methods interact with the repository as expected.

**`VehicleServiceTest.java`**

```java
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import org.mockito.InjectMocks;
import org.mockito.Mock;
import org.mockito.MockitoAnnotations;
import org.springframework.boot.test.context.SpringBootTest;

import java.util.List;

import static org.assertj.core.api.Assertions.assertThat;
import static org.mockito.Mockito.when;

@ExtendWith(MockitoExtension.class)
public class VehicleServiceTest {

    @Mock
    private VehicleRepository vehicleRepository;

    @InjectMocks
    private VehicleService vehicleService;

    @BeforeEach
    public void setUp() {
        MockitoAnnotations.openMocks(this);
    }

    @Test
    public void testGetAllVehicles() {
        Vehicle vehicle1 = new Vehicle();
        vehicle1.setMake("Toyota");
        vehicle1.setModel("Corolla");
        vehicle1.setYear(2020);

        Vehicle vehicle2 = new Vehicle();
        vehicle2.setMake("Honda");
        vehicle2.setModel("Civic");
        vehicle2.setYear(2019);

        when(vehicleRepository.findAll()).thenReturn(List.of(vehicle1, vehicle2));

        List<Vehicle> vehicles = vehicleService.getAllVehicles();
        assertThat(vehicles).hasSize(2);
        assertThat(vehicles.get(0).getMake()).isEqualTo("Toyota");
        assertThat(vehicles.get(1).getMake()).isEqualTo("Honda");
    }

    @Test
    public void testSaveVehicle() {
        Vehicle vehicle = new Vehicle();
        vehicle.setMake("Ford");
        vehicle.setModel("Focus");
        vehicle.setYear(2021);

        when(vehicleRepository.save(vehicle)).thenReturn(vehicle);

        Vehicle savedVehicle = vehicleService.saveVehicle(vehicle);
        assertThat(savedVehicle).isNotNull();
        assertThat(savedVehicle.getMake()).isEqualTo("Ford");
    }
}
```
### 3. Controller Layer Test

Test the controller by mocking the service layer to isolate it. Use MockMvc to perform HTTP requests to controller endpoints and verify the correct status codes and response bodies. Ensure to check if the controller handles the HTTP requests as expected and returns the appropriate responses.

 **`VehicleControllerTest.java`**

 ```java
    import com.fasterxml.jackson.databind.ObjectMapper;
    import org.junit.jupiter.api.Test;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.boot.test.autoconfigure.web.servlet.WebMvcTest;
    import org.springframework.boot.test.mock.mockito.MockBean;
    import org.springframework.http.MediaType;
    import org.springframework.test.web.servlet.MockMvc;
    import org.springframework.test.web.servlet.request.MockMvcRequestBuilders;
    import org.springframework.test.web.servlet.result.MockMvcResultMatchers;

    import java.util.List;

    import static org.mockito.ArgumentMatchers.any;
    import static org.mockito.Mockito.when;

    @WebMvcTest(VehicleController.class)
    public class VehicleControllerTest {

        @Autowired
        private MockMvc mockMvc;

        @MockBean
        private VehicleService vehicleService;

        @Autowired
        private ObjectMapper objectMapper;

        @Test
        public void testGetAllVehicles() throws Exception {
            when(vehicleService.getAllVehicles()).thenReturn(List.of(
                new Vehicle(1L, "Toyota", "Corolla", 2020),
                new Vehicle(2L, "Honda", "Civic", 2019)
            ));

            mockMvc.perform(MockMvcRequestBuilders.get("/vehicles"))
                   .andExpect(MockMvcResultMatchers.status().isOk())
                   .andExpect(MockMvcResultMatchers.jsonPath("$[0].make").value("Toyota"))
                   .andExpect(MockMvcResultMatchers.jsonPath("$[1].make").value("Honda"));
        }

        @Test
        public void testCreateVehicle() throws Exception {
            Vehicle vehicle = new Vehicle();
            vehicle.setMake("Ford");
            vehicle.setModel("Focus");
            vehicle.setYear(2021);

            when(vehicleService.saveVehicle(any(Vehicle.class))).thenReturn(vehicle);

            mockMvc.perform(MockMvcRequestBuilders.post("/vehicles")
                   .contentType(MediaType.APPLICATION_JSON)
                   .content(objectMapper.writeValueAsString(vehicle)))
                   .andExpect(MockMvcResultMatchers.status().isCreated())
                   .andExpect(MockMvcResultMatchers.jsonPath("$.make").value("Ford"));
        }
    }
 ```

### 2 Implement a React component that fetches vehicle data from the backend, displays it in a grid, and write a test case for the component.

**Answer:**

- **React Component:**

    **`VehicleList.js`**

    ```jsx
    import React, { useEffect, useState } from 'react';
    import axios from 'axios';

    const VehicleList = () => {
        const [vehicles, setVehicles] = useState([]);
        const [error, setError] = useState(null);

        useEffect(() => {
            axios.get('http://localhost:8080/vehicles')
                .then(response => {
                    setVehicles(response.data);
                })
                .catch(error => {
                    setError("There was an error fetching the vehicles.");
                    console.error("There was an error fetching the vehicles!", error);
                });
        }, []);

        return (
            <div className="vehicle-list">
                <h1>Vehicle List</h1>
                {error && <p className="error">{error}</p>}
                <div className="grid-container">
                    {vehicles.map(vehicle => (
                        <div key={vehicle.id} className="grid-item">
                            <h3>{vehicle.make} {vehicle.model}</h3>
                            <p>Year: {vehicle.year}</p>
                        </div>
                    ))}
                </div>
            </div>
        );
    };

    export default VehicleList;
    ```

    **CSS (for grid layout):**

    **`App.css`**

    ```css
    .vehicle-list {
        padding: 20px;
    }

    .grid-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
        gap: 20px;
    }

    .grid-item {
        border: 1px solid #ddd;
        padding: 10px;
        border-radius: 5px;
    }
    ```

- **React Test Case:**

    **`VehicleList.test.js`**

    ```jsx
    import React from 'react';
    import { render, screen } from '@testing-library/react';
    import axios from 'axios';
    import VehicleList from './VehicleList';
    import '@testing-library/jest-dom/extend-expect';

    // Mocking Axios
    jest.mock('axios');

    test('renders vehicle list', async () => {
        // Mocking the response data
        axios.get.mockResolvedValue({
            data: [
                { id: 1, make: 'Toyota', model: 'Corolla', year: 2020 },
                { id: 2, make: 'Honda', model: 'Civic', year: 2019 },
            ],
        });

        render(<VehicleList />);

        // Assertions
        expect(await screen.findByText(/Toyota Corolla/i)).toBeInTheDocument();
        expect(await screen.findByText(/Honda Civic/i)).toBeInTheDocument();
    });

    test('handles error response', async () => {
        // Mocking the error response
        axios.get.mockRejectedValue(new Error("Network Error"));

        render(<VehicleList />);

        // Assertions
        expect(await screen.findByText(/There was an error fetching the vehicles./i)).toBeInTheDocument();
    });
    ```

