
---

### **1. What is a hash collision?**
- **Answer:** A hash collision occurs when two different keys in a hash-based collection, such as a `HashMap`, produce the same hash code and thus are placed in the same bucket. This can lead to performance degradation as multiple keys have to be stored and managed in the same location.

### **2. When does a collision error occur in hash-based collections?**
- **Answer:** A collision error occurs in hash-based collections when multiple keys are mapped to the same hash code, causing them to be stored in the same bucket. This results in a need for the collection to handle the collision, usually through chaining (linked list) or open addressing (probing).

### **3. What are the key differences between `Runnable` and `Callable` in Java?**
- **Answer:** 
  - **`Runnable`:** Does not return a result and cannot throw a checked exception.
  - **`Callable`:** Returns a result (`T`) and can throw checked exceptions.
  - `Runnable` is executed by `Thread` or `Executor`, while `Callable` is executed by `ExecutorService`.

### **4. What is the difference between `map` and `flatMap` in Java Streams?**
- **Answer:** 
  - **`map`:** Transforms each element in the stream into another form, producing a stream of the same structure.
  - **`flatMap`:** Flattens multiple streams into a single stream by applying a one-to-many transformation function to each element and then flattening the resulting streams into one.

### **5. How does `flatMap` work internally?**
- **Answer:** Internally, `flatMap` applies a function that returns a stream for each element of the original stream. It then flattens these streams into a single stream, effectively concatenating them. This is achieved through a combination of the `map` operation and the `Stream.flatMap` method, which merges the nested streams.

---

### **6. Find and Insert Target in a Sorted Array:**

- **Question:** You are given an unsorted array of integers. You need to find the index of a target value within this array. If the target value is not present in the array, insert it into the array such that the array remains sorted after insertion, and return the index where the target value would be if it were inserted.

**Example:**
- **Input 1:**
  - Array: `[4, 1, 7, 2]`
  - Target: `4`
  - **Output:** `0`
- **Input 2:**
  - Array: `[4, 1, 7, 2]`
  - Target: `5`
  - **Output:** `3` (because the array becomes `[1, 2, 4, 5, 7]` and `5` is at index `3`)

- **Answer (Java Code):**
```java
import java.util.Arrays;

public class InsertAndFindIndex {
    public static int insertAndFindIndex(int[] arr, int target) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == target) {
                return i;
            }
        }
        Arrays.sort(arr);
        int index = Arrays.binarySearch(arr, target);
        if (index >= 0) {
            return index;
        }
        return -(index + 1);
    }

    public static void main(String[] args) {
        int[] arr1 = {4, 1, 7, 2};
        int target1 = 4;
        System.out.println(insertAndFindIndex(arr1, target1)); // Output: 0

        int[] arr2 = {4, 1, 7, 2};
        int target2 = 5;
        System.out.println(insertAndFindIndex(arr2, target2)); // Output: 3
    }
}
```

---

### **7. Capitalize and Count Words in a List Using Streams:**

- **Question:** You are given a list of lowercase strings. Write a Java program that:
  - Capitalizes the first letter of each word.
  - Counts the occurrences of each word after capitalization.

**Example:**
- **Input:**
  - List: `["hello", "world", "this", "hello"]`
- **Output:**
  - Capitalized List: `["Hello", "World", "This", "Hello"]`
  - Word Counts:
    - `Hello`: 2
    - `World`: 1
    - `This`: 1

- **Answer (Java Code):**
```java
import java.util.*;
import java.util.function.Function;
import java.util.stream.Collectors;

public class CapitalizeWords {
    public static void main(String[] args) {
        List<String> words = Arrays.asList("hello", "world", "this", "hello");

        List<String> capitalizedWords = words.stream()
            .map(word -> word.isEmpty() ? word : Character.toUpperCase(word.charAt(0)) + word.substring(1))
            .collect(Collectors.toList());

        System.out.println("Capitalized List: " + capitalizedWords);

        Map<String, Long> wordCounts = words.stream()
            .map(word -> word.isEmpty() ? word : Character.toUpperCase(word.charAt(0)) + word.substring(1))
            .collect(Collectors.groupingBy(Function.identity(), Collectors.counting()));

        wordCounts.forEach((word, count) -> System.out.println(word + ": " + count));
    }
}
```
