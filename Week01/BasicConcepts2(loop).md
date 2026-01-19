
---

## **Question 1**

Write a program in Java to print numbers from `10` to `0` in reverse order using a `for` loop.

---

## **Program**

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        int n = 10; // Starting number

        // Loop to print numbers from 10 to 0 in reverse order
        for (int i = n; i >= 0; i--) {
            System.out.println(i);
        }
    }
}
```

---

## **Output**

### Example Output:
```
10
9
8
7
6
5
4
3
2
1
0
```

---

## **Explanation**

1. **Initialization:**
   - The variable `n` is set to `10`, which is the starting point for the countdown.

2. **For Loop:**
   ```java
   for (int i = n; i >= 0; i--) {
   ```
   - **`int i = n;`**: The loop starts with `i` equal to `10`.
   - **`i >= 0;`**: The loop continues as long as `i` is greater than or equal to `0`.
   - **`i--`**: After each iteration, the value of `i` decreases by `1`.

3. **Output:**
   - Inside the loop, the program prints the value of `i` on a new line.

---

## **How the Program Works**

| **Iteration** | **Value of `i`** | **Condition (`i >= 0`)** | **Output** |
|---------------|-------------------|--------------------------|------------|
| 1             | 10                | True                     | 10         |
| 2             | 9                 | True                     | 9          |
| 3             | 8                 | True                     | 8          |
| 4             | 7                 | True                     | 7          |
| 5             | 6                 | True                     | 6          |
| 6             | 5                 | True                     | 5          |
| 7             | 4                 | True                     | 4          |
| 8             | 3                 | True                     | 3          |
| 9             | 2                 | True                     | 2          |
| 10            | 1                 | True                     | 1          |
| 11            | 0                 | True                     | 0          |
| 12            | -1                | False                    | Loop ends  |

---

## **Key Points**

1. **Loop Control:**
   - The `for` loop structure ensures the countdown starts at `10` and stops at `0`.
   - The condition `i >= 0` ensures the loop runs until `i` becomes negative.

2. **Decrementing `i`:**
   - `i--` decreases the value of `i` by `1` in each iteration, creating the countdown effect.

3. **Scalability:**
   - You can modify the starting value of `n` to any other positive integer to print a countdown from that number.

---
### ***WHILE LOOP AND DO WHILE LOOP***

The difference between **`while`** and **`do-while`** lies in **when the condition is checked** and **how many times the loop executes**. Here's a detailed explanation along with examples:

---

### **Key Difference**

1. **`while` Loop:**
   - The condition is checked **before** the loop body executes.
   - If the condition is `false` at the start, the loop body may **not execute at all**.

2. **`do-while` Loop:**
   - The condition is checked **after** the loop body executes.
   - The loop body is guaranteed to execute **at least once**, even if the condition is `false`.

---

### **Example Code**

#### **Using `while` Loop**
```java
class Main {
    public static void main(String[] args) {
        int i = 10;

        while (i >= 0) { // Check condition first
            System.out.println(i);
            i--;
        }
    }
}
```

#### **Output:**
```
10
9
8
7
6
5
4
3
2
1
0
```

- **How It Works:**
  - The condition `i >= 0` is checked before entering the loop.
  - As long as the condition is true, the loop body executes.

---

#### **Using `do-while` Loop**
```java
class Main {
    public static void main(String[] args) {
        int i = 10;

        do {
            System.out.println(i);
            i--;
        } while (i >= 0); // Check condition after execution
    }
}
```

#### **Output:**
```
10
9
8
7
6
5
4
3
2
1
0
```

- **How It Works:**
  - The loop body executes first.
  - After each iteration, the condition `i >= 0` is checked.

---

### **Key Scenario: What If the Condition is False Initially?**

#### **With `while` Loop**
```java
class Main {
    public static void main(String[] args) {
        int i = -1;

        while (i >= 0) { // Condition is false
            System.out.println(i);
            i--;
        }
    }
}
```

#### **Output:**
```
```

- The condition `i >= 0` is false initially, so the loop body **does not execute even once**.

---

#### **With `do-while` Loop**
```java
class Main {
    public static void main(String[] args) {
        int i = -1;

        do {
            System.out.println(i); // Executes once, even though the condition is false
            i--;
        } while (i >= 0);
    }
}
```

#### **Output:**
```
-1
```

- The loop body executes **at least once**, printing `-1`, before checking the condition `i >= 0`.

---

### **Comparison Table**

| **Aspect**               | **`while` Loop**                                 | **`do-while` Loop**                             |
|--------------------------|--------------------------------------------------|------------------------------------------------|
| **Condition Check**       | At the beginning of the loop                    | After the loop body executes                   |
| **Minimum Executions**    | **0 times** (if the condition is false initially)| **At least once**, even if the condition is false|
| **Use Case**              | When the loop may or may not execute             | When the loop must execute at least once       |

---

### **When to Use Which?**

1. **`while` Loop:**
   - Use when the loop should execute **only if the condition is true** from the beginning.
   - Example: Running a loop to process user input only if the input meets specific criteria.

2. **`do-while` Loop:**
   - Use when the loop must **execute at least once**, regardless of the condition.
   - Example: Displaying a menu and prompting the user for input at least once.

---


