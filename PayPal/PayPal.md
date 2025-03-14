### **HackerRank Coding Assessment - PayPal**  
1. **Java.Inventory Clearance Sale**  
2. **Item Purchase**  
3. **Minimum Total Weight**  

---

### **PayPal Technical L1 Interview - Coding Questions**  

#### **1. Find the longest substring with non-repeating characters**  
**Question:**  
Write a function that takes a string and returns the longest substring that contains only unique (non-repeating) characters.  

**Example Input & Output:**  
**Input:** `"abcabcbb"`  
**Output:** `3` (`"abc"`)  

**Input:** `"bbbbb"`  
**Output:** `1` (`"b"`)  

**Input:** `"pwwkew"`  
**Output:** `3` (`"wke"`)  

**Java Code:**  
```java
import java.util.HashSet;

public class LongestSubstring {
    public static int lengthOfLongestSubstring(String s) {
        int left = 0, right = 0, maxLength = 0;
        HashSet<Character> set = new HashSet<>();

        while (right < s.length()) {
            if (!set.contains(s.charAt(right))) {
                set.add(s.charAt(right));
                maxLength = Math.max(maxLength, right - left + 1);
                right++;
            } else {
                set.remove(s.charAt(left));
                left++;
            }
        }
        return maxLength;
    }

    public static void main(String[] args) {
        System.out.println(lengthOfLongestSubstring("abcabcbb")); // Output: 3
        System.out.println(lengthOfLongestSubstring("bbbbb"));    // Output: 1
        System.out.println(lengthOfLongestSubstring("pwwkew"));   // Output: 3
    }
}
```

---

#### **2. Find the maximum water trapped between bars**  
**Question:**  
Given an array where each element represents the height of a bar, find the maximum amount of water that can be trapped between the bars after rainfall.  

**Example Input & Output:**  
**Input:** `[0,1,0,2,1,0,1,3,2,1,2,1]`  
**Output:** `6`  

**Input:** `[4,2,0,3,2,5]`  
**Output:** `9`  

**Java Code:**  
```java
public class TrappingRainWater {
    public static int trap(int[] height) {
        if (height == null || height.length == 0) return 0;

        int left = 0, right = height.length - 1;
        int leftMax = 0, rightMax = 0, trappedWater = 0;

        while (left < right) {
            if (height[left] < height[right]) {
                if (height[left] >= leftMax) {
                    leftMax = height[left];
                } else {
                    trappedWater += (leftMax - height[left]);
                }
                left++;
            } else {
                if (height[right] >= rightMax) {
                    rightMax = height[right];
                } else {
                    trappedWater += (rightMax - height[right]);
                }
                right--;
            }
        }
        return trappedWater;
    }

    public static void main(String[] args) {
        System.out.println(trap(new int[]{0,1,0,2,1,0,1,3,2,1,2,1})); // Output: 6
        System.out.println(trap(new int[]{4,2,0,3,2,5})); // Output: 9
    }
}
```

---
### **PayPal Technical L2 Interview - Coding Questions**  

### **Peer-to-Peer Payment System Design**  
We will design two APIs:  
1. **Send Payment API** – Allows a user to send money to another user.  
2. **Request Payment API** – Allows a user to request money from another user.  

### **Design Considerations**  
- Each user will have a **User ID** and **Balance**.  
- Sending money requires checking the sender’s balance.  
- Requesting money creates a pending request.  

---

### **Implementation Plan**  
1. **User Class**: Represents a user with an ID and balance.  
2. **Transaction Class**: Represents payment transactions.  
3. **PaymentService Class**: Implements send and request payment logic.  
4. **Main Class**: Demonstrates API usage.  

---

### **Java Implementation**  

```java
import java.util.*;

class User {
    private String userId;
    private double balance;

    public User(String userId, double balance) {
        this.userId = userId;
        this.balance = balance;
    }

    public String getUserId() {
        return userId;
    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }
}

class Transaction {
    private String senderId;
    private String receiverId;
    private double amount;
    private String status; // "COMPLETED" or "FAILED"

    public Transaction(String senderId, String receiverId, double amount, String status) {
        this.senderId = senderId;
        this.receiverId = receiverId;
        this.amount = amount;
        this.status = status;
    }

    public String toString() {
        return "Transaction: " + senderId + " -> " + receiverId + " | Amount: " + amount + " | Status: " + status;
    }
}

class PaymentService {
    private Map<String, User> users = new HashMap<>();
    private List<Transaction> transactions = new ArrayList<>();
    private List<String> paymentRequests = new ArrayList<>();

    public void addUser(String userId, double balance) {
        users.put(userId, new User(userId, balance));
    }

    public String sendPayment(String senderId, String receiverId, double amount) {
        if (!users.containsKey(senderId) || !users.containsKey(receiverId)) {
            return "Invalid user IDs";
        }

        User sender = users.get(senderId);
        User receiver = users.get(receiverId);

        if (sender.getBalance() < amount) {
            transactions.add(new Transaction(senderId, receiverId, amount, "FAILED"));
            return "Insufficient balance";
        }

        sender.setBalance(sender.getBalance() - amount);
        receiver.setBalance(receiver.getBalance() + amount);
        transactions.add(new Transaction(senderId, receiverId, amount, "COMPLETED"));

        return "Payment Successful";
    }

    public String requestPayment(String requesterId, String payerId, double amount) {
        if (!users.containsKey(requesterId) || !users.containsKey(payerId)) {
            return "Invalid user IDs";
        }

        String request = "Request from " + requesterId + " to " + payerId + " for amount " + amount;
        paymentRequests.add(request);
        return "Payment Request Sent";
    }

    public void printTransactions() {
        transactions.forEach(System.out::println);
    }

    public void printRequests() {
        paymentRequests.forEach(System.out::println);
    }
}

public class PeerToPeerPayment {
    public static void main(String[] args) {
        PaymentService service = new PaymentService();

        service.addUser("user1", 1000);
        service.addUser("user2", 500);

        System.out.println(service.sendPayment("user1", "user2", 200));
        System.out.println(service.requestPayment("user2", "user1", 150));

        service.printTransactions();
        service.printRequests();
    }
}
```

---

### **Explanation**  
1. **User Class**: Holds user ID and balance.  
2. **Transaction Class**: Stores transaction details.  
3. **PaymentService Class**:  
   - **sendPayment()**: Checks balance and transfers money.  
   - **requestPayment()**: Adds a payment request.  
4. **Main Class**: Demonstrates functionality.  

---
### **PayPal Technical L3 Interview - Coding Questions**  

```java
import java.util.EnumMap;
import java.util.Map;

// Enum for Furniture with cost
enum Furniture {
    CHAIR(1500), FAN(2000), BED(5000);
    
    private final int cost;
    
    Furniture(int cost) {
        this.cost = cost;
    }
    
    public int getCost() {
        return cost;
    }
}

// Furniture Order Class
class FurnitureOrder {
    private final Map<Furniture, Integer> orders = new EnumMap<>(Furniture.class);

    // Add order
    public void addOrder(Furniture furniture, int quantity) {
        orders.put(furniture, orders.getOrDefault(furniture, 0) + quantity);
    }

    // Get all orders
    public Map<Furniture, Integer> getAllOrders() {
        return new EnumMap<>(orders);
    }

    // Get total furniture count
    public int getTotalFurnitureCount() {
        return orders.values().stream().mapToInt(Integer::intValue).sum();
    }

    // Get specific furniture count
    public int getFurnitureCount(Furniture furniture) {
        return orders.getOrDefault(furniture, 0);
    }

    // Get total cost of all orders
    public int getTotalOrderCost() {
        return orders.entrySet().stream().mapToInt(e -> e.getKey().getCost() * e.getValue()).sum();
    }

    // Get cost of specific furniture type
    public int getFurnitureTypeCost(Furniture furniture) {
        return getFurnitureCount(furniture) * furniture.getCost();
    }
}

// JUnit Test Cases
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;

class FurnitureOrderTest {
    private FurnitureOrder order;

    @BeforeEach
    void setUp() {
        order = new FurnitureOrder();
    }

    @Test
    void testAddOrder() {
        order.addOrder(Furniture.CHAIR, 2);
        assertEquals(2, order.getFurnitureCount(Furniture.CHAIR));
    }

    @Test
    void testGetAllOrders() {
        order.addOrder(Furniture.FAN, 1);
        assertTrue(order.getAllOrders().containsKey(Furniture.FAN));
    }

    @Test
    void testGetTotalFurnitureCount() {
        order.addOrder(Furniture.BED, 2);
        order.addOrder(Furniture.CHAIR, 3);
        assertEquals(5, order.getTotalFurnitureCount());
    }

    @Test
    void testGetFurnitureCount() {
        order.addOrder(Furniture.FAN, 4);
        assertEquals(4, order.getFurnitureCount(Furniture.FAN));
    }

    @Test
    void testGetTotalOrderCost() {
        order.addOrder(Furniture.CHAIR, 2);
        order.addOrder(Furniture.BED, 1);
        assertEquals(8000, order.getTotalOrderCost());
    }

    @Test
    void testGetFurnitureTypeCost() {
        order.addOrder(Furniture.FAN, 3);
        assertEquals(6000, order.getFurnitureTypeCost(Furniture.FAN));
    }

    @Test
    void testEmptyOrderCost() {
        assertEquals(0, order.getTotalOrderCost());
    }
}
```
