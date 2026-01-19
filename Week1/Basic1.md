
---

## **Question 1**

Write a program in Java to check if a person is eligible based on their age.  
- If the age is **greater than or equal to 18**, the program should:
  - Print `"eligible"`.
  - Increment the age by 1.
- Otherwise, the program should print `"Not eligible"`.

Finally, the program will print the updated age.

---

## **Program**

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        System.out.println("Enter age:");
        Scanner scan = new Scanner(System.in);
        int n = scan.nextInt(); // Input the age
        
        if (n >= 18) { // Check if the age is 18 or older
            n++; // Increment the age
            System.out.println("eligible");
        } else { // If the age is less than 18
            System.out.println("Not eligible");
        }
        
        System.out.println(n); // Print the (possibly updated) age
    }
}
```

---

## **Output**

### Example 1:
**Input:**
```
Enter age:
18
```

**Output:**
```
Enter age:
eligible
19
```

---

### Example 2:
**Input:**
```
Enter age:
30
```

**Output:**
```
Enter age:
eligible
31
```

---

### Example 3:
**Input:**
```
Enter age:
17
```

**Output:**
```
Enter age:
Not eligible
17
```

---

## **Explanation**

1. **Input Handling:**
   - The user enters an integer value for their age (`n`).

2. **Eligibility Check (`if`):**
   - If `n >= 18`:
     - The program prints `"eligible"`.
     - The age is incremented by 1 (`n++`).
   - If `n < 18`:
     - The program prints `"Not eligible"`, and the age remains unchanged.

3. **Final Output:**
   - The program prints the updated or unchanged age based on the conditions.

---

## **Working Table**

The following table shows how the program works step by step:

| **Input (Age)** | **Condition (`n >= 18`)** | **Output**           | **Updated Age (`n`)** |
|------------------|---------------------------|-----------------------|------------------------|
| 18               | `true`                   | `"eligible"`          | 19                     |
| 30               | `true`                   | `"eligible"`          | 31                     |
| 17               | `false`                  | `"Not eligible"`      | 17                     |
| 50               | `true`                   | `"eligible"`          | 51                     |
| 16               | `false`                  | `"Not eligible"`      | 16                     |

---

## **How to Use:**

1. **Input:**
   - Enter your age when prompted by the program.

2. **Output:**
   - The program will print whether you are `"eligible"` or `"Not eligible"`.
   - It will also print the updated or unchanged age.

---
Here’s the full content formatted for your GitHub repository, including the **question**, **program**, **output**, **explanation**, and a **table to visualize the working**.

---

## **Question 2**

Write a program in Java to find the largest number among three numbers entered by the user.  
The program should:
- Compare the numbers and determine which one is the largest.
- Ensure only one output is displayed using `if-else if-else`.

---

## **Program**

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        System.out.println("Enter three numbers:");
        Scanner scan = new Scanner(System.in);

        // Input three numbers
        int a = scan.nextInt();
        int b = scan.nextInt();
        int c = scan.nextInt();

        // Check the largest number
        if (a >= b && a >= c) {
            System.out.println("a is largest");
        } else if (b >= a && b >= c) {
            System.out.println("b is largest");
        } else {
            System.out.println("c is largest");
        }
    }
}
```

---

## **Output**

### Example 1:
**Input:**
```
Enter three numbers:
10
20
30
```

**Output:**
```
c is largest
```

---

### Example 2:
**Input:**
```
Enter three numbers:
50
30
40
```

**Output:**
```
a is largest
```

---

### Example 3:
**Input:**
```
Enter three numbers:
20
50
50
```

**Output:**
```
b is largest
```

---

## **Explanation**

1. **Input Handling:**
   - The user is prompted to input three integers, which are stored in variables `a`, `b`, and `c`.

2. **Comparison Logic (`if-else if-else`):**
   - **Case 1:** If `a` is greater than or equal to both `b` and `c`, the program prints `"a is largest"`.
   - **Case 2:** If `b` is greater than or equal to both `a` and `c`, the program prints `"b is largest"`.
   - **Case 3:** If neither of the above conditions is true, `c` must be the largest, and the program prints `"c is largest"`.

3. **Output:**
   - The program outputs the largest number based on the conditions.

---

## **Working Table**

The following table shows the logic applied to different inputs:

| **a** | **b** | **c** | **Condition Checked**          | **Output**        |
|-------|-------|-------|-------------------------------|-------------------|
| 10    | 20    | 30    | `c >= a && c >= b`            | `c is largest`    |
| 50    | 30    | 40    | `a >= b && a >= c`            | `a is largest`    |
| 20    | 50    | 50    | `b >= a && b >= c`            | `b is largest`    |
| 30    | 30    | 10    | `a >= b && a >= c`            | `a is largest`    |
| 40    | 40    | 40    | Any condition (all are equal) | `a is largest`    |

---

## **Why Use `if-else if-else`?**

### **Advantages:**
1. **Mutual Exclusivity:**
   - Only one condition is evaluated once the correct one is found.
   - This prevents redundant evaluations and multiple outputs for overlapping conditions.

2. **Efficiency:**
   - The program stops checking further conditions as soon as one is true.

3. **Cleaner Logic:**
   - Ensures a single, logical flow with no ambiguity.

### Example:
For input `10, 10, 5`:
- Using `if-else if-else`:
  - Output: `a is largest`
- Using independent `if` statements:
  - Output: 
    ```
    a is largest
    b is largest
    ```

---

## **How to Use:**

1. Input three integers when prompted.
2. The program will determine the largest number among the three and print the result.

---


---
---
## **Question 3**: Write a program to check if a number is positive or negative, and if positive, determine if it is even or odd.

### **Program**

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        System.out.println("Enter number:");
        Scanner scan = new Scanner(System.in);
        int a = scan.nextInt(); // Input the number

        // Block 1: Check if the number is positive
        if (a > 0) {
            // Block 2: Check if the number is even or odd
            if (a % 2 == 0) {
                System.out.println("Positive and even");
            } else {
                System.out.println("Positive and odd");
            }
        } 
        // Block 3: If the number is not positive, it is negative
        else {
            System.out.println("Negative");
        }
    }
}
```

---

### **Explanation with Blocks and Examples**

#### **Block 1: Check if the Number is Positive**

```java
if (a > 0) {
    // Block 2 executes if this is true
}
else {
    // Block 3 executes if this is false
}
```

- If the number is **greater than 0**, the program moves to **Block 2** to check if it is even or odd.
- If the number is **not greater than 0**, the program skips **Block 2** and goes to **Block 3**, printing `"Negative"`.

---

#### **Block 2: Check if the Number is Even or Odd**

```java
if (a % 2 == 0) {
    System.out.println("Positive and even");
} else {
    System.out.println("Positive and odd");
}
```

- If the number is divisible by `2` (`a % 2 == 0`), it prints `"Positive and even"`.
- If not, it prints `"Positive and odd"`.

---

#### **Block 3: Handle Negative Numbers**

```java
else {
    System.out.println("Negative");
}
```

- If the number is not positive, the program prints `"Negative"` without checking if it’s even or odd (because negatives are not categorized like that here).

---

### **Example Walkthroughs**

#### **Example 1: Input = 10**
1. **Input:** `10`
2. **Block 1:** `10 > 0` → **True**
3. **Block 2:** `10 % 2 == 0` → **True** (10 is even).
4. **Output:**
   ```
   Positive and even
   ```

---

#### **Example 2: Input = 15**
1. **Input:** `15`
2. **Block 1:** `15 > 0` → **True**
3. **Block 2:** `15 % 2 == 0` → **False** (15 is odd).
4. **Output:**
   ```
   Positive and odd
   ```

---

#### **Example 3: Input = -7**
1. **Input:** `-7`
2. **Block 1:** `-7 > 0` → **False**
3. **Block 3:** The program skips Block 2 and directly prints `"Negative"`.
4. **Output:**
   ```
   Negative
   ```

---

### **Visual Summary**

| **Input** | **Block 1 (a > 0)** | **Block 2 (a % 2 == 0)** | **Block 3** | **Output**            |
|-----------|---------------------|--------------------------|-------------|-----------------------|
| 10        | True                | True                     | Skipped     | Positive and even     |
| 15        | True                | False                    | Skipped     | Positive and odd      |
| -7        | False               | Skipped                  | True        | Negative              |
| -4        | False               | Skipped                  | True        | Negative              |
| 0         | False               | Skipped                  | True        | Negative              |

---

### **Why is This Program Simple and Effective?**

1. **Blocks of Logic:**
   - Separate checks for positivity and even/odd make the program easy to understand and maintain.

2. **Efficiency:**
   - Negative numbers skip the unnecessary even/odd check.
   - Positive numbers directly proceed to even/odd classification.

3. **Readability:**
   - Nested conditions help group related checks (positive → even/odd).

---
Here is the content formatted for your GitHub repository:

---

## **Question**

Write a program to print the day of the week based on the input number. If the number does not correspond to a valid day, print `"invalid"`.

---

## **Program**

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        System.out.println("Enter number:");
        Scanner scan = new Scanner(System.in);
        int day = scan.nextInt(); // Input for the day

        switch (day) {
            case 1: {
                System.out.println("Monday");
                break;
            }
            case 2: {
                System.out.println("Tuesday");
                break;
            }
            case 3: {
                System.out.println("Wednesday");
                break;
            }
            default: {
                System.out.println("invalid");
            }
        }
    }
}
```

---

## **Output**

### Example 1:
**Input:**
```
1
```

**Output:**
```
Monday
```
---

### Example 3:
**Input:**
```
5
```

**Output:**
```
invalid
```

---

## **Explanation**

1. **Input Handling:**
   - The user is prompted to enter an integer (`day`), which represents the day of the week.

2. **Switch Statement:**
   - The program evaluates the value of `day` using the `switch` statement:
     - `case 1`: Prints `"Monday"`.
     - `case 2`: Prints `"Tuesday"`.
     - `case 3`: Prints `"Wednesday"`.
   - If the value of `day` does not match any of the cases (`1`, `2`, `3`), the `default` case executes, printing `"invalid"`.

3. **Break Statements:**
   - After each `case`, the `break` statement ensures that no other cases are executed.

---

## **Working Table**

| **Input (day)** | **Switch Case Triggered** | **Output**   |
|------------------|---------------------------|--------------|
| 1                | `case 1`                 | Monday       |
| 2                | `case 2`                 | Tuesday      |
| 3                | `case 3`                 | Wednesday    |
| 5                | `default`                | invalid      |
| -1               | `default`                | invalid      |

---

## **How to Use:**

1. Run the program and input a number.
2. The program will print the corresponding day for numbers `1` to `3`.
3. For any other number, the program will print `"invalid"`.

---


