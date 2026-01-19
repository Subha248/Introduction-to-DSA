### Question

**Write a program that gets `n` as input and prints the reverse of the number.**

---

### Testcases

**Testcase 1**:  
**Input**:  
```
325345
```  
**Output**:  
```
543523
```

**Testcase 2**:  
**Input**:  
```
987987
```  
**Output**:  
```
789789
```

---

### Program

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        System.out.println("Enter a number:");
        Scanner scan = new Scanner(System.in);
        
        int n = scan.nextInt(); // Input the number
        
        // Reverse the number by extracting digits
        while (n > 0) {
            int ld = n % 10; // Extract the last digit
            System.out.print(ld); // Print the digit
            n = n / 10; // Remove the last digit
        }
    }
}
```

---

### Explanation

1. **Input the Number**:
   - The program takes an integer `n` as input using the `Scanner` class.

2. **Extract Last Digit**:
   - Inside the `while` loop, `% 10` extracts the last digit of `n`.

3. **Print in Reverse**:
   - The extracted digit is printed using `System.out.print()` to avoid a new line.

4. **Remove Last Digit**:
   - The number is divided by `10` using `n = n / 10` to process the next digit.

5. **Stop Condition**:
   - The loop stops when `n` becomes `0` (all digits are reversed).

---

### Execution Walkthrough

#### Testcase 1:
**Input**: `325345`

| **Iteration** | **Value of `n`** | **Last Digit (ld)** | **Printed Output** | **New `n`** |
|---------------|-------------------|---------------------|---------------------|--------------|
| 1             | 325345           | 5                   | `5`                 | 32534        |
| 2             | 32534            | 4                   | `54`                | 3253         |
| 3             | 3253             | 3                   | `543`               | 325          |
| 4             | 325              | 5                   | `5435`              | 32           |
| 5             | 32               | 2                   | `54352`             | 3            |
| 6             | 3                | 3                   | `543523`            | 0            |

**Output**:
```
543523
```

---

#### Testcase 2:
**Input**: `987987`

| **Iteration** | **Value of `n`** | **Last Digit (ld)** | **Printed Output** | **New `n`** |
|---------------|-------------------|---------------------|---------------------|--------------|
| 1             | 987987           | 7                   | `7`                 | 98798        |
| 2             | 98798            | 8                   | `78`                | 9879         |
| 3             | 9879             | 9                   | `789`               | 987          |
| 4             | 987              | 7                   | `7897`              | 98           |
| 5             | 98               | 8                   | `78978`             | 9            |
| 6             | 9                | 9                   | `789789`            | 0            |

**Output**:
```
789789
```
