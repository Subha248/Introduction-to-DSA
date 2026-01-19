

# 🌟 Euclidean Algorithm / GCD — The Ultimate Cheat-Sheet

---

## 1️⃣ The Formula (the magic line)

```
GCD(a, b) = GCD(b % a, a)
```

* `%` = remainder after dividing `b` by `a`
* Keep going until remainder = 0
* Last non-zero number = GCD

---

## 2️⃣ Step-by-step Process (no math drama)

1. Take **bigger number `b`** and **smaller number `a`**
2. Find remainder: `r = b % a`
3. Replace `(b, a)` → `(a, r)`
4. Repeat until `r = 0`
5. GCD = `a` (last non-zero number)

> **Basically:** Keep taking remainder until one number hits 0 → last number = GCD.

---
---

## 3️⃣ Why This Works (Intuition Only) — With Example

**Formula:**

```
b % a = b − (b // a) * a
```

* `%` just means **take remainder after subtracting multiples of `a` from `b`**
* **GCD doesn’t change** because multiples of `a` don’t add new common factors
* Numbers get smaller → easier to compute

---

### Example: `GCD(224, 105)`

#### Step 1: Apply remainder formula

```
b = 224, a = 105
b % a = 224 − (224 // 105) * 105
224 // 105 = 2
224 − 2*105 = 224 − 210 = 14
```

✅ Remainder = 14 → next step: `GCD(105, 14)`

---

#### Step 2:

```
b = 105, a = 14
b % a = 105 − (105 // 14) * 14
105 // 14 = 7
105 − 7*14 = 105 − 98 = 7
```

✅ Remainder = 7 → next step: `GCD(14, 7)`

---

#### Step 3:

```
b = 14, a = 7
b % a = 14 − (14 // 7) * 7
14 // 7 = 2
14 − 2*7 = 14 − 14 = 0
```

✅ Remainder = 0 → base case reached → **GCD = 7**

---

### Key Takeaways

* `%` = subtract multiples of `a` until leftover
* The leftover (remainder) **still contains the same factors**
* That’s why **GCD stays the same**
* Numbers get smaller → algorithm finishes fast

---
### The “same” part. Let me break it down **super clearly**.

---

### Why the GCD “stays the same”

We are doing this step repeatedly:

```
GCD(a, b) = GCD(b % a, a)
```

* `%` = remainder = `b − (b // a) * a`
* So we are literally doing: **subtract multiples of `a` from `b`**

---

#### Step-by-step with factors

Example: `GCD(224, 105)`

1. **Original numbers**:

   * 224 = 2 × 2 × 2 × 2 × 2 × 7
   * 105 = 3 × 5 × 7

**Common factors = 7** → GCD = 7

2. **Take remainder**: `224 % 105 = 14`

   * 14 = 2 × 7
   * Now we do `GCD(105, 14)`

**Check common factors**:

* 105 = 3 × 5 × 7
* 14 = 2 × 7
* Common factor still = 7 ✅

> See? Subtracting multiples of 105 didn’t remove the 7 — the **common factor is still there**.

3. Next remainder: `105 % 14 = 7`

* 14 = 2 × 7
* 7 = 7
* Common factor still = 7 ✅

4. Finally `14 % 7 = 0` → GCD = 7

---

### TL;DR / Goldfish version

* Every time you do `b % a`, you **only remove multiples of `a`**
* That **cannot remove the common factor** between `a` and `b`
* So the **GCD stays the same**, just smaller numbers → faster calculation

---
---
### EXPLANATION


### Example: `GCD(224, 105)`

#### Step 0: Start

```
a = 224, b = 105
```

**Formula:** `GCD(a, b) = GCD(b % a, a)`

* Plug in: `GCD(224, 105) = GCD(105 % 224, 224)`
* 105 % 224 = 105 (because 105 < 224)
* So next step: `GCD(105, 224)` ✅

> Notice we **always put the smaller number first as b % a**, that’s why initial swap happens naturally.

---

#### Step 1

```
a = 105, b = 224
```

* `GCD(a, b) = GCD(b % a, a)` → `GCD(224 % 105, 105)`
* 224 % 105 = 14
* Next step: `GCD(14, 105)`

---

#### Step 2

```
a = 14, b = 105
```

* `GCD(105 % 14, 14)`
* 105 % 14 = 7
* Next step: `GCD(7, 14)`

---

#### Step 3

```
a = 7, b = 14
```

* `GCD(14 % 7, 7)`
* 14 % 7 = 0
* Next step: `GCD(0, 7)` ✅

---

#### Step 4: Base case

```
GCD(0, 7) = 7
```

* The **formula stops when the first number becomes 0**
* The **GCD is the other number** → 7 ✅

---

### ✅ Key Takeaways

1. **Yes**, the final pair will look like `(0, GCD)` — that’s normal.
2. **The GCD is always the non-zero number**.
3. If you follow the formula **exactly**, the sequence of pairs is:

```
(224, 105) → (105, 224) → (14, 105) → (7, 14) → (0, 7)
```

---
The one you ACTUALLY need is:

# ✅ **EUCLIDEAN ALGORITHM (REMAINDER METHOD)**

That’s the official name.
That’s the one every coder uses.
That’s the one DSA teachers expect.
That’s the one interviewers expect.
That’s the FAST one.

---

### 📌 Formula (the only one you need)

```
GCD(a, b) = GCD(b, a % b)
```

Keep doing it until remainder becomes **0**.

---

### 📌 Example (clean + simple)

Find **GCD(42, 30)**

1️⃣ `42 % 30 = 12`
→ GCD(42,30) = GCD(30,12)

2️⃣ `30 % 12 = 6`
→ GCD(30,12) = GCD(12,6)

3️⃣ `12 % 6 = 0`
→ GCD(12,6) = GCD(6,0)

🎉 **Answer = 6**

---

### 📌 ONE-LINE MEMORY TRICK

> “Keep dividing till remainder dies. The survivor is GCD.”

---


