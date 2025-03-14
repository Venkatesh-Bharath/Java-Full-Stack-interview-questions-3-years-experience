# Amazon Interview

## Online Coding Assessment (2 Questions)
---
## Technical L1 Interview (Coding)
1. **Validate an IP address without using any inbuilt methods efficiently**  

```java
public class IPAddressValidator {
    public static boolean isValidIP(String ip) {
        if (ip == null || ip.isEmpty()) return false;

        String[] parts = new String[4];
        int partIndex = 0, num = 0, count = 0;
        boolean hasNum = false;

        for (int i = 0; i < ip.length(); i++) {
            char c = ip.charAt(i);
            if (c >= '0' && c <= '9') {
                num = num * 10 + (c - '0');
                hasNum = true;
                if (num > 255) return false;
            } else if (c == '.') {
                if (!hasNum || partIndex >= 3) return false;
                parts[partIndex++] = String.valueOf(num);
                num = 0;
                hasNum = false;
                count++;
            } else {
                return false;
            }
        }

        if (partIndex != 3 || !hasNum) return false;
        return true;
    }

    public static void main(String[] args) {
        System.out.println(isValidIP("192.168.1.1")); // true
        System.out.println(isValidIP("256.100.100.100")); // false
        System.out.println(isValidIP("192.168.1.")); // false
    }
}
```
---
## Technical L2 Interview (Coding)
2. **Pacific Atlantic Water Flow** [Watch on YouTube](https://youtu.be/yH0DesUBuFo?si=M0pcOaAy8Rm4qluD)  
```java
class Solution {
    public List<List<Integer>> pacificAtlantic(int[][] heights) {
        List<List<Integer>> ansList=new ArrayList<>();
        int row=heights.length,col=heights[0].length;
        boolean pacific[][]=new boolean[row][col];
        boolean atlantic[][]=new boolean[row][col];
        for(int i=0;i<row;i++){
            dfs(i,0,heights,pacific,Integer.MIN_VALUE);
            dfs(i,col-1,heights,atlantic,Integer.MIN_VALUE);
        }
        for(int j=0;j<col;j++){
            dfs(0,j,heights,pacific,Integer.MIN_VALUE);
            dfs(row-1,j,heights,atlantic,Integer.MIN_VALUE);
        }
        for(int i=0;i<row;i++){
            for(int j=0;j<col;j++){
                if(pacific[i][j]&&atlantic[i][j]){
                    ansList.add(Arrays.asList(i,j));
                }
            }
        }
        return ansList;
    }
    void dfs(int i,int j,int[][] heights, boolean ocean[][],int height){
        if(i<0||j<0||i>=heights.length||j>=heights[0].length||ocean[i][j]||height>heights[i][j]){
            return;
        }
        ocean[i][j]=true;
        dfs(i+1,j,heights,ocean,heights[i][j]);
        dfs(i-1,j,heights,ocean,heights[i][j]);
        dfs(i,j+1,heights,ocean,heights[i][j]);
        dfs(i,j-1,heights,ocean,heights[i][j]);
    }
}
```
---
## Technical L3 Interview (System Design)

### **Chef Booking  -System Design**  
---

## **1. System Requirements**  

### **1.1 Functional Requirements**
- Users can **register** and log in.  
- Users can **search for chefs** based on availability, cuisine, and location.  
- Users can **book a chef** for a specific time slot.  
- Users can **cancel or reschedule bookings**.  
- Chefs can **accept or reject bookings**.  
- Notifications for booking confirmations, rejections, and reminders.  
- Admin dashboard for managing users, chefs, and bookings.  

### **1.2 Non-Functional Requirements**
- **Scalability** → Handle large bookings efficiently.  
- **Performance** → Optimize API responses and database queries.  
- **Reliability** → Ensure high availability and fault tolerance.  
- **Security** → Authentication, authorization, and data protection.  
- **Observability** → Logging, monitoring, and alerting.  

---

## **2. High-Level Architecture**  

### **2.1 Components**  
1. **Frontend** → React.js / Angular  
2. **Backend** → Spring Boot (Java)  
3. **Database** → PostgreSQL (Relational DB) + Redis (Caching)  
4. **Authentication** → JWT-based authentication  
5. **Messaging Queue** → Kafka / RabbitMQ for notifications  
6. **Caching** → Redis for faster lookup of chef availability  
7. **Storage** → AWS S3 / Firebase for chef images & documents  
8. **Load Balancer** → Nginx / AWS ALB for handling traffic  
9. **Microservices** (Optional for scalability) →  
   - User Service  
   - Chef Service  
   - Booking Service  
   - Notification Service  

---

## **3. Database Design**  

### **3.1 Database Schema (Relational - PostgreSQL)**  

#### **Users Table**
```sql
CREATE TABLE users (
    user_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    phone VARCHAR(15),
    created_at TIMESTAMP DEFAULT NOW()
);
```

#### **Chefs Table**
```sql
CREATE TABLE chefs (
    chef_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    specialty VARCHAR(100),
    experience INT,
    available_from TIME,
    available_to TIME,
    price_per_hour DECIMAL(10,2),
    location VARCHAR(255),
    created_at TIMESTAMP DEFAULT NOW()
);
```

#### **Bookings Table**
```sql
CREATE TABLE bookings (
    booking_id SERIAL PRIMARY KEY,
    user_id INT REFERENCES users(user_id),
    chef_id INT REFERENCES chefs(chef_id),
    booking_time TIMESTAMP NOT NULL,
    duration INT NOT NULL,
    status VARCHAR(20) CHECK (status IN ('BOOKED', 'CANCELLED', 'COMPLETED')),
    created_at TIMESTAMP DEFAULT NOW()
);
```

#### **Notifications Table**
```sql
CREATE TABLE notifications (
    notification_id SERIAL PRIMARY KEY,
    user_id INT REFERENCES users(user_id),
    message TEXT NOT NULL,
    status VARCHAR(20) CHECK (status IN ('SENT', 'PENDING')),
    created_at TIMESTAMP DEFAULT NOW()
);
```

---

## **4. API Design (RESTful Services)**  

### **4.1 Authentication API**
- `POST /auth/register` → Register new users  
- `POST /auth/login` → Authenticate user and return JWT token  

### **4.2 User API**
- `GET /users/{userId}` → Fetch user details  
- `PUT /users/{userId}` → Update user profile  

### **4.3 Chef API**
- `GET /chefs` → Get list of available chefs  
- `GET /chefs/{chefId}` → Get chef details  
- `POST /chefs` → Add a new chef (Admin Only)  
- `PUT /chefs/{chefId}` → Update chef details  

### **4.4 Booking API**
- `POST /bookings` → Create a new booking  
- `GET /bookings/{bookingId}` → Fetch booking details  
- `PUT /bookings/{bookingId}` → Reschedule booking  
- `DELETE /bookings/{bookingId}` → Cancel booking  

### **4.5 Notification API**
- `GET /notifications` → Fetch user notifications  
- `POST /notifications` → Send notifications  

---

## **5. Optimization Techniques**  

### **5.1 Caching (Redis)**
- Store chef availability in Redis to reduce database load.  
- Store frequently accessed user data (e.g., profile info) in Redis.  

### **5.2 Database Indexing**
- Add indexes on frequently queried columns like `email`, `booking_time`, and `chef_id`.  

```sql
CREATE INDEX idx_email ON users(email);
CREATE INDEX idx_booking_time ON bookings(booking_time);
CREATE INDEX idx_chef_id ON bookings(chef_id);
```

### **5.3 Load Balancing**
- Use **Nginx / AWS ALB** to distribute traffic among multiple backend instances.  

### **5.4 Background Jobs for Notifications**
- Use **Kafka / RabbitMQ** to process notifications asynchronously.  

### **5.5 Microservices Approach (Optional)**
- **User Service** → Handles user authentication and profile management.  
- **Chef Service** → Manages chef details and availability.  
- **Booking Service** → Handles booking and scheduling logic.  
- **Notification Service** → Sends emails, SMS, and push notifications.  

---

## **6. Security Measures**  

### **6.1 Authentication & Authorization**
- Use **JWT-based authentication** for securing APIs.  
- Implement **role-based access control (RBAC)** for user roles.  

### **6.2 Input Validation**
- Validate all API inputs using **Spring Boot validation**.  

### **6.3 Rate Limiting**
- Implement API rate limiting using **Spring Boot RateLimiter** to prevent abuse.  

### **6.4 Secure Data Storage**
- Encrypt sensitive data like passwords using **BCrypt hashing**.  

---

## **7. Deployment & DevOps**  

### **7.1 CI/CD Pipeline**
- **GitHub Actions / Jenkins** for automated testing and deployment.  
- **Docker** for containerized deployment.  
- **Kubernetes** for scalable microservices.  

### **7.2 Monitoring & Logging**
- Use **Prometheus + Grafana** for monitoring.  
- **ELK Stack (Elasticsearch, Logstash, Kibana)** for logging and alerting.  

### **7.3 Cloud Deployment**
- **AWS / GCP / Azure** for cloud hosting.  
- **S3 Storage** for storing chef images and documents.  

---

## **8. Tech Stack Summary**  

| **Component**       | **Technology**             |
|---------------------|--------------------------|
| Frontend           | React.js / Angular        |
| Backend           | Spring Boot (Java)        |
| Database           | PostgreSQL / MySQL        |
| Caching            | Redis                      |
| Queueing System    | Kafka / RabbitMQ          |
| Authentication     | JWT + OAuth2              |
| Storage           | AWS S3 / Firebase         |
| Monitoring        | Prometheus + Grafana      |
| Deployment        | Docker + Kubernetes       |

---

## **9. Conclusion**
- **Scalable:** Microservices architecture for high scalability.  
- **Efficient:** Optimized database queries and caching.  
- **Secure:** JWT-based authentication and role-based access control.  
- **Fault-Tolerant:** Background jobs for async processing.  
- **Cloud-Ready:** Deployable on AWS/GCP/Azure with containerization.  
