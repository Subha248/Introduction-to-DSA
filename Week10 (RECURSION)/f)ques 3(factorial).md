
---

# 📝 Factorial & Recursion — Revision Notes

## 1️⃣ What makes factorial a perfect recursion example?

Because it naturally breaks into **smaller versions of itself**.

```
5! = 5 × 4!
4! = 4 × 3!
3! = 3 × 2!
2! = 2 × 1!
1! = 1   (base case)
```

So the rule becomes:

```java
factorial(n) = n * factorial(n-1)
```

---

## 2️⃣ Why the base case is `n <= 1`

If you don’t stop at 1, it keeps going:

```
5 → 4 → 3 → 2 → 1 → 0 → -1 → -2 ...
```

And boom 💥 stack overflow again.

So we say:

```java
if (n <= 1) return 1;
```

That’s the **wall** that stops recursion.

---

## 3️⃣ How values move through the stack (MOST IMPORTANT PART)

Code:

```java
static int factorial(int n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}
```

Let’s trace `factorial(5)`.

### ⬇️ Going DOWN (calls stacking)

```
factorial(5) = 5 * factorial(4)
factorial(4) = 4 * factorial(3)
factorial(3) = 3 * factorial(2)
factorial(2) = 2 * factorial(1)
factorial(1) = 1   ← base case reached
```

Nothing multiplies yet — calls are just waiting.

---

### ⬆️ Coming UP (returns happening)

```
factorial(1) returns 1
factorial(2) = 2 * 1 = 2 → returns 2
factorial(3) = 3 * 2 = 6 → returns 6
factorial(4) = 4 * 6 = 24 → returns 24
factorial(5) = 5 * 24 = 120 → returns 120
```

---

## 4️⃣ Stack Visualization

```
factorial(5) waiting for factorial(4)
factorial(4) waiting for factorial(3)
factorial(3) waiting for factorial(2)
factorial(2) waiting for factorial(1)
factorial(1) returns 1
            ↑
factorial(2) returns 2
            ↑
factorial(3) returns 6
            ↑
factorial(4) returns 24
            ↑
factorial(5) returns 120
```

---

## 5️⃣ Why Return Type Must Be `int`

Earlier printing examples were:

```java
void fun(int n)
```

Because they just **printed**, no value needed later.

**Printing functions (`void`) just print — no value needed.**
**Factorial must pass the number back to the previous function in the stack.**
**Without return, `factorial(5)` wouldn’t know the result of `factorial(4)`, so multiplication fails.**

**Analogy:** Passing a ball up a line — each person multiplies their number and passes it back. Without return, the ball is lost.

So we must return an `int`.

---


## 6️⃣ Same Pattern for SUM

Just change `*` to `+`

```java
static int sum(int n) {
    if (n == 1) return 1;
    return n + sum(n - 1);
}
```

Example: `sum(5) = 5+4+3+2+1 = 15`

---

## 7️⃣ Product of Digits (same recursion idea)

For number `1342`:

```java
static int productOfDigits(int n) {
    if (n % 10 == n) return n;  // single digit left
    return (n % 10) * productOfDigits(n / 10);
}
```

Breaks like:

```
1342 → 2 * product(134)
134  → 4 * product(13)
13   → 3 * product(1)
1    → base case
```

Result = `1×3×4×2 = 24`

---

## 8️⃣ Final Mental Model

Every recursion problem has **3 parts**:

1. **What is the smallest version?** → Base case
2. **How to shrink the problem?** → Recursive call
3. **What to do with the result?** → Combine step (print, multiply, add, etc.)

Factorial = **multiply while coming back up the stack**

You’re officially past beginner recursion now. This is the foundation for trees, backtracking, dynamic programming later on 👀

---

