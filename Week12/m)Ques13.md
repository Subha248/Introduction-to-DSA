

## ❓ QUESTION

**Find `a^b` efficiently using bit manipulation.**
Example: **Calculate `5^3`**

---

## 🧠 IDEA (ONE LINE)

> Break the exponent into **binary**, keep squaring the base, and multiply **only when the bit is 1**.

---

## ✏️ STEP 1: Write the exponent in binary

```
b = 3
binary = 11
```

Meaning:

```
3 = 2 + 1
5^3 = 5^2 × 5^1
```

So we only need **5² and 5¹**.

---

## ✏️ STEP 2: Initialize variables

```
ans = 1      // collector
base = 5     // starts as 5^1
b = 3
```

---

## ✏️ STEP 3: Loop step-by-step (THIS IS THE CORE)

### 🔁 Iteration 1

```
b = 3 (binary 11)
last bit = 1
```

Bit is 1 → **we need this power**

```
ans = ans × base = 1 × 5 = 5
```

Prepare next power:

```
base = base × base = 5 × 5 = 25   // now 5^2
b = b >> 1 = 1
```

---

### 🔁 Iteration 2

```
b = 1 (binary 1)
last bit = 1
```

Bit is 1 → **we need this power**

```
ans = ans × base = 5 × 25 = 125
```

Prepare next power (not needed anymore but done anyway):

```
base = 25 × 25
b = b >> 1 = 0  → stop
```

---

## ✅ FINAL ANSWER

```
ans = 125
```

✔️ **5³ = 125**

---

## 💻 JAVA CODE (EXAM-READY)

```java
public class Main {
    public static void main(String[] args) {
        int a = 5;
        int b = 3;

        int ans = 1;
        int base = a;

        while (b > 0) {
            if ((b & 1) == 1) {
                ans *= base;
            }
            base *= base;
            b = b >> 1;
        }

        System.out.println(ans);
    }
}
```

---

## 🖨️ OUTPUT

```
125
```

---

## 🧠 REVISION CHEAT (READ THIS BEFORE EXAM)

* Binary of exponent tells **which powers to take**
* `base` becomes: `a¹ → a² → a⁴ → a⁸ ...`
* `ans` multiplies **only when bit = 1**
* Fast because loop runs **log b times**

---

## ⏱️ TIME COMPLEXITY — WHY IT’S FAST
We’re talking about **fast exponentiation (binary exponentiation)**.

### What actually repeats?

This loop:

```java
while (b > 0) {
    ...
    b = b >> 1;
}
```

Every iteration:

* `b` is **right-shifted**
* Right shift = **divide by 2**

So `b` becomes:

```
b → b/2 → b/4 → b/8 → ...
```

👉 How many times can you divide `b` by 2 until it becomes 0?
👉 **log₂(b) times**

### ✅ Time Complexity

```
O(log b)
```

### Compare with slow method:

| Method                        | Steps      |
| ----------------------------- | ---------- |
| Naive (a × a × a × … b times) | O(b) ❌     |
| Fast exponentiation           | O(log b) ✅ |

Example:

* `b = 1,000,000`
* Naive → 1,000,000 multiplications 😭
* Fast → ~20 iterations 😎

---

## 💾 SPACE COMPLEXITY — WHY IT’S LOW

What extra memory do we use?

Only:

```java
int ans;
int base;
int b;
```

* No arrays
* No recursion
* No extra data structures

👉 Constant number of variables.

### ✅ Space Complexity

```
O(1)
```

---

## 🧠 ONE-LINE EXAM ANSWER (MEMORISE THIS)

> “Since the exponent is halved in each iteration, the time complexity is O(log b). Only constant extra variables are used, so the space complexity is O(1).”

---

## 🔑 FINAL SNAPSHOT

* **Time:** `O(log b)` → because exponent is halved every loop
* **Space:** `O(1)` → only a few variables

That’s it. Clean. Clear. Exam-ready. 💯
