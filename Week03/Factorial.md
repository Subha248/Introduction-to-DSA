

### **Program to Calculate Factorial of a Number**

**Question:**
Write a program to calculate the factorial of a given number \( n \).

**Testcase 1:**

Input:
```
n = 5
```

Output:
```
120
```

Explanation:
- The factorial of 5 is calculated as \( 5! = 5 \times 4 \times 3 \times 2 \times 1 = 120 \).

---

**Code:**

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        int n = 5; // Input number for factorial
        int fact = 1; // Variable to store factorial, initialized to 1
        
        // Loop to calculate factorial
        for (int i = 1; i <= n; i++) {
            fact = fact * i; // Multiply fact by current value of i
        }
        
        // Print the final factorial value
        System.out.println(fact);
    }
}
```

---

**Explanation of the Code:**

1. **Initialize `n` and `fact`:**
   - `n = 5`: Input number for which we calculate the factorial.
   - `fact = 1`: Variable to store the factorial result, initially set to 1.

2. **For Loop:**
   - The loop runs from `i = 1` to `i = n` (inclusive).
   - In each iteration:
     - Multiply the current value of `fact` by `i` and store the result back in `fact`.

3. **Final Result:**
   - After the loop ends, `fact` contains the final factorial of `n`.
   - Print the value of `fact` to display the result.

---

**Testcase Walkthrough:**

| **Iteration** | **Value of `i`** | **Value of `fact` (Before)** | **Value of `fact` (After)** | **Calculation**     |
|---------------|-------------------|-----------------------------|----------------------------|---------------------|
| 1             | 1                 | 1                           | 1                          | \( 1 \times 1 = 1 \) |
| 2             | 2                 | 1                           | 2                          | \( 1 \times 2 = 2 \) |
| 3             | 3                 | 2                           | 6                          | \( 2 \times 3 = 6 \) |
| 4             | 4                 | 6                           | 24                         | \( 6 \times 4 = 24 \) |
| 5             | 5                 | 24                          | 120                        | \( 24 \times 5 = 120 \) |

---

**Output:**
```
120
```

---
### Problem: Calculate Factorial of a Number

Write a function `factorial` that takes an integer `n` as input and returns its factorial.

---

### **Code**

```java
class Solution {
    static int factorial(int n) {
        // Declare and initialize factorial to 1
        int factorial = 1;

        // Loop to calculate factorial
        for (int i = 1; i <= n; i++) {
            factorial = factorial * i; // Multiply current factorial with i
        }

        // Return the computed factorial
        return factorial;
    }
}
```

---

### **Explanation**

1. **Input**: An integer `n` (e.g., `n = 5`).

2. **Initialization**:
   - `int factorial = 1;` — The `factorial` variable is initialized to 1 because multiplying by 1 does not change the result.

3. **Loop**:
   - A `for` loop iterates from 1 to `n`.
   - During each iteration, the current value of `factorial` is multiplied by the loop variable `i`, and the result is stored back in `factorial`.

4. **Return Statement**:
   - After the loop completes, the computed factorial value is returned.

---

### **Example Walkthrough**

#### Example 1:
**Input**:  
`n = 5`

**Execution**:  
- **Iteration 1**: `factorial = 1 * 1 = 1`
- **Iteration 2**: `factorial = 1 * 2 = 2`
- **Iteration 3**: `factorial = 2 * 3 = 6`
- **Iteration 4**: `factorial = 6 * 4 = 24`
- **Iteration 5**: `factorial = 24 * 5 = 120`

**Output**:  
`120`

#### Example 2:
**Input**:  
`n = 0`

**Execution**:  
- The loop does not execute because `n = 0`.  
- By definition, `0! = 1`.

**Output**:  
`1`

---

### **Complexity Analysis**

- **Time Complexity**:  
  \( O(n) \) — The loop runs `n` times.

- **Space Complexity**:  
  \( O(1) \) — Only a constant amount of space is used.

---

### **Test Cases**

#### Test Case 1:
Input: `n = 5`  
Output: `120`

#### Test Case 2:
Input: `n = 0`  
Output: `1`

#### Test Case 3:
Input: `n = 10`  
Output: `3628800`

#### Test Case 4:
Input: `n = 1`  
Output: `1`

---

### **Conclusion**

This code correctly computes the factorial of a given number `n`. The implementation is efficient and handles edge cases like `n = 0` properly.

