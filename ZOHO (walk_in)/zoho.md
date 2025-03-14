
---

# **Zoho Interview:**

## **1st Round: Factorial Sum (Avoiding Repeated Calculations)**
#### **Question:**  
Given a number, find the sum of the factorials of its digits without recalculating previously computed factorials.

#### **Example:**  
**Input:** `145`  
**Output:** `1! + 4! + 5! = 1 + 24 + 120 = 145`

#### **Optimized Java Solution:**
```java
import java.util.HashMap;
import java.util.Map;

public class FactorialSum {
    private static final Map<Integer, Integer> factorialCache = new HashMap<>();

    public static void main(String[] args) {
        int num = 145;
        System.out.println("Factorial Sum: " + factorialSum(num));
    }

    public static int factorialSum(int num) {
        int sum = 0;
        while (num > 0) {
            int digit = num % 10;
            sum += factorial(digit);
            num /= 10;
        }
        return sum;
    }

    private static int factorial(int n) {
        if (!factorialCache.containsKey(n)) {
            factorialCache.put(n, (n == 0 || n == 1) ? 1 : n * factorial(n - 1));
        }
        return factorialCache.get(n);
    }
}
```
✅ **Avoids recalculating factorial using a HashMap.**

---

## **2nd Round: Character Occurrence Sorting**
#### **Question:**  
Given a string, count the occurrences of each character and sort by frequency in descending order.

#### **Example:**  
**Input:** `"zoho"`  
**Output:** `"o:2, z:1, h:1"`

#### **Optimized Java Solution:**
```java
import java.util.*;
import java.util.stream.Collectors;

public class CharacterFrequencySort {
    public static void main(String[] args) {
        String input = "zoho";
        System.out.println(sortByFrequency(input));
    }

    public static String sortByFrequency(String s) {
        Map<Character, Long> frequencyMap = s.chars()
                .mapToObj(c -> (char) c)
                .collect(Collectors.groupingBy(c -> c, Collectors.counting()));

        return frequencyMap.entrySet().stream()
                .sorted((a, b) -> Long.compare(b.getValue(), a.getValue()))  // Sort by frequency descending
                .map(e -> e.getKey() + ":" + e.getValue())
                .collect(Collectors.joining(", "));
    }
}
```
✅ **Uses Java Streams for efficient sorting and counting.**

---

## **3rd Round: Matrix Rotation Validation**
#### **Question:**  
Check if a given matrix is a rotated version of itself.

#### **Example:**  
**Valid Rotation:**  
```text
[
 [1,2,3]
 [3,1,2]
 [2,3,1]
]
```
**Invalid Rotation:**  
```text
[
 [1,2,3]
 [3,1,2]
 [1,2,3]
]
```

#### **Optimized Java Solution:**
```java
import java.util.Arrays;

public class MatrixRotation {
    public static void main(String[] args) {
        int[][] matrix1 = {
                {1, 2, 3},
                {3, 1, 2},
                {2, 3, 1}
        };

        int[][] matrix2 = {
                {1, 2, 3},
                {3, 1, 2},
                {1, 2, 3}
        };

        System.out.println(isRotatedMatrix(matrix1)); // true
        System.out.println(isRotatedMatrix(matrix2)); // false
    }

    public static boolean isRotatedMatrix(int[][] matrix) {
        int n = matrix.length;
        for (int i = 1; i < n; i++) {
            if (!Arrays.equals(matrix[i], rotateRow(matrix[i - 1]))) {
                return false;
            }
        }
        return true;
    }

    private static int[] rotateRow(int[] row) {
        int n = row.length;
        int[] rotated = new int[n];
        System.arraycopy(row, 1, rotated, 0, n - 1);
        rotated[n - 1] = row[0];
        return rotated;
    }
}
```
✅ **Checks each row’s rotation efficiently.**

---

## **4th Round: Cipher Text Encryption**
#### **Question:**  
Encrypt a given string by shifting characters forward based on a given number.

#### **Example:**  
**Input:** `("zoho", 2)`  
**Output:** `"bqjq"`

---

### **Optimized Java Solution:**
```java
public class CipherText {
    public static void main(String[] args) {
        String input = "zoho";
        int shift = 2;
        System.out.println(encrypt(input, shift));
    }

    public static String encrypt(String text, int shift) {
        StringBuilder encrypted = new StringBuilder();

        for (char ch : text.toCharArray()) {
            if (Character.isLetter(ch)) {
                char base = Character.isUpperCase(ch) ? 'A' : 'a';
                encrypted.append((char) ((ch - base + shift) % 26 + base));
            } else {
                encrypted.append(ch);
            }
        }
        return encrypted.toString();
    }
}
```
---

## **5th Round: Zig-Zag String Transformation**
#### **Question:**  
Given a string and number of rows, convert it into a Zig-Zag pattern.

#### **Example:**  
**Input:** `"PAYPALISHIRING"`, `Rows = 3`  
**Output:** `"PAHNAPLSIIGYIR"`

#### **Optimized Java Solution:**
```java
public class ZigZagConversion {
    public static void main(String[] args) {
        String s = "PAYPALISHIRING";
        int numRows = 3;
        System.out.println(convertZigZag(s, numRows));
    }

    public static String convertZigZag(String s, int numRows) {
        if (numRows == 1) return s;

        StringBuilder[] rows = new StringBuilder[numRows];
        for (int i = 0; i < numRows; i++) {
            rows[i] = new StringBuilder();
        }

        int i = 0, step = 1;
        for (char c : s.toCharArray()) {
            rows[i].append(c);
            if (i == 0) step = 1;
            if (i == numRows - 1) step = -1;
            i += step;
        }

        return Arrays.stream(rows).map(StringBuilder::toString).collect(Collectors.joining());
    }
}
```
✅ **Uses an efficient approach with `StringBuilder` arrays.**

---

## **6th Round: Database Questions**

### **1. Full Stack Application Data Flow**
Explain data flow from frontend to backend and database.

### **2. SQL Queries for Employee Table**
Example:
```sql
SELECT * FROM employees WHERE department = 'HR';
```

### **3. Fetching Data from Multiple Tables**
**Example Using JOIN:**
```sql
SELECT e.name, d.department_name
FROM employees e
JOIN departments d ON e.department_id = d.id;
```

### **4. Primary Key vs Foreign Key**
- **Primary Key**: Unique identifier in a table.
- **Foreign Key**: References another table’s primary key.

### **5. Types of Joins with Example**
```sql
-- INNER JOIN
SELECT e.name, d.department_name
FROM employees e
INNER JOIN departments d ON e.department_id = d.id;

-- LEFT JOIN
SELECT e.name, d.department_name
FROM employees e
LEFT JOIN departments d ON e.department_id = d.id;
```

### **6. Subqueries vs Joins**
- **Joins** are used for merging tables.
- **Subqueries** are nested queries.

✅ **Database concepts covered efficiently.**

---
- **Expected Package** discussion.
- **How do you keep up with new technologies?**
- **College life & how you got your first job.**

