
---

## CORE IDEA (lock this first 🔒)

All these notations talk about **how fast time grows when input `n` becomes very large**.

---

## 1️⃣ Big O — **Upper Bound (Worst Case)**

**What it means**

* Maximum time an algorithm can take
* It **will NOT go beyond this**

**How to find it**

* Ignore constants → `3n²` → `O(n²)`
* Keep biggest term → `n³ + log n` → `O(n³)`

🧠 Head sentence:

> **Big O = “at most this slow”**

---

## 2️⃣ Big Omega (Ω) — **Lower Bound (Best Case)**

**What it means**

* Minimum time an algorithm must take
* It **cannot be faster than this**

Example from your text:

* If algo is `Ω(n³)`
  → it may be `n³`, `n⁴`, `n¹⁰`
  → but **never less than `n³`**

🧠 Head sentence:

> **Big Ω = “at least this slow”**

---

## 3️⃣ Big Theta (Θ) — **Tight Bound**

**What it means**

* Exact growth rate
* When **upper bound = lower bound**

Example:

* Upper bound = `n²`
* Lower bound = `n²`
* ⇒ **Θ(n²)**

🧠 Head sentence:

> **Θ = “exactly this growth”**

---

## QUICK 3-LINE MEMORY 🧠

* **O(n²)** → at most n²
* **Ω(n²)** → at least n²
* **Θ(n²)** → exactly n²

---

## 4️⃣ Little o — **Strict Upper Bound**

**What it means**

* Function grows **strictly slower**
* Not equal, always smaller

From your example:

* `n²` is `o(n³)`
* Because `n³` grows much faster

🧠 Head sentence:

> **Little o = “definitely smaller”**

---

## 5️⃣ Little Omega (ω) — **Strict Lower Bound**

**What it means**

* Function grows **strictly faster**
* Stronger than Big Ω

From your example:

* `n³` is `ω(n²)`
* Because `n³` dominates `n²`

🧠 Head sentence:

> **Little ω = “definitely bigger”**

---

## ONE TABLE TO REMEMBER (VERY IMPORTANT)

| Notation | Meaning in words |
| -------- | ---------------- |
| **O**    | at most          |
| **Ω**    | at least         |
| **Θ**    | exactly          |
| **o**    | strictly smaller |
| **ω**    | strictly bigger  |

---

## INTERVIEW-SAFE ONE-LINER 🔥

If stuck, say:

> “Big O gives the worst-case upper bound, Big Omega gives the best-case lower bound, and Big Theta gives the exact growth when both match.”

That’s **perfect** and matches your original text.

---
