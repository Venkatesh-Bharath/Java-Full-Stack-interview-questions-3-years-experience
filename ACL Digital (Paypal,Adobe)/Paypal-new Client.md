# Techincal L1 

### Self-Introduction
Hello, my name is-----. I have 3 years of experience as a Java Full Stack Developer, specializing in Java, Spring Boot, Hibernate, Microservices, and ReactJS. I have worked on multiple projects, including customer registration services and banking applications, where I implemented secure transaction handling, API development, and front-end components. I am proficient in writing clean, testable code using JUnit, Mockito, and TDD principles. I am also experienced in deploying applications using cloud platforms. I am eager to leverage my skills to contribute to innovative solutions in my next role.

---

### Problem 1: Sorting an Array of {-1, 0, 1} in O(n) Time and O(1) Space
#### **Problem Statement:**
Given an array containing only three types of elements (`-1`, `0`, and `1`), sort it in O(n) time and O(1) space complexity.

#### **Example:**
**Input:** `[1, 0, -1, 0, 1]`
**Output:** `[-1, 0, 0, 1, 1]`

#### **Java Solution:**
```java
public class SortThreeElements {
    public static void sortArray(int[] arr) {
        int low = 0, mid = 0, high = arr.length - 1;
        while (mid <= high) {
            if (arr[mid] == -1) {
                swap(arr, low, mid);
                low++;
                mid++;
            } else if (arr[mid] == 0) {
                mid++;
            } else {
                swap(arr, mid, high);
                high--;
            }
        }
    }

    private static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }

    public static void main(String[] args) {
        int[] arr = {1, 0, -1, 0, 1};
        sortArray(arr);
        System.out.println(Arrays.toString(arr));
    }
}
```

---

### Problem 2: Quantitative Trading Firm Profit Calculation
#### **Problem Statement:**
A quantitative trading firm processes a list of events, each classified into one of four categories:

1. **BUY <stock> <quantity>**: Buy `<quantity>` shares of `<stock>` at market price.
2. **SELL <stock> <quantity>**: Sell `<quantity>` shares of `<stock>` at market price.
3. **CHANGE <stock> <price>**: Change market price of `<stock>` by `<price>` (can be positive or negative).
4. **QUERY**: Return the gross profit/loss from start to present.

#### **Example:**
**Input:**
```
["BUY googl 20", "BUY aapl 50", "CHANGE googl 6", "QUERY",
 "SELL aapl 10", "CHANGE aapl -2", "QUERY"]
```
**Output:**
```
[120, 40]
```

#### **Java Solution:**
```java
import java.io.*;
import java.util.*;


public class Solution {
    public static void main(String[] args) throws IOException {
        List<String> events = Arrays.asList(
            "BUY googl 20", "BUY aapl 50", "CHANGE googl 6", 
            "QUERY", "SELL aapl 10", "CHANGE aapl -2", "QUERY"
        );

        List<Long> result = Result.getNetProfit(events);
        for (Long value : result) {
            System.out.println(value);
        }
    }
}
class Result {
    public static List<Long> getNetProfit(List<String> events) {
        List<Long> ansList = new ArrayList<>();
        Map<String, Long> portfolio = new HashMap<>();
        long query = 0;

        for (String event : events) {
            String[] word = event.split(" ");
            String type = word[0];

            if (type.equals("QUERY")) {
                ansList.add(query);
            } else {
                String company = word[1];
                long unit = Long.parseLong(word[2]);

                switch (type) {
                    case "BUY":
                        portfolio.put(company, portfolio.getOrDefault(company, 0L) + unit);
                        break;
                    case "SELL":
                        portfolio.put(company, portfolio.getOrDefault(company, 0L) - unit);
                        break;
                    case "CHANGE":
                        if (portfolio.containsKey(company)) {
                            query += portfolio.get(company) * unit;
                        }
                        break;
                }
            }
        }
        return ansList;
    }
}
```

---

### Problem 3: Another Trading Firm Example
#### **Example:**
**Input:**
```
6
BUY stock2 2
BUY stock1 4
CHANGE stock2 -8
SELL stock1 2
BUY stock3 3
QUERY
```
**Output:**
```
-16
```

#### **Explanation:**
- The price of `stock2` dropped by `-8`, affecting overall profit calculations.
- Final profit/loss calculation after all events is `16`.


# Techincal L2

### Self-Introduction
Hello, my name is-----. I have 3 years of experience as a Java Full Stack Developer, specializing in Java, Spring Boot, Hibernate, Microservices, and ReactJS. I have worked on multiple projects, including customer registration services and banking applications, where I implemented secure transaction handling, API development, and front-end components. I am proficient in writing clean, testable code using JUnit, Mockito, and TDD principles. I am also experienced in deploying applications using cloud platforms. I am eager to leverage my skills to contribute to innovative solutions in my next role.

---
### **Question:**  
Find the minimum element in a rotated sorted array.  
A rotated sorted array is an array that was originally sorted in increasing order but then rotated at some pivot. Your task is to find the minimum element in the given array in O(log N) time complexity.  

#### **Example Input & Output:**  
##### **Example 1:**  
**Input:** `[100,105,110,90,95]`  
**Output:** `90`  

##### **Example 2:**  
**Input:** `[3,4,5,6,7,8,9,10,1,2]`  
**Output:** `1`  

##### **Example 3:**  
**Input:** `[1,2,3,4,5,6,7,8,9,10]`  
**Output:** `1`  

##### **Example 4:**  
**Input:** `[5,4,3,2,1]`  
**Output:** `1`  

---

### **Java Code Solution:**  

```java
public class RotatedSortedArray {
    public static int findMin(int[] nums) {
        int left = 0, right = nums.length - 1;
        
        while (left < right) {
            int mid = left + (right - left) / 2;
            
            if (nums[mid] > nums[right]) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        return nums[left];
    }

    public static void main(String[] args) {
        int[][] testCases = {
            {100, 105, 110, 90, 95},
            {3, 4, 5, 6, 7, 8, 9, 10, 1, 2},
            {1, 2, 3, 4, 5, 6, 7, 8, 9, 10},
            {5, 4, 3, 2, 1}
        };

        for (int[] testCase : testCases) {
            System.out.println("Minimum Element: " + findMin(testCase));
        }
    }
}
```

### **Time Complexity:**  
- The solution uses **binary search**, making it **O(log N)**.  
