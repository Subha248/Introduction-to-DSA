
---

### **Prime Number Checker in Java**

**Problem Statement:**

Write a program in Java to determine whether a given number \( n \) is a prime number or not.

#### **Definition of a Prime Number:**
- A prime number is a number greater than 1 that has no divisors other than 1 and itself.
- Examples: \( 2, 3, 5, 7, 11, 13, \dots \)

---

### **Code Implementation**

```java
import java.util.*; // Importing the Scanner class for user input

public class Main { 
    public static void main(String[] args) { 
        Scanner scan = new Scanner(System.in); // Creating a scanner object to read input
        
        int n = scan.nextInt(); // Reading an integer input from the user
        
        // Step 1: Check if the number is less than or equal to 1
        if (n <= 1) { 
            System.out.println("not a prime"); // If n is less than or equal to 1, it's not prime
            return; // Exit the program since we already know the result
        }
        
        // Step 2: Loop from 2 up to the square root of n
        for (int i = 2; i * i <= n; i++) { 
            // Check if n is divisible by i
            if (n % i == 0) { 
                System.out.println("not a prime"); // If n is divisible by i, it's not a prime number
                return; // Exit the program since we found a divisor
            }
        }
        
        // Step 3: If no divisors were found, n is a prime number
        System.out.println("a prime"); // Output that the number is prime
    }
}
```

---

### **How the Code Works**

The program uses a loop to check for divisors of \( n \). If any divisor other than \( 1 \) or \( n \) is found, it concludes that \( n \) is not a prime number. For efficiency, the loop runs only up to \( \sqrt{n} \), as any divisor greater than \( \sqrt{n} \) would have a corresponding divisor smaller than \( \sqrt{n} \).

---

### **Code Execution Table**

#### **Case 1: \( n = 7 \) (Prime)**

| **Step** | **Value of \( i \)** | **Check \( i \times i \leq n \)** | **Check \( n \% i == 0 \)** | **Action**               |
|----------|----------------------|----------------------------------|----------------------------|--------------------------|
| 1        | Input \( n = 7 \)    | -                                | -                          | Start                   |
| 2        | \( i = 2 \)          | \( 2 \times 2 = 4 \leq 7 \)      | \( 7 \% 2 \neq 0 \)        | Continue Loop           |
| 3        | \( i = 3 \)          | \( 3 \times 3 = 9 > 7 \)         | -                          | Exit Loop               |
| 4        | -                    | -                                | -                          | Print "a prime"         |

**Output:**
```
a prime
```

---

#### **Case 2: \( n = 10 \) (Not Prime)**

| **Step** | **Value of \( i \)** | **Check \( i \times i \leq n \)** | **Check \( n \% i == 0 \)** | **Action**               |
|----------|----------------------|----------------------------------|----------------------------|--------------------------|
| 1        | Input \( n = 10 \)   | -                                | -                          | Start                   |
| 2        | \( i = 2 \)          | \( 2 \times 2 = 4 \leq 10 \)     | \( 10 \% 2 == 0 \)         | Print "not a prime"     |

**Output:**
```
not a prime
```

---

#### **Case 3: \( n = 1 \) (Not Prime)**

| **Step** | **Value of \( i \)** | **Check \( i \times i \leq n \)** | **Check \( n \% i == 0 \)** | **Action**               |
|----------|----------------------|----------------------------------|----------------------------|--------------------------|
| 1        | Input \( n = 1 \)    | -                                | -                          | Print "not a prime"     |

**Output:**
```
not a prime
```

---

#### **Case 4: \( n = 25 \) (Not Prime)**

| **Step** | **Value of \( i \)** | **Check \( i \times i \leq n \)** | **Check \( n \% i == 0 \)** | **Action**               |
|----------|----------------------|----------------------------------|----------------------------|--------------------------|
| 1        | Input \( n = 25 \)   | -                                | -                          | Start                   |
| 2        | \( i = 2 \)          | \( 2 \times 2 = 4 \leq 25 \)     | \( 25 \% 2 \neq 0 \)       | Continue Loop           |
| 3        | \( i = 3 \)          | \( 3 \times 3 = 9 \leq 25 \)     | \( 25 \% 3 \neq 0 \)       | Continue Loop           |
| 4        | \( i = 4 \)          | \( 4 \times 4 = 16 \leq 25 \)    | \( 25 \% 4 \neq 0 \)       | Continue Loop           |
| 5        | \( i = 5 \)          | \( 5 \times 5 = 25 \leq 25 \)    | \( 25 \% 5 == 0 \)         | Print "not a prime"     |

**Output:**
```
not a prime
```

---

### **Why This Code Works**

1. **Efficient Prime Check:**
   - The loop runs up to \( \sqrt{n} \), making it faster for larger numbers.
   
2. **Handles Edge Cases:**
   - Directly marks \( n \leq 1 \) as not prime.
   
3. **Early Exit:**
   - Stops checking as soon as a divisor is found, avoiding unnecessary calculations.

---

### **Summary of the Table Columns**

| **Column**             | **Description**                                                                 |
|-------------------------|---------------------------------------------------------------------------------|
| **Step**               | Sequence of operations in the program.                                         |
| **Value of \( i \)**    | The number currently being checked as a divisor.                              |
| **Check \( i \times i \leq n \)** | Verifies if the loop condition is satisfied.                              |
| **Check \( n \% i == 0 \)** | Checks if \( n \) is divisible by \( i \).                                    |
| **Action**              | Describes what the program does at each step (e.g., continue, exit, print).   |

---


---

### **Why Only Check Up to the Square Root?**

1. **Divisors Come in Pairs:**
   - Every number \( n \) can be expressed as a product of two factors: \( a \times b = n \).
   - If \( a \leq \sqrt{n} \), then \( b \geq \sqrt{n} \), and vice versa.

   Example:
   - \( n = 36 \):
     - Divisor pairs: \( (1, 36), (2, 18), (3, 12), (4, 9), (6, 6) \).
     - Once you’ve checked up to \( \sqrt{36} = 6 \), you’ve effectively checked all possible divisors.

2. **No Need to Check Larger Factors:**
   - If a number \( n \) is divisible by any number greater than \( \sqrt{n} \), the corresponding smaller factor would already have been checked.

   Example:
   - For \( n = 36 \), if you check \( 9 \), you’ll already know that \( 36 \div 9 = 4 \), and \( 4 \) was checked earlier.

3. **Efficiency:**
   - By only checking up to \( \sqrt{n} \), you drastically reduce the number of checks needed.
   - Instead of checking all numbers from \( 2 \) to \( n-1 \), you only check up to \( \sqrt{n} \).

---

### **What Does the Program Do?**

1. It loops from \( i = 2 \) to \( i \times i \leq n \) (i.e., up to \( \sqrt{n} \)).
2. For each \( i \), it checks if \( n \% i == 0 \):
   - If true, \( n \) is divisible by \( i \), so it’s **not prime**.
   - If no such \( i \) is found, \( n \) is **prime**.

---

### **Why Multiplying Instead of Taking Square Root?**

In the loop condition:
```java
for (int i = 2; i * i <= n; i++)
```

1. **Avoiding the Square Root Calculation:**
   - Directly calculating \( \sqrt{n} \) (e.g., using `Math.sqrt(n)`) is computationally expensive.
   - Instead, comparing \( i \times i \leq n \) avoids the need for floating-point arithmetic and ensures accuracy.

2. **Iterative Multiplication:**
   - \( i * i \) is checked incrementally for each \( i \), which is simpler and efficient for this purpose.

---

### **Example Walkthrough**

Let’s analyze \( n = 36 \):

#### Step 1: Start Loop
- \( i = 2 \):  
  \( 2 \times 2 = 4 \leq 36 \).  
  \( 36 \% 2 == 0 \), so \( n \) is **not prime**.

#### Step 2: Check Smaller \( n \) (e.g., \( n = 37 \)):
- \( i = 2 \):  
  \( 2 \times 2 = 4 \leq 37 \).  
  \( 37 \% 2 \neq 0 \), continue.

- \( i = 3 \):  
  \( 3 \times 3 = 9 \leq 37 \).  
  \( 37 \% 3 \neq 0 \), continue.

- \( i = 4 \):  
  \( 4 \times 4 = 16 \leq 37 \).  
  \( 37 \% 4 \neq 0 \), continue.

- \( i = 5 \):  
  \( 5 \times 5 = 25 \leq 37 \).  
  \( 37 \% 5 \neq 0 \), continue.

- \( i = 6 \):  
  \( 6 \times 6 = 36 \leq 37 \).  
  \( 37 \% 6 \neq 0 \), continue.

- \( i = 7 \):  
  \( 7 \times 7 = 49 > 37 \). Exit loop.

Since no divisors were found, \( n = 37 \) is **prime**.

---

### **Key Points**

1. **Why Check Up to \( \sqrt{n} \):**
   - Divisors come in pairs (\( a, b \)), and one of them is always \( \leq \sqrt{n} \).

2. **Why Use \( i \times i \):**
   - Avoids unnecessary computation of \( \sqrt{n} \).
   - Simple integer comparison, avoiding floating-point inaccuracies.

3. **Efficient Prime Check:**
   - Instead of looping through all numbers up to \( n \), only loop up to \( \sqrt{n} \).

