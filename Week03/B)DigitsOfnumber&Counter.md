### **Question 1**
Write a program that gets `n` as input and prints the number of digits in the number.

---

### **Program**
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        System.out.println("Enter a number:");
        Scanner scan = new Scanner(System.in);
        int n = scan.nextInt(); // Input the number
        int count = 0; // Initialize count to 0

        // Loop to count the digits
        while (n > 0) {
            int ld = n % 10; // Extract the last digit (optional for understanding)
            count++; // Increment the count
            n = n / 10; // Remove the last digit
        }

        System.out.println("Number of digits: " + count); // Print the result
    }
}
```

---

### **Explanation**
1. **Input a Number**:
   - User enters an integer `n`.

2. **Count Digits**:
   - The program uses a `while` loop to count the digits.
   - The last digit is extracted using `n % 10`, but it is not mandatory for counting.
   - After processing the last digit, the number is reduced by dividing it by `10` (`n = n / 10`).
   - For each digit processed, `count` is incremented.

3. **Terminate the Loop**:
   - When `n` becomes `0`, the loop terminates.

4. **Output**:
   - After the loop, the program prints the total number of digits stored in `count`.

---

### **Test Cases**

#### Test Case 1:
**Input:**
```
325345
```

**Execution Steps**:
- `n = 325345`, `count = 0`
- `n = 32534`, `count = 1`
- `n = 3253`, `count = 2`
- `n = 325`, `count = 3`
- `n = 32`, `count = 4`
- `n = 3`, `count = 5`
- `n = 0`, `count = 6`

**Output:**
```
Number of digits: 6
```

---

#### Test Case 2:
**Input:**
```
9879
```

**Execution Steps**:
- `n = 9879`, `count = 0`
- `n = 987`, `count = 1`
- `n = 98`, `count = 2`
- `n = 9`, `count = 3`
- `n = 0`, `count = 4`

**Output:**
```
Number of digits: 4
```

---

### **Table for Visualization**

#### Input: `n = 325345`

| **Iteration** | **Value of `n`** | **Last Digit (`ld`)** | **Count** | **Action**        |
|---------------|-------------------|-----------------------|-----------|-------------------|
| 1             | 325345            | 5                     | 1         | `n = 32534`       |
| 2             | 32534             | 4                     | 2         | `n = 3253`        |
| 3             | 3253              | 3                     | 3         | `n = 325`         |
| 4             | 325               | 5                     | 4         | `n = 32`          |
| 5             | 32                | 2                     | 5         | `n = 3`           |
| 6             | 3                 | 3                     | 6         | `n = 0`           |

---

### **Output**
- **Test Case 1:** `Number of digits: 6`
- **Test Case 2:** `Number of digits: 4`
  ---
  Here’s the complete format for your GitHub reference, including the question, program, explanation, and test cases:

---

## Problem: Corner Digits Sum

### Question 2:

Given a number `N`, find the sum of the first and last digit of `N`.

### Example 1:
**Input:**
```
N = 12345
```
**Output:**
```
6
```
**Explanation:**  
The first digit is `1` and the last digit is `5`. Their sum is `1 + 5 = 6`.

### Example 2:
**Input:**
```
N = 98562
```
**Output:**
```
11
```
**Explanation:**  
The first digit is `9` and the last digit is `2`. Their sum is `9 + 2 = 11`.

---

### Code:

```java
// User function Template for Java
class Solution {
    public int corner_digitSum(int n) {
        // Extract the last digit
        int ld = n % 10;

        // Variable to store the first digit
        int fd = 0;

        // Find the first digit using a loop
        while (n > 0) {
            fd = n % 10; // Extract the current digit
            n = n / 10;  // Remove the last digit
        }

        // Return the sum of first and last digits
        return fd + ld;
    }
}
```

---

### Explanation:

1. **Extract the Last Digit (`ld`):**
   ```java
   int ld = n % 10;
   ```
   - The last digit of `N` is extracted using the modulus operator `%`.

2. **Find the First Digit (`fd`):**
   ```java
   while (n > 0) {
       fd = n % 10;
       n = n / 10;
   }
   ```
   - The `while` loop iterates through all the digits of `N` by removing the last digit in each iteration (`n = n / 10`).
   - The loop stops when `n` becomes `0`, leaving `fd` as the first digit.

3. **Sum of First and Last Digits:**
   ```java
   return fd + ld;
   ```
   - Adds the first digit (`fd`) and the last digit (`ld`) and returns the result.

---

### Test Cases:

#### Test Case 1:
**Input:**
```
N = 12345
```
**Output:**
```
6
```
**Explanation:**
- Last digit (`ld`) = 5.
- First digit (`fd`) = 1.
- Sum = `1 + 5 = 6`.

---

#### Test Case 2:
**Input:**
```
N = 98562
```
**Output:**
```
11
```
**Explanation:**
- Last digit (`ld`) = 2.
- First digit (`fd`) = 9.
- Sum = `9 + 2 = 11`.

---

### Complexity Analysis:

- **Time Complexity:** \(O(\log_{10}(N))\)  
  - The loop runs for the number of digits in `N`.
- **Space Complexity:** \(O(1)\)  
  - Uses a constant amount of extra space.

---


