## Assessment 
### Spring Boot App - HackerRank Assessment 
### 5 Multiple Choice Questions (MCQs)

## First Round Interview 

### 1. Explain the concept of OOP (Object-Oriented Programming) in Java.
   - **Answer:** OOP in Java is a programming paradigm based on the concept of objects, which can contain data and code. The four main principles of OOP are encapsulation, inheritance, polymorphism, and abstraction.

### 2. What are the differences between `==` and `equals()` in Java?
   - **Answer:** `==` checks for reference equality, meaning it checks whether two references point to the same object in memory. `equals()` checks for value equality, meaning it checks whether two objects are meaningfully equivalent.

### 3. How does Java handle memory management?
   - **Answer:** Java uses an automatic garbage collection mechanism to manage memory. It allocates memory on the heap for new objects and reclaims memory from objects that are no longer referenced.

### 4. How do you handle exceptions in Java?
   - **Answer:** Exceptions in Java are handled using try-catch blocks, where code that might throw an exception is placed inside the try block and exception handling code is placed inside the catch block.

### 5. What are checked and unchecked exceptions in Java?
   - **Answer:** Checked exceptions are exceptions that must be either caught or declared in the method signature using the `throws` keyword. Unchecked exceptions are exceptions that do not need to be explicitly handled, typically subclasses of `RuntimeException`.

### 6. How do you handle exceptions in Spring Boot applications?
   - **Answer:** Spring Boot provides the `@ExceptionHandler` annotation to handle exceptions in a controller. Additionally, `@ControllerAdvice` can be used to define global exception handlers for the entire application.

### 7. Given a list of employees, find the list of employees based on gender. Result should be - Male, [e1, e2, e3] Female, [e4, e5].
   - **Answer:**
   ```java
   Map<String, List<Employee>> employeesByGender = employees.stream()
       .collect(Collectors.groupingBy(Employee::getGender));
   ```

### 8. Explain the basics of Spring Boot.
   - **Answer:** Spring Boot simplifies the development of Spring applications by providing a set of tools and libraries for rapid application development. It offers features like auto-configuration, standalone application configuration, and embedded servers.

### 9. Write a code example for a JPA repository and a derived query.
   - **Answer:**
   ```java
   @Repository
   public interface EmployeeRepository extends JpaRepository<Employee, Long> {
       List<Employee> findByGender(String gender);
   }
   ```

### 10. Explain thread pools and their use in Java.
   - **Answer:**  Thread pools manage a collection of reusable threads for executing tasks, which improves application performance by reducing the overhead of creating and destroying threads. Java provides `ExecutorService` to manage thread pools.

### 11. Configure HikariCP in a Spring Boot application.
   - **Answer:**  
   ```yaml
    spring:
      datasource:
        url: jdbc:mysql://localhost:3306/db
        username: user
        password: pass
        hikari:
          maximum-pool-size: 10
   ```


### 12. Explain Hibernate queries and entity graphs.
- **Answer:**   Hibernate queries can be written using HQL or Criteria API. Entity graphs optimize queries by defining which related entities should be fetched, reducing the number of queries executed and improving performance.

### 13. How do you write test cases differently for controller, data, and service layers?
   - **Answer:**    
   ```java
    // Controller Test
    @WebMvcTest(EmployeeController.class)
    public class EmployeeControllerTest {
        @Autowired
        private MockMvc mockMvc;

        @MockBean
        private EmployeeService employeeService;

        @Test
        public void testGetEmployee() throws Exception {
            mockMvc.perform(get("/employees/1"))
                .andExpect(status().isOk())
                .andExpect(jsonPath("$.name").value("John"));
        }
    }

    // Service Test
    @ExtendWith(MockitoExtension.class)
    public class EmployeeServiceTest {
        @Mock
        private EmployeeRepository employeeRepository;

        @InjectMocks
        private EmployeeService employeeService;

        @Test
        public void testFindEmployeeById() {
            when(employeeRepository.findById(1L)).thenReturn(Optional.of(new Employee("John")));
            Employee employee = employeeService.findEmployeeById(1L);
            assertEquals("John", employee.getName());
        }
    }

    // Repository Test
    @DataJpaTest
    public class EmployeeRepositoryTest {
        @Autowired
        private EmployeeRepository employeeRepository;

        @Test
        public void testFindByGender() {
            List<Employee> employees = employeeRepository.findByGender("Male");
            assertEquals(3, employees.size());
        }
    }
   ```

### 14. Explain code coverage and tools like SonarQube.
 - **Answer:**  Code coverage measures how much of the code is tested by unit tests. Tools like SonarQube analyze code quality, including code coverage, and provide reports to help improve code reliability and maintainability.

### 15. What are deployment tools and how do they work?
  - **Answer:**   - **Answer:** Deployment tools like Jenkins, Docker, and Kubernetes automate the process of deploying applications, ensuring consistent environments and simplifying scaling and management.

### 16. Difference between vanilla JavaScript and React.
  - **Answer:**  Vanilla JavaScript is a plain JavaScript without any libraries or frameworks. React is a library for building user interfaces, offering components, state management, and virtual DOM for efficient updates.

### 17. Explain useState and useEffect hooks in React.
   - **Answer:** `useState` is a hook that lets you add state to functional components. `useEffect` is a hook for performing side effects, such as data fetching or updating the DOM, in functional components.

### 18. Write a basic API call using React.
   - **Answer:** 
   ```javascript
    useEffect(() => {
      fetch('https://api.example.com/data')
        .then(response => response.json())
        .then(data => setData(data));
    }, []);
   ```

### 19. Transform an IP address from `192.62.255.31` to `291.26.552.13`.
   - **Answer:** 
   ```javascript
    function transformIP(ip) {
        return ip.split('.').map(octet => {
            return octet.split('').reverse().join('');
        }).join('.');
    }
    console.log(transformIP('192.62.255.31')); // 291.26.552.13
   ```
## Second Round Interview: Pair Programming
### 1. Develop a UI page to show a list of items in the search page using React.
   - **Answer:**
   ```javascript
   import React, { useState, useEffect } from 'react';

   const ItemList = () => {
       const [items, setItems] = useState([]);
       const [searchTerm, setSearchTerm] = useState('');

       useEffect(() => {
           fetch('http://localhost:8080/api/items')
               .then(response => response.json())
               .then(data => setItems(data));
       }, []);

       const filteredItems = items.filter(item => item.name.includes(searchTerm));

       return (
           <div>
               <input
                   type="text"
                   placeholder="Search items"
                   value={searchTerm}
                   onChange={e => setSearchTerm(e.target.value)}
               />
               <ul>
                   {filteredItems.map(item => (
                       <li key={item.id}>{item.name}</li>
                   ))}
               </ul>
           </div>
       );
   };

   export default ItemList;
   ```

### 2. Write an API with Spring Boot and use the API endpoint in React to show the list.
   - **Spring Boot API:**
   ```java
   @RestController
   @RequestMapping("/api/items")
   public class ItemController {
       @Autowired
       private ItemService itemService;
   
       @GetMapping
       public List<Item> getAllItems() {
           return itemService.getAllItems();
       }
   }
   
   @Service
   public class ItemService {
       @Autowired
       private ItemRepository itemRepository;
   
       public List<Item> getAllItems() {
           return itemRepository.findAll();
       }
   }
   
   @Repository
   public interface ItemRepository extends JpaRepository<Item, Long> {}
   
   @Entity
   public class Item {
       @Id
       @GeneratedValue(strategy = GenerationType.IDENTITY)
       private Long id;
       private String name;

       // getters and setters
   }
   ```

   - **React Integration:**
   ```javascript
   import React, { useState, useEffect } from 'react';

   const ItemList = () => {
       const [items, setItems] = useState([]);

       useEffect(() => {
           fetch('http://localhost:8080/api/items')
               .then(response => response.json())
               .then(data => setItems(data));
       }, []);

       return (
           <ul>
               {items.map(item => (
                   <li key={item.id}>{item.name}</li>
               ))}
           </ul>
       );
   };

   export default ItemList;
   ```
