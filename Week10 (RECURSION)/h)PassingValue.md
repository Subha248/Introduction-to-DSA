
---

## 🧾 Your Code

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        fun(5);
    }

    public static void fun(int n) {
        if (n == 0) return;

        System.out.println(n);

        fun(--n);
    }
}
```

---

## 🎯 What This Program Does

It prints numbers from **5 down to 1** using **recursion**.

Output:

```
5
4
3
2
1
```

---

## 🧠 Step-by-Step Explanation

### 🔹 `main()` method

```java
fun(5);
```

Program starts here and calls the function `fun` with **n = 5**.

---

## 🔁 Inside the Recursive Function

```java
public static void fun(int n)
```

This function keeps calling itself with a smaller number until it reaches **0**.

---

### 1️⃣ Base Case (Stopping Condition)

```java
if (n == 0) return;
```

This is the **exit door** 🚪
When `n` becomes 0, the function stops calling itself.

Without this → **infinite recursion → stack overflow**

---

### 2️⃣ Print Current Value

```java
System.out.println(n);
```

Whatever `n` is right now, it gets printed.

---

### 3️⃣ Recursive Call

```java
fun(--n);
```

This is the important part.

`--n` means:

> Decrease `n` FIRST, then send it to the next function call.

So the value actually passed is **one less than current n**.

---

## 🔄 Full Flow of Calls

Let’s trace it:

```
fun(5) → prints 5 → calls fun(4)
fun(4) → prints 4 → calls fun(3)
fun(3) → prints 3 → calls fun(2)
fun(2) → prints 2 → calls fun(1)
fun(1) → prints 1 → calls fun(0)
fun(0) → base case hit → stops
```

---

## ⚠️ Why `--n` Works Here

Because it **reduces the value before passing**.

If you had written:

```java
fun(n--);  // ❌ WRONG
```

Then Java would:

1. Send **current value**
2. Reduce later

So `fun(5)` would keep calling `fun(5)` forever 💀

---

## ✅ Final Concept Summary (For Revision)

✔ Recursion = function calling itself
✔ Needs a **base case** to stop
✔ Each call must move **closer to base case**
✔ `--n` reduces before passing
✔ `n--` passes first, reduces later (danger in recursion)
✔ Safer alternative: `fun(n - 1)`

---

