
## **Question**
### Find the \( K \)-th Digit from \( A^B \) (Right to Left)

Write a program to calculate \( A^B \) (A raised to the power B) and find the \( K \)-th digit from the right in the resulting number. If \( K \) is larger than the number of digits in \( A^B \), print `0`.

---

## **Program**

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);

        // Input values for A, B, and K
        int A = scan.nextInt();
        int B = scan.nextInt();
        int K = scan.nextInt();

        // Step 1: Compute A^B
        long power = (long) Math.pow(A, B);
        long i = 1; // Position counter for digits

        // Step 2: Extract the K-th digit
        while (power > 0) {
            long ans = power % 10; // Extract the last digit

            if (i == K) { // Check if it's the K-th digit
                System.out.println(ans); // Print the K-th digit
                return; // Exit once the digit is found
            }

            power = power / 10; // Remove the last digit
            i++; // Increment the position
        }

        // If the loop finishes without finding the K-th digit
        System.out.println(0);
    }
}
```

---

## **Explanation**

1. **Input Values**:
   - `A` (base), `B` (exponent), and `K` (position of digit to find).

2. **Compute \( A^B \)**:
   - Use `Math.pow(A, B)` to calculate \( A^B \) and store it as a `long` to handle large numbers.

3. **Digit Extraction**:
   - The loop processes one digit at a time from right to left:
     - Extract the last digit using `% 10`.
     - Check if the current digit is the \( K \)-th digit using a counter `i`.

4. **Output the Result**:
   - If the \( K \)-th digit is found, print it and exit the program.
   - If the loop finishes and \( K \) is larger than the number of digits, print `0`.

---

## **Example Input and Output**

### Example 1:
**Input**:
```
3
3
2
```
**Execution**:
- \( A^B = 3^3 = 27 \)
- Digits from right to left: `7`, `2`
- \( K = 2 \), so the output is:
```
2
```

---

### Example 2:
**Input**:
```
5
2
3
```
**Execution**:
- \( A^B = 5^2 = 25 \)
- Digits from right to left: `5`, `2`
- \( K = 3 \), which is larger than the number of digits:
```
0
```

---

### Example 3:
**Input**:
```
2
10
1
```
**Execution**:
- \( A^B = 2^{10} = 1024 \)
- Digits from right to left: `4`, `2`, `0`, `1`
- \( K = 1 \), so the output is:
```
4
```

---

### **Key Points**
1. The program processes digits from right to left using `% 10`.
2. Handles cases where \( K \) is larger than the number of digits by printing `0`.
3. Efficiently stops once the \( K \)-th digit is found.

---

