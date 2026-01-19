
---

###  – Fibonacci Series using While Loop (Java)**
**📌 Question:**
Write a Java program to print the *n-th term* of the Fibonacci series using a `while` loop.
The Fibonacci series starts with `0, 1` and each next term is the sum of the previous two.

**📘 Explanation:**

1. We first take an integer input `n` (the position in the Fibonacci sequence).
2. Initialize two variables:

   * `a = 0` (first Fibonacci number)
   * `b = 1` (second Fibonacci number)
3. Use a `while` loop that continues until we reach the `n`th term.
4. In each iteration:

   * Store `b` in a temporary variable.
   * Update `b` as the sum of `a + b`.
   * Assign the previous `b` (stored in `temp`) to `a`.
   * Increment the count.
5. After the loop ends, print the **n-th Fibonacci number** (`b`).

---

```java
// Week 3 - Fibonacci Series using While Loop
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        
        // Initialize first two Fibonacci numbers
        int a = 0;
        int b = 1;
        
        // Input: nth term to find
        int n = scan.nextInt();
        
        int count = 2; // Starting count from 2 as first two numbers are already defined
        
        // Loop to calculate Fibonacci up to nth term
        while (count <= n) {
            int temp = b;
            b = b + a;
            a = temp;
            count++;
        }
        
        // Output: nth Fibonacci number
        System.out.println("The " + n + "th Fibonacci number is: " + b);
    }
}
```

---

**💡 Example Output:**

```
Input: 7  
Output: The 7th Fibonacci number is: 13
```

---

