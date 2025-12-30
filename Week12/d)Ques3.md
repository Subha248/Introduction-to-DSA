
---

## 🎯 Goal

**Find the iᵗʰ bit of a number** (whether it’s `0` or `1`)

We’ll use:

* `<<` (left shift)
* `&` (AND)

---

## 🧮 Example (actual numbers)

### Number:

```
n = 13
```

Binary of 13:

```
13 = 1101
```

Let’s number the bits **from right to left** (important):

```
Position: 4 3 2 1
Bits:     1 1 0 1
```

---

## 🔍 Question

👉 **Find the 3rd bit of 13**

---

## STEP 1: Create the MASK

Formula:

```
1 << (i - 1)
```

Here:

```
i = 3
```

So:

```
1 << (3 - 1) = 1 << 2
```

Binary:

```
1      = 0001
1<<2   = 0100
```

Mask = **0100**

---

## STEP 2: AND the number with the mask

```
   n = 1101
mask = 0100
----------------
      0100
```

Result ≠ 0

---

## STEP 3: Interpret result

Since result is **non-zero**,
✅ **3rd bit is 1**

---

## 🧠 Try another one (same number)

### Find the **2nd bit of 13**

#### Mask:

```
1 << (2 - 1) = 1 << 1 = 0010
```

#### AND:

```
1101
0010
----
0000
```

Result = 0
❌ **2nd bit is 0**

---

## 🔑 One-line logic (burn this into memory)

```
n & (1 << (i - 1))
```

* result > 0 → bit is 1
* result = 0 → bit is 0

---

## 💡 Why this works (no overthinking)

* `1` keeps the bit as it is
* `0` kills the bit
* Mask has **only one 1**
* So only that bit survives

---

## 🪟 Window analogy (in one line)

Mask = cardboard with one hole
Light visible → bit = 1
Dark → bit = 0

---

## 🚀 Final permission

> “Shift 1 → AND → check zero or not.”

