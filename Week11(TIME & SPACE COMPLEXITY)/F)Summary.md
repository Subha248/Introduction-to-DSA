

---

# 🧠 WHAT IS TIME & SPACE COMPLEXITY (FROM SCRATCH)

## Step 0: WHY this even exists (MOST IMPORTANT)

Computers have **2 limits**:

1. **Time** (how long code runs)
2. **Memory** (how much space it eats)

👉 **Time complexity** = how much **work**
👉 **Space complexity** = how much **memory**

That’s the whole subject. No magic.

---

# ⏱️ TIME COMPLEXITY (WORK)

## What it ACTUALLY means

> “If input becomes BIG, how badly does my code suffer?”

NOT:
❌ seconds
❌ laptop speed
❌ RAM size

YES:
✅ growth pattern

---

## Think like this 👇

If input size = **n**

Ask:

> “How many times does my code run **because of n**?”

---

## CASE 1: Single loop

```java
for (int i = 0; i < n; i++) {
    // work
}
```

• Runs **n times**
• Work grows with n

👉 **Time = O(n)**

🧠 Memory hook:

> n items → n work

---

## CASE 2: Two nested loops

```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        // work
    }
}
```

• Inner loop runs **n** times
• Outer loop runs **n** times

👉 Total work = n × n = n²
👉 **Time = O(n²)**

🧠 Hook:

> loop inside loop = square pain

---

## CASE 3: Halving input (log n)

```java
while (n > 1) {
    n = n / 2;
}
```

• n becomes half every step
• Steps = log₂n

👉 **Time = O(log n)**

🧠 Hook:

> Cutting in half = log

---

## CASE 4: Fibonacci recursion (slow AF)

```java
fibo(n) = fibo(n-1) + fibo(n-2)
```

• Each call makes **2 more calls**
• Tree explodes

👉 **Time = exponential (O(2ⁿ))**

🧠 Hook:

> branching = disaster

---

# ❗ WHY WORST CASE ONLY?

Because:
• Best case = luck
• Average case = assumptions
• Worst case = **guarantee**

Example:
Linear search

Best: element first → O(1)
Worst: element last → **O(n)**

👉 Interview answer = **O(n)**

🧠 Tattoo:

> Worst case = safety promise

---

# 🧠 SPACE COMPLEXITY (MEMORY)

Now memory. Same reset.

---

## Think in BOXES 📦

### One variable

```java
int x;
```

👉 1 box → **O(1)**

---

### Multiple variables

```java
int a, b, c;
```

👉 Still constant → **O(1)**

---

## ARRAYS = MANY BOXES

```java
int[] arr = new int[n];
```

Memory:

```
arr[0] → 📦
arr[1] → 📦
...
arr[n-1] → 📦
```

👉 n elements = n boxes
👉 **Space = O(n)**

🧠 Hook:

> each element needs its own bed

---

## EXTRA array = EXTRA memory

```java
int[] copy = new int[n];
```

• Original array → ignored (input)
• New array → counted

👉 **Space = O(n)**

---

# 🔁 RECURSION SPACE (STACK)

This is where people panic. Relax.

### Recursive call = stack box 📦

Example:

```java
fibo(5)
```

Call stack:

```
fibo(5)
fibo(4)
fibo(3)
fibo(2)
fibo(1)
```

👉 Max calls at once = 5
👉 **Space = O(n)**

IMPORTANT:
❌ total calls don’t matter
✅ deepest chain matters

🧠 Hook:

> stack cares about height, not width

---

# 🔥 COMBINE TIME + SPACE

### Example 1: Binary Search

• Time = O(log n)
• Space = O(1) (iterative)

---

### Example 2: Merge Sort

• Time = O(n log n)
• Space = O(n) (extra array)

---

### Example 3: Recursive Fibonacci

• Time = exponential
• Space = O(n) (stack)

---

# 🎯 FINAL TATTOO LIST (MEMORISE THIS)

Say this in your head:

> **Time = how work grows**
> **Space = how memory grows**
> **Worst case always**
> **Big n only**
> **Ignore constants**
> **Keep biggest term**

---

## ONE LINE YOU SHOULD NEVER FORGET

> **Time complexity tells if code is fast.
> Space complexity tells if code fits in memory.**

