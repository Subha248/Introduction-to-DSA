

---

### 🧮 Week 3 – Simple Calculator using `while` Loop (Java)

**📌 Question:**
Write a Java program that performs basic arithmetic operations (`+`, `-`, `*`, `/`, `%`) using a `while` loop.
The program should keep taking input from the user until they press `'x'` or `'X'` to exit.

---

**📘 Explanation (Concise):**

1. The program runs in an infinite `while (true)` loop.
2. It asks the user to enter an operator (`+`, `-`, `*`, `/`, `%`).
3. If the user enters `'x'` or `'X'`, the loop breaks — program ends.
4. Otherwise, it takes two integer inputs and performs the chosen arithmetic operation.
5. If the operator is invalid, it prints **"invalid operation"**.
6. The result of the operation is displayed, and the program continues asking for the next operator.

---

```java
import java.util.*;

public class condition {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);

        while (true) {
            System.out.print("Enter the operator (+, -, *, /, %, or X to exit): ");
            char ch = scan.next().trim().charAt(0);

            if (ch == 'x' || ch == 'X') {
                break; // exit the loop
            }

            int ans = 0;

            if (ch == '+' || ch == '-' || ch == '*' || ch == '/' || ch == '%') {
                System.out.print("Enter two numbers: ");
                int a = scan.nextInt();
                int b = scan.nextInt();

                if (ch == '+') {
                    ans = a + b;
                } else if (ch == '-') {
                    ans = a - b;
                } else if (ch == '*') {
                    ans = a * b;
                } else if (ch == '/') {
                    if (b != 0) {
                        ans = a / b;
                    } else {
                        System.out.println("Division by zero not allowed!");
                        continue;
                    }
                } else if (ch == '%') {
                    ans = a % b;
                }

                System.out.println("The result is: " + ans);
            } else {
                System.out.println("Invalid operation");
            }
        }

        scan.close();
        System.out.println("Calculator closed.");
    }
}
```

---

**💡 Example Output:**

```
Enter the operator (+, -, *, /, %, or X to exit): +
Enter two numbers: 5 3
The result is: 8
Enter the operator (+, -, *, /, %, or X to exit): x
Calculator closed.
```

---

