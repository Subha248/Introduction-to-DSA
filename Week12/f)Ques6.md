
---

## **1️⃣ Two’s Complement: How Negatives Work**

Computers don’t have a “-” sign. They store negatives using **Two’s Complement**.

**Steps to get -n:**

1. Flip all bits of n → `~n`
2. Add 1

**Example: -5 in 8-bit**

```
+5 = 00000101
Flip bits → 11111010
Add 1     → 11111011
-5 = 11111011
```

✅ MSB (leftmost bit) = 1 → negative.
✅ This allows subtraction to become **addition** of Two’s Complement.

**Check Addition (+5 + -5):**

```
  00000101  (+5)
+ 11111011  (-5)
-------------
100000000  (9 bits, overflow discarded)
00000000 → 0 ✅
```

* The **extra bit overflows** because we only have 8 bits.
* Remaining bits = correct result: `0`.

**Shortcut memory tip:**

* MSB = 0 → positive
* MSB = 1 → negative

---

## **2️⃣ Rightmost Set Bit (`n & -n`)**

* Rightmost set bit = first 1 from the **right**.
* Formula: `n & -n`

**Why it works:**

1. -n is Two’s Complement of n → flips bits and adds 1.
2. This isolates the **first 1** from the right.

**Example: n = 12 (1100)**

```
n    = 1100
-n   = 0100 (Two’s Complement)
n & -n = 0100 ✅
```

* Only the **rightmost 1** stays.

**Memory trick:** `n & -n` = “mask” for the first 1 from the right.

---

## **3️⃣ “Odometer Roll-over” Analogy**

* Binary subtraction = odometer going backward.
* 0000 - 1 → 1111 (-1)
* Leftmost bit naturally = 1 → negative.

This is why Two’s Complement **automatically handles negative numbers and subtraction**.

---

### **4️⃣ Quick Cheat Sheet**

| Concept           | Formula              | What it Does                |
| ----------------- | -------------------- | --------------------------- |
| Rightmost set bit | `n & -n`             | Isolates first 1 from right |
| Negative number   | `~n + 1`             | Two’s Complement            |
| MSB               | Leftmost bit         | 0 = positive, 1 = negative  |
| Subtraction       | Add Two’s Complement | No extra logic needed       |

---

