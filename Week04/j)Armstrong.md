
---

## ✅ Final Code (Copy-Paste Ready)

```java
// 💫 Armstrong Number Checker
// A number is Armstrong if the sum of cubes of its digits equals the number itself
// Example: 153 → 1³ + 5³ + 3³ = 153 ✅

import java.util.*;
public class ArmstrongCheck {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);

    System.out.print("Enter a number: ");
    int n = sc.nextInt();

    boolean ans = isArmstrong(n);
    System.out.println("Is Armstrong? " + ans);
  }

  // 🌸 Method to check if a number is Armstrong
  static boolean isArmstrong(int n) {
    int original = n;   // store the original number
    int sum = 0;        // to hold the sum of cubes of digits

    // extract each digit one by one
    while (n > 0) {
      int rem = n % 10;            // get last digit
      sum = sum + rem * rem * rem; // add its cube to sum
      n = n / 10;                  // remove last digit
    }

    // check if the sum equals the original number
    return sum == original;
  }
}
```

---


---

### Example Run:

**Input:**

```
Enter a number: 153
```

**Step-by-step inside the program:**

1. `original = 153`
2. `sum = 0`

**While loop starts:**

* Last digit: `rem = 153 % 10 = 3` → `sum = 0 + 3*3*3 = 27` → `n = 153 / 10 = 15`
* Last digit: `rem = 15 % 10 = 5` → `sum = 27 + 5*5*5 = 152` → `n = 15 / 10 = 1`
* Last digit: `rem = 1 % 10 = 1` → `sum = 152 + 1*1*1 = 153` → `n = 1 / 10 = 0`

**While loop ends** (`n = 0`)

**Check:** `sum == original` → `153 == 153` → **true** ✅

---

**Output:**

```
Is Armstrong? true
```

---

### Another Example:

**Input:**

```
Enter a number: 120
```

**Steps inside the program:**

* `rem = 0` → sum = 0
* `rem = 2` → sum = 8
* `rem = 1` → sum = 9

**Check:** `sum == original` → `9 == 120` → **false** ❌

**Output:**

```
Is Armstrong? false
```

---

---
**2**
## GitHub-Ready Code

```java
// 💫 Armstrong Numbers (3-Digit) Finder
// This program prints all 3-digit Armstrong numbers (100 to 999)
// Example: 153 → 1³ + 5³ + 3³ = 153 ✅

import java.util.*;

public class ArmstrongNumbers {
    public static void main(String[] args) {
        System.out.println("3-digit Armstrong numbers:");

        // Loop through all 3-digit numbers
        for (int i = 100; i < 1000; i++) {
            if (isArmstrong(i)) {           // Check if number is Armstrong
                System.out.print(i + " ");  // Print if true
            }
        }
    }

    // 🌸 Method to check if a number is Armstrong
    static boolean isArmstrong(int n) {
        int original = n;   // store original number
        int sum = 0;        // sum of cubes of digits

        // calculate sum of cubes of each digit
        while (n > 0) {
            int rem = n % 10;           // get last digit
            sum += rem * rem * rem;     // add cube to sum
            n /= 10;                     // remove last digit
        }

        // compare sum with original number
        return sum == original;
    }
}
```

---

### ✨ Sample Output (when run)

```
3-digit Armstrong numbers:
153 370 371 407
```

---


---

