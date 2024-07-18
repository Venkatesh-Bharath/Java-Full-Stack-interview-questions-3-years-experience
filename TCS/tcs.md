### 1. Can you briefly introduce yourself?
------*****------
### 2. Can you give a brief explanation about your projects?
------******-----
### 3. What are the common error status codes?
- **400 Bad Request**: The server could not understand the request due to invalid syntax.
- **401 Unauthorized**: The client must authenticate itself to get the requested response.
- **403 Forbidden**: The client does not have access rights to the content.
- **404 Not Found**: The server can not find the requested resource.
- **500 Internal Server Error**: The server has encountered a situation it doesn't know how to handle.

### 4. What are the new features in Java 8?
- **Lambda Expressions**: Introduce a new syntax and way to pass behavior as a parameter.
- **Functional Interfaces**: Interfaces with a single abstract method.
- **Stream API**: For processing sequences of elements.
- **Optional**: A container object which may or may not contain a value.
- **New Date and Time API**: For improved date and time manipulation.
- **Default Methods**: Allow methods in interfaces to have implementations.

### 5. What is the String pool in Java?
The String pool is a special storage area in the Java heap where String literals are stored. It helps in saving memory and improving performance by reusing instances of String literals.

### 6. What is a marker interface and what are some inbuilt marker interfaces in Java?
A marker interface is an interface with no methods or fields, used to signal to the JVM or compiler some special behavior. Examples include:
- **Serializable**: Indicates that a class can be serialized.
- **Cloneable**: Indicates that a class can be cloned.
- **Remote**: Indicates that a class can be used in RMI (Remote Method Invocation).

### 7. What is an HTTP POST method?
The HTTP POST method is used to send data to the server to create a resource. The data sent to the server with POST is stored in the request body of the HTTP request.

### 8. What is the difference between POST and GET methods?
- **GET**: Requests data from a specified resource, and the data is sent in the URL.
- **POST**: Submits data to be processed to a specified resource, and the data is sent in the request body.

### 9. Can you use a try block without a catch block?
Yes, a try block can be used without a catch block if it is followed by a finally block. The finally block will execute regardless of whether an exception occurs or not.

### 10. How do you use try with multiple catch blocks?
```java
try {
    // code that may throw exceptions
} catch (IOException e) {
    // handle IOException
} catch (SQLException e) {
    // handle SQLException
} finally {
    // cleanup code
}
```
This allows handling different types of exceptions separately.

### 11. What is try with resources?
Try with resources is a feature in Java that allows you to declare resources to be closed automatically after the try block. It is used for managing resources such as streams, files, etc.
```java
try (BufferedReader br = new BufferedReader(new FileReader("file.txt"))) {
    // use br
} catch (IOException e) {
    // handle IOException
}
```

### 12. How do you connect multiple databases in Spring Boot?
You can configure multiple data sources in Spring Boot by defining multiple `DataSource` beans and using `@Primary` to specify the default data source. You also need to configure multiple `EntityManagerFactory` and `TransactionManager` beans for different data sources.

### 13. What is the difference between 400 and 403 status codes?
- **400 Bad Request**: Indicates that the server cannot process the request due to client error (e.g., malformed request syntax).
- **403 Forbidden**: Indicates that the client’s request is valid, but the server is refusing action. The client does not have the necessary permissions.

### 14. How do you create a singleton class in Java?
```java
public class Singleton {
    private static Singleton instance;

    private Singleton() {
        // private constructor
    }

    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```
