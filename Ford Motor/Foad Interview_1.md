
# Ford Interview
## Java/Spring Boot
### 1. Explain CSR (Cross-Site Request) and how you handle it in your applications.

Cross-Site Request Forgery (CSRF) is an attack that tricks the victim into submitting a malicious request. It exploits the trust a site has in the user's browser. To handle CSRF in Spring Boot, you can use the CSRF protection provided by Spring Security. By default, CSRF protection is enabled in Spring Security.

```java
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;

public class SecurityConfig extends WebSecurityConfigurerAdapter {
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .csrf().csrfTokenRepository(CookieCsrfTokenRepository.withHttpOnlyFalse())
            .and()
            .authorizeRequests()
            .anyRequest().authenticated();
    }
}
```

### 2. What is JWT Security, and how do you implement it?

JWT (JSON Web Token) Security is a method for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair (using RSA or ECDSA).
Implementing JWT Security in Spring Boot
#### To implement JWT security in a Spring Boot application, you typically follow these steps:
**Add Dependencies:** Include necessary dependencies for Spring Security and JWT in your project. These can be added in the pom.xml file for Maven projects or build.gradle for Gradle projects.

**Configure Spring Security:** Configure Spring Security to intercept requests and ensure only authenticated users can access certain endpoints. This involves setting up a security configuration class.

**Create JWT Utility Class:** This class will handle JWT creation, validation, and parsing. It includes methods to generate tokens, extract claims, and validate tokens.

**Create Authentication Filter:** Implement a filter that intercepts incoming requests and checks for a valid JWT in the Authorization header. This filter will use the JWT utility class to validate the token and set the authentication context.

**User Authentication and Authorization:** Implement user authentication by overriding the UserDetailsService to load user-specific data. Use the AuthenticationManager to authenticate users and generate a JWT for authenticated users.


### 3. Describe OAuth2 and how it is used in your applications.

OAuth2 (Open Authorization) is an authorization framework that allows applications to obtain limited access to user accounts on an HTTP service, such as Facebook, GitHub, or Google. It works by delegating user authentication to the service that hosts the user account and authorizing third-party applications to access the user account.

### 4. How do you implement paging to get data in Spring Boot?

You can use Spring Data JPA’s `Pageable` interface to implement paging.

```java
import org.springframework.data.domain.Page;
import org.springframework.data.domain.Pageable;

public interface UserRepository extends JpaRepository<User, Long> {
    Page<User> findAll(Pageable pageable);
}

// Service
public Page<User> getUsers(Pageable pageable) {
    return userRepository.findAll(pageable);
}

// Controller
@GetMapping("/users")
public Page<User> listUsers(Pageable pageable) {
    return userService.getUsers(pageable);
}
```

### 5. How do you sort data based on a property in Spring Boot?

You can use Spring Data JPA’s `Sort` class to sort data.

```java
import org.springframework.data.domain.Sort;

public List<User> getUsers() {
    return userRepository.findAll(Sort.by(Sort.Direction.ASC, "name"));
}
```

### 6. What is an API Gateway, and why is it used?

An API Gateway is a server that acts as an API front-end, receiving API requests, enforcing throttling and security policies, passing requests to the back-end service, and then passing the response back to the requester. It is used to manage traffic, handle cross-cutting concerns like security, and provide a single entry point for client requests.

### 7. How do you implement load balancing in your applications?

You can implement load balancing using tools like Ribbon or Spring Cloud LoadBalancer in a Spring Boot application.

```java
import org.springframework.cloud.client.loadbalancer.LoadBalanced;
import org.springframework.context.annotation.Bean;
import org.springframework.web.client.RestTemplate;

@Bean
@LoadBalanced
public RestTemplate restTemplate() {
    return new RestTemplate();
}
```

### 8. Explain the difference between Monolithic and Microservices architectures.

- **Monolithic Architecture:** A single unified codebase where all the components and services are tightly coupled and run as a single service.
- **Microservices Architecture:** An approach where an application is composed of loosely coupled services, each running in its own process and communicating through lightweight mechanisms like HTTP or messaging queues.

### 9. What is Kubernetes, and how do you use it in your applications?

Kubernetes is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications. You can use it to deploy, manage, and scale your microservices.

### 10. How do you connect one microservice to another?

You can use REST APIs, messaging queues (like RabbitMQ), or service discovery tools (like Eureka) to connect microservices.

### 11. What is the difference between @RestController and @Controller in Spring Boot?

- **@RestController:** Combines @Controller and @ResponseBody, used to create RESTful web services.
- **@Controller:** Used to define a controller and is typically used with view templates to render HTML.

### 12. How do you perform code quality analysis in your projects?

You can use tools like SonarQube for static code analysis, which helps in identifying code smells, bugs, and security vulnerabilities.

### 13. What is the difference between authentication and authorization?

- **Authentication:** The process of verifying the identity of a user.
- **Authorization:** The process of verifying what resources an authenticated user has access to.

### 14. How do you scale your application?

You can scale your application horizontally by adding more instances or vertically by adding more resources (CPU, memory) to the existing instances. Tools like Kubernetes help in managing scaling.

### 15. What are profiles in Spring Boot, and how do you use them?

Profiles in Spring Boot allow you to configure different environments (e.g., development, testing, production). You can specify different configurations in `application-{profile}.properties` files.

```java
// application-dev.properties
spring.datasource.url=jdbc:h2:mem:devdb

// application-prod.properties
spring.datasource.url=jdbc:mysql://localhost/proddb

// Main application
@SpringBootApplication
@PropertySource("classpath:application-${spring.profiles.active}.properties")
public class MyApp {
    public static void main(String[] args) {
        SpringApplication.run(MyApp.class, args);
    }
}
```

## React

### 1. What is middleware in ReactJS, and how do you use it?

Middleware in React, typically used with state management libraries like Redux, is a way to extend the capabilities of the store by adding custom functionality between dispatching an action and the moment it reaches the reducer.

```javascript
const loggerMiddleware = store => next => action => {
    console.log('Dispatching:', action);
    let result = next(action);
    console.log('Next state:', store.getState());
    return result;
};

const store = createStore(
    rootReducer,
    applyMiddleware(loggerMiddleware)
);
```

### 2. Explain the Context API and Redux. How do they differ, and when do you use each?

- **Context API:** Built-in feature of React for prop drilling and global state management. Best for small to medium applications.
- **Redux:** A state management library that provides a single source of truth and a predictable state container. Best for larger applications with more complex state management needs.

### 3. How do you write unit tests in React?

You can use testing libraries like Jest and React Testing Library to write unit tests.

```javascript
import { render, screen } from '@testing-library/react';
import App from './App';

test('renders learn react link', () => {
    render(<App />);
    const linkElement = screen.getByText(/learn react/i);
    expect(linkElement).toBeInTheDocument();
});
```

### 4. Have you worked on reusable components in React? Give an example.

Yes, for example, a Button component that can be reused across the application.

```javascript
const Button = ({ label, onClick }) => (
    <button onClick={onClick}>
        {label}
    </button>
);

// Usage
<Button label="Click Me" onClick={handleClick} />
```

### 5. What is a Higher-Order Component (HoC) in ReactJS, and how do you use it?

A Higher-Order Component (HoC) is a function that takes a component and returns a new component. It’s used for reusing component logic.

```javascript
const withLogging = WrappedComponent => {
    return class extends React.Component {
        componentDidMount() {
            console.log('Component mounted');
        }

        render() {
            return <WrappedComponent {...this.props} />;
        }
    };
};

// Usage
const EnhancedComponent = withLogging(MyComponent);
```
