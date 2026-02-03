
---

# 🧩 PROBLEM

Count how many **0 digits** are inside a number.

Example:
`30204 → 2 zeros`

---

# 🔥 MAIN IDEA (THE SPECIAL PATTERN)

Instead of using a global variable, we:

✅ Put `count` **inside the function arguments**
✅ Update it while going **deeper** into recursion
✅ Return the **final count once**, and let it flow back up

This is called **passing state through recursion**.

---

# ✅ CODE

```java
static int count(int n) {
    return helper(n, 0); // Start with count = 0
}

static int helper(int n, int count) {
    if (n == 0) {
        return count; // Base case returns final answer
    }

    int rem = n % 10;

    if (rem == 0) {
        return helper(n / 10, count + 1); // Found a zero
    }

    return helper(n / 10, count); // Not a zero
}
```

---

# 🧠 STEP-BY-STEP EXECUTION (STACK FLOW)

We call:

```
count(30204)
→ helper(30204, 0)
```

Now recursion starts going **down the stack** ⬇

---

### 🔹 Call 1

`helper(30204, 0)`
Last digit = **4** → not zero
Next call:

```
helper(3020, 0)
```

---

### 🔹 Call 2

`helper(3020, 0)`
Last digit = **0** → zero found
Increase count:

```
helper(302, 1)
```

---

### 🔹 Call 3

`helper(302, 1)`
Last digit = **2** → not zero

```
helper(30, 1)
```

---

### 🔹 Call 4

`helper(30, 1)`
Last digit = **0** → zero found
Increase count:

```
helper(3, 2)
```

---

### 🔹 Call 5

`helper(3, 2)`
Last digit = **3** → not zero

```
helper(0, 2)
```

---

### 🔹 Call 6 — BASE CASE

`helper(0, 2)`

Now:

```java
if (n == 0) return count;
```

So it returns **2** 🎯

---

# 🔁 NOW STACK UNWINDS (GOING BACK UP)

Here’s the key thing Kunal stresses:

Every function call is written as:

```java
return helper(...)
```

So once the deepest call returns **2**, nobody changes it.
They all just **pass it back up**.

```
helper(0,2)  → returns 2
helper(3,2)  → returns 2
helper(30,1) → returns 2
helper(302,1) → returns 2
helper(3020,0) → returns 2
helper(30204,0) → returns 2
```

Finally:

```
count(30204) → returns 2
```

Printed in `main`.

---

# ⭐ VERY IMPORTANT CONCEPTS (DON’T MISS)

### ✅ 1. Count is NOT global

Each call has its **own copy** of `count`.
We pass updated values forward.

---

### ✅ 2. Base case happens ONLY ONCE

Only when `n == 0` do we actually produce the answer.

After that, recursion doesn’t calculate anything —
it just **returns the same value upward**.

---

### ✅ 3. This is a special recursion pattern

Used when you need to:

✔ Count things
✔ Track steps
✔ Accumulate values
✔ Pass extra info

Instead of building the answer on the way back up,
we **build it on the way down**.

---

# ⏱ TIME COMPLEXITY

Each step removes one digit:

```
n → n/10 → n/10 → n/10 ...
```

Number of digits = `log₁₀(n)`

So time complexity:

```
O(log n)
```

---

# 🧠 ONE-LINE MEMORY TRICK

**“We carry the answer downward, and return it unchanged upward.”**

That’s the whole pattern.

---



