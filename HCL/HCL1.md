# HCL L1 

1. **Brief about the project:**
   - The project is focused on developing a distributed banking application that handles real-time transactions using microservices architecture. It includes features like customer registration, account management, and secure transaction processing. Technologies like Spring Boot, Kafka, Docker, and React are used, ensuring high scalability and reliability.

2. **Explain Kafka architecture:**
   - Kafka architecture consists of Producers, Consumers, Brokers, Topics, and Zookeeper. Producers send data to Kafka topics, while Consumers read data from these topics. Kafka Brokers manage the storage and retrieval of messages, and Zookeeper handles metadata, including leader election and partition management, ensuring Kafka's fault tolerance and distributed nature.

3. **What is Jenkins and how do you use it?**
   - Jenkins is an open-source automation server used for continuous integration and continuous delivery (CI/CD). It automates the build, test, and deployment processes, enabling faster and more reliable software delivery. I use Jenkins to trigger automated builds on code commits, run tests, and deploy applications to different environments.

4. **What are the features of Java 17?**
   - Java 17 includes several new features such as sealed classes, pattern matching for switch (preview), new macOS rendering pipeline, enhanced pseudo-random number generators, and the removal of the experimental AOT and JIT compilers. It also includes long-term support (LTS) for stability in enterprise applications.

5. **What are the features of Java 8?**
   - Java 8 introduced several major features, including Lambda expressions, the Stream API for functional-style operations on collections, the new Date and Time API (java.time), default methods in interfaces, and the Optional class to handle null values more gracefully.

6. **Create a single thread in Java using different approaches (code):**
   ```java
   // Using Thread class
   Thread thread1 = new Thread() {
       public void run() {
           System.out.println("Thread using Thread class");
       }
   };
   thread1.start();

   // Using Runnable interface
   Runnable runnable = () -> System.out.println("Thread using Runnable interface");
   Thread thread2 = new Thread(runnable);
   thread2.start();

   // Using ExecutorService
   ExecutorService executor = Executors.newSingleThreadExecutor();
   executor.submit(() -> System.out.println("Thread using ExecutorService"));
   executor.shutdown();
   ```

7. **Create a text input and password input in React and display them when a button is clicked using functional components:**
   ```javascript
   import React, { useState } from 'react';

   function App() {
       const [text, setText] = useState('');
       const [password, setPassword] = useState('');
       const [show, setShow] = useState(false);

       const handleClick = () => {
           setShow(true);
       };

       return (
           <div>
               <input 
                   type="text" 
                   placeholder="Enter text" 
                   value={text} 
                   onChange={(e) => setText(e.target.value)} 
               />
               <input 
                   type="password" 
                   placeholder="Enter password" 
                   value={password} 
                   onChange={(e) => setPassword(e.target.value)} 
               />
               <button onClick={handleClick}>Show</button>
               {show && (
                   <div>
                       <p>Text: {text}</p>
                       <p>Password: {password}</p>
                   </div>
               )}
           </div>
       );
   }

   export default App;
   ```

8. **Explain your weekly tasks:**
   - My weekly tasks typically involve developing new features, fixing bugs, and optimizing existing code for better performance. I collaborate with team members in daily stand-up meetings, work on writing unit and integration tests, and participate in code reviews. Additionally, I contribute to the continuous integration pipeline and ensure smooth deployments.

9. **What is Agile methodology?**
   - Agile methodology is an iterative approach to software development and project management. It emphasizes collaboration, flexibility, and customer feedback, allowing teams to deliver small, functional pieces of software incrementally. Agile promotes adaptive planning, evolutionary development, early delivery, and continuous improvement.

10. **What is Jira and how do you use it?**
    - Jira is a project management tool used for tracking tasks, bugs, and issues. It supports Agile methodologies like Scrum and Kanban. I use Jira to manage and prioritize tasks, track progress through sprints, create and assign issues, and document project workflows. Jira also integrates with CI/CD pipelines for automated updates.
