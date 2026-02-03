#WAY1: Using External Variable
---
```java
import java.util.*;

public class Main {

    static int sum = 0;

    public static void main(String[] args) {
        int n = 1234;
        reverse1(n);
        System.out.println(sum);
    }

    static void reverse1(int n) {
        if (n == 0) return;

        int rem = n % 10;
        sum = sum * 10 + rem;
        reverse1(n / 10);
    }
}
```

## 🌟 What this program does

It **reverses a number** using recursion.

If input is:

```
1234
```

Output will be:

```
4321
```

---

## 🧱 Structure of the Program

### 1️⃣ Class-level variable

```java
static int sum = 0;
```

This creates a variable that belongs to the **whole class**, not just one function.

Think of it like a **shared storage box** that every function in this class can use.

We use it to **build the reversed number**.

---

### 2️⃣ Main method (starting point)

```java
public static void main(String[] args) {
    int n = 1234;
    reverse1(n);
    System.out.println(sum);
}
```

Steps here:

1. Store number `1234` in variable `n`
2. Call the recursive function `reverse1(n)`
3. After recursion finishes, print the final value of `sum`

---

### 3️⃣ Recursive function

```java
static void reverse1(int n) {
    if (n == 0) return;

    int rem = n % 10;
    sum = sum * 10 + rem;
    reverse1(n / 10);
}
```

This function processes **one digit at a time**.

---

## 🔄 Step-by-step execution (n = 1234)

### 🧠 Key operations

* `n % 10` → gets last digit
* `n / 10` → removes last digit

---

### Call 1 → `reverse1(1234)`

* Last digit: `1234 % 10 = 4`
* Update sum: `0 * 10 + 4 = 4`
* Call `reverse1(123)`

---

### Call 2 → `reverse1(123)`

* Last digit: `3`
* Update sum: `4 * 10 + 3 = 43`
* Call `reverse1(12)`

---

### Call 3 → `reverse1(12)`

* Last digit: `2`
* Update sum: `43 * 10 + 2 = 432`
* Call `reverse1(1)`

---

### Call 4 → `reverse1(1)`

* Last digit: `1`
* Update sum: `432 * 10 + 1 = 4321`
* Call `reverse1(0)`

---

### Call 5 → `reverse1(0)`

Base case reached → function stops.

---

## 🧾 Final step back in `main`

Now `sum = 4321`, so:

```java
System.out.println(sum);
```

prints:

```
4321
```

---

## 🎯 Core Concept Summary

This program:
✔ Uses recursion to process digits one by one
✔ Uses `% 10` to take digits from right
✔ Uses `/ 10` to shrink the number
✔ Builds the reversed number in a shared variable (`sum`)

---

## 📌 One-line professional explanation

> The program reverses an integer by recursively extracting its digits and accumulating them into a class-level variable.

---
---
###WAY2: Pure Recursion (No external variable)
---
```java
import java.util.*;

public class Main {

    public static void main(String[] args) {
        int n = 1234;
        System.out.println(rev2(n));
    }

    static int rev2(int n) {
        int digits = (int)(Math.log10(n)) + 1;
        return helper(n, digits);
    }

    static int helper(int n, int digits) {
        if (n % 10 == n) return n;

        int rem = n % 10;
        return rem * (int)Math.pow(10, digits - 1)
                + helper(n / 10, digits - 1);
    }
}
```
