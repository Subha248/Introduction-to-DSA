

---

## **Code: Sum of Digits**

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        int n = 1342;
        System.out.print(sum(n));
    }

    public static int sum(int n) {
        if (n == 0) return 0;
        return (n % 10) + sum(n / 10);
    }
}
```

---

## **Step 1: Understanding the logic**

We want **sum of digits** of a number `n`.

* **Last digit:** `n % 10` → gives the digit at the end.
* **Remaining number:** `n / 10` → removes the last digit.
* **Recursive step:** sum last digit + sum of remaining number.

**Base case:**

```java
if(n == 0) return 0;
```

* When `n` becomes 0, we stop recursion because there are **no digits left**.

---

## **Step 2: How the recursion works**

Let’s take `n = 1342`.

1. `sum(1342)`

   * Last digit: `1342 % 10 = 2`
   * Remaining: `1342 / 10 = 134`
   * Returns: `2 + sum(134)`

2. `sum(134)`

   * Last digit: `134 % 10 = 4`
   * Remaining: `134 / 10 = 13`
   * Returns: `4 + sum(13)`

3. `sum(13)`

   * Last digit: `13 % 10 = 3`
   * Remaining: `13 / 10 = 1`
   * Returns: `3 + sum(1)`

4. `sum(1)`

   * Last digit: `1 % 10 = 1`
   * Remaining: `1 / 10 = 0`
   * Returns: `1 + sum(0)`

5. `sum(0)`

   * Base case reached → returns 0

---

## **Step 3: Coming back up the stack**

Now the recursion **unwinds**:

```
sum(0) returns 0
sum(1) = 1 + 0 = 1
sum(13) = 3 + 1 = 4
sum(134) = 4 + 4 = 8
sum(1342) = 2 + 8 = 10
```

✅ Final answer = **10**

---

## **Step 4: Step-by-step “stack view”**

```
sum(1342) → waiting for sum(134)
sum(134)  → waiting for sum(13)
sum(13)   → waiting for sum(1)
sum(1)    → waiting for sum(0)
sum(0)    → returns 0
           ↑
sum(1)    → returns 1
           ↑
sum(13)   → returns 4
           ↑
sum(134)  → returns 8
           ↑
sum(1342) → returns 10
```

* Notice **nothing adds until recursion hits the base case**.
* Then **each paused call adds its digit** and returns it to the previous one.

---

## **Step 5: Key points to remember for revision**

1. **Base case**: `n == 0` → stops recursion.
2. **Recursive call**: `sum(n / 10)` → reduces the number by removing last digit.
3. **Combine result**: `n % 10 + sum(n / 10)` → adds current digit to sum of remaining digits.
4. **Stack behavior**: recursion builds going down, sums calculated coming up.
5. **Time complexity**: `O(log10 n)` → because each call removes one digit.

---

💡 **Extra tip:**

* For **product of digits**, it’s almost the same, but **base case** is `if (n % 10 == n) return n;` and you **multiply instead of add**.

---


Do you want me to do that?
