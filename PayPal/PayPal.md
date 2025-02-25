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
coming soon
