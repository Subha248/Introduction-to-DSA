
---

### **Question**

**Problem Statement:**

Write a program in Java to find the number of divisors of a given integer \( n \) that are divisible by \( 3 \).

#### **Input:**
- A single integer \( n \) (\( 1 \leq n \leq 10^5 \)).

#### **Output:**
- Print the count of divisors of \( n \) that are divisible by \( 3 \).

---

### **Answer**

```java
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in); // For input
        int n = scan.nextInt(); // Read input number
        int count = 0; // Initialize count of divisors divisible by 3

        // Loop through all integers from 1 to n
        for (int i = 1; i <= n; i++) {
            // Check if i is a divisor of n and divisible by 3
            if (n % i == 0 && i % 3 == 0) {
                count++; // Increment count
            }
        }

        // Print the count of such divisors
        System.out.println(count);
    }
}
```

---

### **How the Program Works**

1. The program reads an integer \( n \).
2. It iterates through all numbers \( i \) from 1 to \( n \).
3. For each \( i \), it checks:
   - \( n \% i == 0 \): Is \( i \) a divisor of \( n \)?
   - \( i \% 3 == 0 \): Is \( i \) divisible by 3?
4. If both conditions are true, the program increments the counter.
5. Finally, it prints the count.

---

### **Example Outputs**

#### **Case 1: \( n = 6 \)**
1. Divisors of \( 6 \): \( 1, 2, 3, 6 \).
2. Divisors divisible by \( 3 \): \( 3, 6 \).
3. **Output:** `2`.

#### **Case 2: \( n = 10 \)**
1. Divisors of \( 10 \): \( 1, 2, 5, 10 \).
2. Divisors divisible by \( 3 \): None.
3. **Output:** `0`.

#### **Case 3: \( n = 12 \)**
1. Divisors of \( 12 \): \( 1, 2, 3, 4, 6, 12 \).
2. Divisors divisible by \( 3 \): \( 3, 6, 12 \).
3. **Output:** `3`.

---

### **Effective Table Visualization**

Let’s break down the **iteration** for \( n = 12 \).

| **Step** | **Value of \( i \)** | **Check \( n \% i == 0 \)** | **Check \( i \% 3 == 0 \)** | **Count Incremented?** |
|----------|-----------------------|----------------------------|----------------------------|-------------------------|
| 1        | \( i = 1 \)           | \( 12 \% 1 == 0 \) (Yes)   | \( 1 \% 3 != 0 \) (No)     | No                     |
| 2        | \( i = 2 \)           | \( 12 \% 2 == 0 \) (Yes)   | \( 2 \% 3 != 0 \) (No)     | No                     |
| 3        | \( i = 3 \)           | \( 12 \% 3 == 0 \) (Yes)   | \( 3 \% 3 == 0 \) (Yes)    | Yes (\( +1 \))         |
| 4        | \( i = 4 \)           | \( 12 \% 4 == 0 \) (Yes)   | \( 4 \% 3 != 0 \) (No)     | No                     |
| 5        | \( i = 5 \)           | \( 12 \% 5 != 0 \) (No)    | -                          | No                     |
| 6        | \( i = 6 \)           | \( 12 \% 6 == 0 \) (Yes)   | \( 6 \% 3 == 0 \) (Yes)    | Yes (\( +1 \))         |
| 7        | \( i = 7 \)           | \( 12 \% 7 != 0 \) (No)    | -                          | No                     |
| 8        | \( i = 12 \)          | \( 12 \% 12 == 0 \) (Yes)  | \( 12 \% 3 == 0 \) (Yes)   | Yes (\( +1 \))         |

**Final Count:** `3`

---

### **Explanation of Table Columns**

1. **Step**: Represents the sequence of operations in the loop.
2. **Value of \( i \)**: The current number being tested as a divisor.
3. **Check \( n \% i == 0 \)**: Verifies if \( i \) is a divisor of \( n \).
4. **Check \( i \% 3 == 0 \)**: Verifies if \( i \) is divisible by 3.
5. **Count Incremented?**: Indicates whether the count was increased in this step.

---

### **Final Explanation**

This program efficiently counts divisors of \( n \) that are divisible by \( 3 \). It works for any valid \( n \) and iterates through all numbers from \( 1 \) to \( n \), ensuring correctness.

