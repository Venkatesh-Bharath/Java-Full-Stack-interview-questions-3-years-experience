## Self Introduction and Project Details
1. **Self Introduction and Project Details:**
   - Briefly introduce yourself, mentioning your experience, key skills, and current role.
   - Briefly describe your current project, the technologies you are using, the version of Java and React you are using, and the testing frameworks in use.
   - Mention the version of Java (Java 8, familiar with Java 17) and React (React 16.8 or React 18).
## JavaScript and React Questions
2. **What are ES6 features in JavaScript?**
   - ES6 features include let and const, arrow functions, template literals, default parameters, rest and spread operators, destructuring assignment, classes, promises, modules, and enhanced object literals.

3. **Difference between `var` and `let`.**
   - `var` is function-scoped, while `let` is block-scoped. Variables declared with `let` are not hoisted to the top of their block, unlike `var`.

4. **What is object cloning in JavaScript?**
   - Object cloning is the process of creating a copy of an object with the same properties and values.

5. **Why do we need to clone an object?**
   - Cloning an object is needed to avoid mutating the original object, ensuring data integrity and avoiding side effects in the code.

6. **How to clone an object in JavaScript? Provide code.**
   ```javascript
   const original = { a: 1, b: 2 };
   const clone = { ...original }; // Shallow copy using spread operator
   ```

7. **Write a JavaScript function to count every character in a string and display it.**
   ```javascript
   function countCharacters(str) {
       const charCount = {};
       for (let char of str) {
           charCount[char] = charCount[char] ? charCount[char] + 1 : 1;
       }
       return charCount;
   }
   console.log(countCharacters("hello"));
   ```

8. **Which version of React are you using?**
   - I am using React 17.

9. **Are you using functional components or class components?**
   - I am primarily using functional components.

10. **What is `useRef` in React? Explain.**
    - `useRef` is a React hook that allows you to create a mutable object that persists for the lifetime of the component. It can be used to access DOM elements directly or to hold a mutable value that doesn’t trigger re-renders when changed.

11. **What is a common component in ReactJS?**
    - A common component is a reusable piece of UI that can be used across different parts of an application, like buttons, form inputs, or modal dialogs.

12. **Have you used reusable components in your project, like tables?**
    - Yes, I have created reusable components such as tables, buttons, and form inputs to maintain consistency and reduce code duplication.

13. **How do you get data from an API and display it in the UI in ReactJS? How do you handle errors? (Example: employee data with id, name, salary)**
    ```javascript
    import React, { useState, useEffect } from 'react';
    import axios from 'axios';

    const EmployeeList = () => {
        const [employees, setEmployees] = useState([]);
        const [error, setError] = useState(null);

        useEffect(() => {
            axios.get('/api/employees')
                .then(response => setEmployees(response.data))
                .catch(error => setError(error.message));
        }, []);

        if (error) {
            return <div>Error: {error}</div>;
        }

        return (
            <div>
                <ul>
                    {employees.map(emp => (
                        <li key={emp.id}>{emp.name} - ${emp.salary}</li>
                    ))}
                </ul>
            </div>
        );
    };

    export default EmployeeList;
    ```

14. **Are you using CSS in your project?**
    - Yes, I am using CSS for styling the components.

15. **Write code to change the color of text in a `div` or `span` when data is posted.**
    ```javascript
    import React, { useState } from 'react';

    const ChangeTextColor = () => {
        const [color, setColor] = useState('black');

        const handleSubmit = (e) => {
            e.preventDefault();
            setColor('blue');
        };

        return (
            <div>
                <form onSubmit={handleSubmit}>
                    <button type="submit">Post Data</button>
                </form>
                <div style={{ color: color }}>This text will change color when data is posted.</div>
            </div>
        );
    };

    export default ChangeTextColor;
    ```

## Java Questions
16. **Which version of Java are you using? (Java 8, familiar with Java 17)**
    - I am using Java 8 and familiar with Java 17.

17. **Write a custom exception in Java and use it.**
    ```java
    public class CustomException extends Exception {
        public CustomException(String message) {
            super(message);
        }
    }

    public class TestCustomException {
        public static void main(String[] args) {
            try {
                validateAge(15);
            } catch (CustomException e) {
                e.printStackTrace();
            }
        }

        static void validateAge(int age) throws CustomException {
            if (age < 18) {
                throw new CustomException("Age is not valid");
            }
        }
    }
    ```

18. **Implement a method in Java to check if a string is present in a list.**
    ```java
    import java.util.List;

    public class StringChecker {
        public static boolean isStringPresent(List<String> list, String str) {
            return list.contains(str);
        }
    }
    ```

19. **Write Java code to remove repeated strings from a list.**
    ```java
    import java.util.ArrayList;
    import java.util.HashSet;
    import java.util.List;
    import java.util.Set;

    public class RemoveDuplicates {
        public static List<String> removeDuplicates(List<String> list) {
            Set<String> set = new HashSet<>(list);
            return new ArrayList<>(set);
        }
    }
    ```

20. **How do you provide security in Spring Boot?**
    - Security in Spring Boot is provided through Spring Security, which offers authentication, authorization, and other security features. It can be configured using Java configuration and annotations.

21. **Explain how JWT token-based authentication works briefly.**
    - JWT token-based authentication works by generating a token after a user successfully logs in. This token is then sent with each subsequent request in the Authorization header. The server validates the token to authenticate the user.

22. **What is the use of the `@Transactional` annotation in Spring Data?**
    - The `@Transactional` annotation in Spring Data is used to manage transactions declaratively. It ensures that a method runs within a transaction and manages commit or rollback based on the method’s execution.

23. **Have you used threads in your project?**
    - Yes, I have used threads in my project to handle concurrent processing tasks like processing multiple requests simultaneously.

24. **How do you limit API calls in Spring Boot?**
    - API calls in Spring Boot can be limited using rate-limiting libraries like Bucket4j or implementing custom rate-limiting logic using interceptors.

25. **Have you created any custom annotations in Spring Boot?**
    - Yes, I have created custom annotations to encapsulate repetitive logic and apply cross-cutting concerns.

26. **Create a Age validation custom annotation.**
- Steps
1. **Create the Annotation Interface**
2. **Create the Validator Class**
3. **Apply the Custom Annotation**

#### 1. Create the Annotation Interface

First, create a custom annotation interface for DOB validation.

```java
import javax.validation.Constraint;
import javax.validation.Payload;
import java.lang.annotation.Documented;
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

@Documented
@Constraint(validatedBy = DOBValidator.class)
@Target({ ElementType.METHOD, ElementType.FIELD })
@Retention(RetentionPolicy.RUNTIME)
public @interface ValidDOB {
    String message() default "Invalid Date of Birth";
    Class<?>[] groups() default {};
    Class<? extends Payload>[] payload() default {};
}
```

#### 2. Create the Validator Class

Next, implement the validator class that will contain the logic for validating the DOB.

```java
import javax.validation.ConstraintValidator;
import javax.validation.ConstraintValidatorContext;
import java.time.LocalDate;

public class DOBValidator implements ConstraintValidator<ValidDOB, LocalDate> {

    @Override
    public void initialize(ValidDOB constraintAnnotation) {
        // Initialization code if necessary
    }

    @Override
    public boolean isValid(LocalDate dob, ConstraintValidatorContext context) {
        if (dob == null) {
            return false; // or true, based on whether null is considered valid
        }
        // Check if the DOB is in the past
        return dob.isBefore(LocalDate.now());
    }
}
```


27. **Have you used a logger in your Spring Boot project?**
    - Yes, I have used SLF4J with Logback for logging in my Spring Boot project.

28. **How can you see which controller API methods are running?**
    - You can see which controller API methods are running by enabling logging for HTTP requests in Spring Boot or using tools like Actuator to monitor endpoints.

29. **How do you create a Spring Boot project?**
    - A Spring Boot project can be created using Spring Initializr, which generates a project structure with the necessary dependencies and configurations.

30. **What does Spring Starter provide?**
    - Spring Starter provides pre-configured templates for specific functionalities like web, security, JPA, etc., making it easier to set up a Spring Boot project.

31. **Which dependencies do you commonly use in Spring Boot?**
    - Common dependencies include Spring Boot Starter Web, Spring Boot Starter Data JPA, Spring Boot Starter Security, and Spring Boot Starter Test.

32. **Which annotations do you use in Spring Boot?**
    - Common annotations include `@SpringBootApplication`, `@RestController`, `@RequestMapping`, `@Autowired`, `@Entity`, `@Repository`, and `@Service`.

33. **Which annotations do you use in JUnit tests?**
    - Common annotations include `@Test`, `@BeforeEach`, `@AfterEach`, `@Mock`, `@InjectMocks`, and `@RunWith`.

34. **Which libraries do you use for JUnit tests?**
    - Common libraries include JUnit 5, Mockito, and Spring Boot Test.
