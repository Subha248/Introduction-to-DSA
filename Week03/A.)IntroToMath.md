
---

## **Question 1**

Write a program in Java to find the **last digit** of a given number.

### Explanation:
The last digit of a number can be obtained by performing the modulus operation with `10`:
- For example:
  - \( 345 \% 10 = 5 \)
  - \( 9876 \% 10 = 6 \)

---

## **Program**

```java
public class Main {
    public static void main(String[] args) {
        int number = 345345; // Input number
        int lastDigit = number % 10; // Find the last digit
        System.out.println("The last digit is: " + lastDigit); // Output the result
    }
}
```

---

## **Output**

### Input:
```
345345
```

### Output:
```
The last digit is: 5
```

---

## **Explanation**

1. **Input Number:** 
   - The number `345345` is stored in the variable `number`.

2. **Finding the Last Digit:**
   - Using `number % 10`, we calculate the remainder when the number is divided by 10. This remainder is the last digit of the number.
   - For `345345`, \( 345345 \% 10 = 5 \).

3. **Output the Result:**
   - `System.out.println("The last digit is: " + lastDigit);` prints the last digit to the console.

## **Working Table**

| **Input (n)** | **`n % 10` (Last Digit)** | **Output** |
|---------------|---------------------------|------------|
| 1234          | 4                         | 4          |
| 98765         | 5                         | 5          |
| 1000          | 0                         | 0          |
| 7             | 7                         | 7          |

---
---


## **Question 2**

Write a program in Java to reverse the digits of a given number using a `while` loop. For example, if the input is `1234`, the program should output `4321`.

---

## **Program**

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);

        System.out.println("Enter a number:");
        int n = scan.nextInt(); // Read the input number

        while (n > 0) { // Loop to reverse the digits
            int l = n % 10; // Get the last digit
            System.out.print(l); // Print the digit
            n = n / 10; // Remove the last digit from the number
        }
    }
}
```

---

## **Output**

### Example 1:
**Input:**
```
1234
```

**Output:**
```
4321
```

---

### Example 2:
**Input:**
```
98765
```

**Output:**
```
56789
```

---

## **Explanation**

1. **Input Handling:**
   - The program reads an integer `n` from the user using `Scanner`.

2. **Reversing Logic:**
   - Inside the `while` loop:
     - **`n % 10`**:
       - Extracts the last digit of the number.
       - Example: For `1234`, `1234 % 10 = 4`.
     - **`System.out.print(l)`**:
       - Prints the extracted digit.
     - **`n = n / 10`**:
       - Removes the last digit of the number by dividing it by `10`.
       - Example: For `1234`, `1234 / 10 = 123`.

3. **Loop Execution:**
   - The loop continues until `n` becomes `0`.

4. **Output:**
   - The digits are printed in reverse order because the last digit is extracted and printed first, followed by the remaining digits.

---

## **Working Table**

| **Input (n)** | **`n % 10` (Last Digit)** | **Print** | **`n / 10` (Remaining Number)** |
|---------------|---------------------------|-----------|----------------------------------|
| 1234          | 4                         | 4         | 123                              |
| 123           | 3                         | 3         | 12                               |
| 12            | 2                         | 2         | 1                                |
| 1             | 1                         | 1         | 0                                |

---

## **Key Points**

1. **Logic for Reversal:**
   - By repeatedly extracting the last digit and removing it from the number, the digits are printed in reverse order.

2. **Termination Condition:**
   - The loop stops when `n` becomes `0`, as there are no more digits to process.

3. **Scalability:**
   - This program works for any positive integer input.

---

---

## **Question 3**

Write a program in Java to find and print the **first digit** of a given number using a `while` loop.

---

## **Program**

```java
import java.util.*;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int n = scan.nextInt(); // Read the input number

        while (n > 0) { // Loop to process the digits
            int fd = n % 10; // Extract the last digit
            n = n / 10; // Remove the last digit
            if (n == 0) // If no more digits remain
                System.out.println(fd); // Print the first digit
        }
    }
}
```

---

## **Output**

### Example 1:
**Input:**
```
1234
```

**Output:**
```
1
```

---

### Example 2:
**Input:**
```
98765
```

**Output:**
```
9
```

---

### Example 3:
**Input:**
```
5
```

**Output:**
```
5
```

---

## **Explanation**

1. **Input Handling:**
   - The program reads an integer `n` from the user using `Scanner`.

2. **Logic to Find the First Digit:**
   - The `while` loop extracts each digit of the number using `n % 10` and removes it using `n / 10`.
   - When `n == 0` (i.e., no more digits are left), the last extracted digit (`fd`) is the **first digit** of the original number.

3. **Output:**
   - The program prints the first digit when the loop identifies that there are no more digits left.

---

## **Working Table**

For input `98765`:

| **Iteration** | **Value of `n`** | **`fd = n % 10`** | **Condition (`n == 0`)** | **Action**         |
|---------------|-------------------|-------------------|--------------------------|--------------------|
| 1             | 98765            | 5                 | False                   | Continue           |
| 2             | 9876             | 6                 | False                   | Continue           |
| 3             | 987              | 7                 | False                   | Continue           |
| 4             | 98               | 8                 | False                   | Continue           |
| 5             | 9                | 9                 | True                    | Print `9`          |

---
---

## **Question 4**

Write a program in Java to count the number of digits in a given number using a `while` loop.

---

## **Program**

```java
import java.util.*;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);

        System.out.println("Enter a number:");
        int n = scan.nextInt(); // Input the number
        int count = 0; // Initialize count to 0

        while (n > 0) {
            count = count + 1; // Increment count for each digit
            n = n / 10; // Remove the last digit
        }

        System.out.println("Number of digits: " + count); // Print the count
    }
}
```

---

## **Explanation**

1. **`count = 0`:**
   - A variable to keep track of the number of digits in the number.

2. **`while (n > 0)`:**
   - The loop continues as long as `n` is greater than `0`.

3. **`count = count + 1`:**
   - For each iteration, `count` is incremented to count the digits.

4. **`n = n / 10`:**
   - Dividing `n` by `10` removes the last digit of the number.

5. **Output:**
   - After the loop ends, `count` holds the total number of digits, which is printed to the console.

---

## **Output**

### Example 1:
**Input:**
```
1234
```

**Output:**
```
Number of digits: 4
```

---

### Example 2:
**Input:**
```
98765
```

**Output:**
```
Number of digits: 5
```

---

## **Visualization Table**

### **Input: `1234`**

| **Iteration** | **Value of `n`** | **`count` (Before Increment)** | **`count` (After Increment)** | **Action Performed**  |
|---------------|-------------------|-------------------------------|-------------------------------|-----------------------|
| 1             | 1234             | 0                             | 1                             | `n = n / 10 → 123`   |
| 2             | 123              | 1                             | 2                             | `n = n / 10 → 12`    |
| 3             | 12               | 2                             | 3                             | `n = n / 10 → 1`     |
| 4             | 1                | 3                             | 4                             | `n = n / 10 → 0`     |

---

### **Input: `98765`**

| **Iteration** | **Value of `n`** | **`count` (Before Increment)** | **`count` (After Increment)** | **Action Performed**  |
|---------------|-------------------|-------------------------------|-------------------------------|-----------------------|
| 1             | 98765            | 0                             | 1                             | `n = n / 10 → 9876`  |
| 2             | 9876             | 1                             | 2                             | `n = n / 10 → 987`   |
| 3             | 987              | 2                             | 3                             | `n = n / 10 → 98`    |
| 4             | 98               | 3                             | 4                             | `n = n / 10 → 9`     |
| 5             | 9                | 4                             | 5                             | `n = n / 10 → 0`     |

---
### **Question 5: Analyze a Number for Even Digits and Print the Last Digit**
Write a program in Java that:
1. Counts how many even digits are in a given number.
2. Prints the last digit when the number becomes a single digit.

---

### **Program: Count Even Digits and Print the First Digit**

```java
/**
 * Program to count the number of even digits in a number
 * and print the first digit of the given number.
 */
import java.util.*;

public class Main {
    public static void main(String args[]) {
        Scanner scan = new Scanner(System.in);
        System.out.print("Enter a number: ");
        int n = scan.nextInt(); // Input the number

        int count = 0; // Variable to count even digits
        int e = 0; // Variable to store the current digit (to later store the first digit)

        // Loop to process each digit of the number
        while (n > 0) {
            e = n % 10; // Extract the last digit

            // Check if the digit is even
            if (e % 2 == 0) {
                count++; // Increment the count of even digits
            }

            n = n / 10; // Remove the last digit
        }

        // Print the results
        System.out.println("Number of even digits: " + count);
        System.out.println("First digit: " + e);
    }
}
```

---

### **Explanation of the Code**

1. **Input the Number:**
   ```java
   int n = scan.nextInt();
   ```
   - Takes an integer input from the user.

2. **Initialization:**
   ```java
   int count = 0; // Counts the even digits
   int e = 0;     // Stores the current digit, which will eventually hold the first digit
   ```

3. **Processing Digits:**
   - The `while` loop continues until all digits are processed:
     ```java
     while (n > 0) {
         e = n % 10; // Extract the last digit
         if (e % 2 == 0) {
             count++; // Increment if it's even
         }
         n = n / 10; // Remove the last digit
     }
     ```

4. **Results:**
   - After the loop ends, `e` holds the first digit, and `count` stores the number of even digits:
     ```java
     System.out.println("Number of even digits: " + count);
     System.out.println("First digit: " + e);
     ```

---

### **Visualization**

| **Step** | **n (Number)** | **e (Current Digit)** | **Even Check (e % 2 == 0)** | **Count** | **Remaining n** |
|----------|-----------------|-----------------------|-----------------------------|-----------|-----------------|
| Start    | `1234`          | -                     | -                           | `0`       | -               |
| 1        | `1234`          | `4`                   | True                        | `1`       | `123`           |
| 2        | `123`           | `3`                   | False                       | `1`       | `12`            |
| 3        | `12`            | `2`                   | True                        | `2`       | `1`             |
| 4        | `1`             | `1`                   | False                       | `2`       | `0`             |

---

### **Example Input and Output**

#### **Input:**
```
1234
```

#### **Output:**
```
Enter a number: 1234
Number of even digits: 2
First digit: 1
```

---

### **How It Works**
1. Each digit is processed using `n % 10`, which extracts the last digit.
2. If the digit is even (`e % 2 == 0`), the `count` is incremented.
3. The first digit is identified by updating `e` during each iteration of the loop. After the loop ends, `e` contains the first digit of the original number.

---

