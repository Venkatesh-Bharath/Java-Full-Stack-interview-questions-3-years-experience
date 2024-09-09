### 1. **Explain your project briefly.**
My project involves [describe your project here], utilizing technologies such as Spring Boot, React, microservices, and databases. The core functionality includes [key features], and I was responsible for [your role].

---

### 2. **Given an array of integers and a number ‘sum’, print all pairs in the array whose sum equals ‘sum’.**
```java
public class PairSum {
    public static void main(String[] args) {
        int[] arr = {1, 5, 7, -1, 5};
        int exp = 6;
		Map<Integer,Integer> map=new LinkedHashMap<>();
		  for(int i=0;i<arr.length;i++) {
			int e=arr[i];
			int dif=exp-e;
			if(map.containsKey(dif)) {
				for(int j=1;j<=map.get(dif);j++)
			  	System.out.println("("+dif+","+e+")");		
			}
			map.put(e,map.getOrDefault(e,0)+1);
    }
}
```

---

### 3. **Design a table structure for books and members**
- **Books Table:**
  - BookID (Primary Key)
  - Title
  - AuthorID (Foreign Key)

- **Authors Table:**
  - AuthorID (Primary Key)
  - Name

- **Members Table:**
  - MemberID (Primary Key)
  - Name

- **Borrowing Table:**
  - BorrowID (Primary Key)
  - MemberID (Foreign Key)
  - BookID (Foreign Key)
  - BorrowDate
  - DueDate
  - ReturnDate

---

### 4. **What happens if an exception is thrown in a method? Explain with a code example.**
When an exception is thrown in a method, it disrupts the normal flow of the program. If the exception is not caught, the method terminates and the exception is propagated to the calling method.
```java
public class ExceptionExample {
    public static void main(String[] args) {
        try {
            divide(10, 0);
        } catch (ArithmeticException e) {
            System.out.println("Caught Exception: " + e);
        }
    }

    public static int divide(int a, int b) throws ArithmeticException {
        return a / b;  // This will throw ArithmeticException if b is 0
    }
}
```

---

### 5. **What is dependency injection?**
Dependency injection is a design pattern used in Spring to manage object dependencies by injecting them at runtime rather than defining them manually in code. It promotes loose coupling and testability.

---

### 6. **Give an example of dependency injection in Spring Boot.**
```java
@Service
public class EmployeeService {
    public String getEmployee() {
        return "Employee Details";
    }
}

@RestController
public class EmployeeController {
    private final EmployeeService employeeService;

    @Autowired
    public EmployeeController(EmployeeService employeeService) {
        this.employeeService = employeeService;
    }

    @GetMapping("/employee")
    public String getEmployee() {
        return employeeService.getEmployee();
    }
}
```

---

### 7. **How do you pass dependency from the controller to the service in Spring Boot?**
You pass the service class dependency to the controller class by using the `@Autowired` annotation in Spring Boot. This allows Spring to inject the service object at runtime.

---

### 8. **List some common Spring Boot annotations.**
- `@SpringBootApplication`: Entry point for Spring Boot applications.
- `@Autowired`: Inject dependencies automatically.
- `@RestController`: Combines `@Controller` and `@ResponseBody`.
- `@Service`: Marks a class as a service provider.
- `@Repository`: Marks a class as a DAO.
- `@GetMapping`, `@PostMapping`: Used for handling HTTP GET/POST requests.

---

### 9. **How do you store unique employee names in a `Map` in Java?**
```java
Map<String, Employee> employeeMap = new HashMap<>();
employeeMap.put("John", new Employee("John"));
employeeMap.put("Alice", new Employee("Alice"));
// Ensure employee names are unique when inserting into the map.
```

---

### 10. **How do you sort a list of employees based on employee names?**
```java
List<Employee> employees = new ArrayList<>();
employees.add(new Employee("John"));
employees.add(new Employee("Alice"));

employees.sort(Comparator.comparing(Employee::getName));
```

---

### 11. **How do you retrieve database data based on a particular page in Spring Boot?**
You can use `Pageable` from Spring Data JPA to retrieve data based on pagination:
```java
Pageable pageable = PageRequest.of(pageNumber, pageSize);
Page<Employee> employees = employeeRepository.findAll(pageable);
```

---

### 12. **How do you write a query to get data for a specific page in a database?**
```sql
SELECT * FROM employees LIMIT 10 OFFSET 20;
```
This will fetch 10 records starting from the 21st record (for pagination).

---

### 13. **How do you deploy your project?**
- Build the project using `mvn clean install`.
- Deploy the generated `.jar` or `.war` file to a server (Tomcat, cloud platform like AWS, or Kubernetes).
- Use CI/CD pipelines for continuous deployment.

---

### 14. **How do you develop code using a Git repository?**
1. Clone the repository using `git clone`.
2. Create a new branch using `git checkout -b new-branch`.
3. Make changes and commit them using `git commit`.
4. Push the branch using `git push`.
5. Create a pull request to merge the changes.

---

### 15. **How do you handle the `application.properties` file in Spring Boot?**
The `application.properties` file is used for configuring your Spring Boot application, such as database configurations, server ports, and other environment-specific properties. You can access these properties using `@Value` or `@ConfigurationProperties` annotations.

---

### 16. **Which cloud are you using for deployment?**
I am using [AWS/Azure/GCP] for deployment, utilizing services like Elastic Beanstalk, EC2, or Kubernetes for application hosting.

---

### 17. **How do you communicate between two microservices?**
Microservices can communicate using:
- **REST APIs** (via HTTP requests).
- **Message brokers** like RabbitMQ, Kafka for asynchronous communication.
- **Feign clients** in Spring Boot for simplified HTTP client calls between services.
