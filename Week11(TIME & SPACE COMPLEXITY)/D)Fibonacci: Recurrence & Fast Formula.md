
---

## 1️⃣ Linear Recurrence Relation (LRR)

* **Meaning:** Each term depends on previous terms.
* **Example:** Fibonacci
  [
  f(n) = f(n-1) + f(n-2)
  ]

  * Depends on **2 previous terms** → second-order recurrence.

💡 Memory: *“Next = sum of previous”*

---

## 2️⃣ Solving Homogeneous Linear Recurrence

**Step-by-step:**

1. **Assume:**
   [
   f(n) = \alpha^n
   ]
   (just pretend solution is an exponential)
2. **Plug in:** Turn the recurrence into a **characteristic equation**

   * Fibonacci:
     (\alpha^2 - \alpha - 1 = 0)
3. **Solve roots:**
   [
   \alpha_1 = \frac{1+\sqrt{5}}{2}, \quad \alpha_2 = \frac{1-\sqrt{5}}{2}
   ]
4. **General solution:**
   [
   f(n) = c_1 \alpha_1^n + c_2 \alpha_2^n
   ]
5. **Repeated roots:** If roots same → use:
   [
   f(n) = c_1 \alpha^n + c_2 n \alpha^n
   ]

💡 Memory: *“Exponential roots + constants = general solution”*

---

## 3️⃣ Finding c₁ and c₂ (base cases)

* Use base cases (f(0) = 0), (f(1) = 1)

1. (f(0) = c_1 + c_2 = 0 \implies c_2 = -c_1)
2. (f(1) = c_1 \alpha_1 + c_2 \alpha_2 = 1)

   * Plug (c_2 = -c_1) → (c_1(\alpha_1 - \alpha_2) = 1)
   * (\alpha_1 - \alpha_2 = \sqrt{5} \implies c_1 = 1/\sqrt{5}, c_2 = -1/\sqrt{5})

💡 Memory: *“f(0) fixes sum, f(1) fixes difference”*

---

## 4️⃣ Fibonacci Formula (Golden Ratio)

* **Formula:**
  [
  f(n) = \frac{1}{\sqrt{5}} \Big[ (\frac{1+\sqrt{5}}{2})^n - (\frac{1-\sqrt{5}}{2})^n \Big]
  ]
* ((1+\sqrt{5})/2 ≈ 1.618) → Golden Ratio
* ((1-\sqrt{5})/2 ≈ -0.618) → tiny, goes to 0 fast
* **Time complexity if using formula:** (O(1))

💡 Memory: *“Golden Ratio = instant Fibonacci”*

---

## 5️⃣ Code Versions

### **A. Formula (fast)**

```java
static int fiboFormula(int n) {
    return (int)(Math.pow((1+Math.sqrt(5))/2, n)/Math.sqrt(5));
}
```

* Only uses α₁ → okay for **small n**
* ⚠️ For big n → slightly wrong because it **ignores α₂**

**Correct full formula:**

```java
static long fiboFormula(int n) {
    double phi = (1 + Math.sqrt(5)) / 2;
    double psi = (1 - Math.sqrt(5)) / 2;
    return Math.round((Math.pow(phi, n) - Math.pow(psi, n)) / Math.sqrt(5));
}
```

✅ Works for **any n**, exact Fibonacci numbers

---

### **B. Recursive Fibonacci (slow)**

```java
static int fibo(int n) {
    if (n < 2) return n;
    return fibo(n-1) + fibo(n-2);
}
```

* Simple recursion → **exponential time** (O(2^n))
* Fine for small n, horrible for large n

💡 Memory: *“Recursion = slow, formula = fast”*

---

## 6️⃣ Key Takeaways

1. **Recurrence** → term depends on previous
2. **Solve with characteristic roots** → get α₁, α₂
3. **c₁, c₂** → use base cases
4. **Golden Ratio formula** → instant Fibonacci, O(1)
5. **Recursion** → slow, O(2^n)

---
