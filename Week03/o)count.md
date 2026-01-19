

### 🔢 Week 3 – Count the Occurrences of Digit '3' in a Number (Java)

**📌 Question:**
Write a Java program to count how many times the digit `'3'` appears in a given number.

**📘 Explanation:**

1. Take an integer input from the user.
2. Initialize a counter variable `count = 0`.
3. Use a `while` loop to extract each digit of the number using modulus (`%`) and division (`/`).
4. Check if the extracted digit equals `3`.
5. If yes, increment the counter.
6. After the loop, print the total count of `'3'` digits found in the number.

---

```java
import java.util.Scanner;

/**
 * This program counts how many times the digit '3' appears in a given number.
 *
 * Example:
 * Input: 133
 * Output: 2
 * Explanation: The number 133 contains two '3' digits.
 */
public class CountDigitThree {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a number: ");
        int number = scanner.nextInt();
        int count = 0;

        // Count occurrences of digit 3
        while (number > 0) {
            if (number % 10 == 3) {
                count++;
            }
            number = number / 10;
        }

        System.out.println("Count of digit 3: " + count);
        scanner.close();
    }
}
```

---

**💡 Example Output:**

```
Enter a number: 133
Count of digit 3: 2
```

---

