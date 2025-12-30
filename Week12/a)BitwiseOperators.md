
---

## 🔹 Why Math + Bits Matter (Kunal’s core point)

* DSA isn’t just “code” — it’s **logic + math**
* Even if you write Java / Python, the computer only understands **machine code**
* Machine code = **binary (0s and 1s)**
* So every:

  * number
  * character
  * instruction
    is internally converted to **bits**

👉 That’s why **bit manipulation** shows up everywhere in DSA & interviews.

---

## 🔹 Bitwise Operators (operate directly on bits)

### 1️⃣ Bitwise AND (`&`)

* Result bit is **1 only if both bits are 1**

```
1 & 1 = 1
1 & 0 = 0
0 & 1 = 0
0 & 0 = 0
```

Used for:

* checking odd/even
* masking bits

---

### 2️⃣ Bitwise OR (`|`)

* Result bit is **1 if at least one bit is 1**

```
1 | 1 = 1
1 | 0 = 1
0 | 1 = 1
0 | 0 = 0
```

---

### 3️⃣ Bitwise XOR (`^`)  ⭐ MOST IMPORTANT

* Result bit is **1 only if bits are different**

```
1 ^ 1 = 0
0 ^ 0 = 0
1 ^ 0 = 1
0 ^ 1 = 1
```

🔥 **Two golden properties (MEMORIZE):**

```
a ^ a = 0
a ^ 0 = a
```

Used for:

* finding unique number
* swapping without temp
* toggling bits

---

### 4️⃣ Bitwise Complement (`~`)

* Flips every bit

```
0 → 1
1 → 0
```

Used in:

* two’s complement (negative numbers)

---

## 🔹 Number Systems (Bases)

| System      | Base | Digits   |
| ----------- | ---- | -------- |
| Decimal     | 10   | 0–9      |
| Binary      | 2    | 0–1      |
| Octal       | 8    | 0–7      |
| Hexadecimal | 16   | 0–9, A–F |

👉 **Base = how many symbols available**

---

## 🔹 Number System Conversions

### ✅ Decimal → Base B

**Rule:**

* Divide by base B
* Store remainders
* Read remainders **bottom to top**

Example:
Decimal → Binary → divide by 2 repeatedly

---

### ✅ Base B → Decimal

**Rule:**

```
digit × base^position
```

* Position starts from **0 on the right**
* Add all values

---

## 🔹 Shift Operators (FAST math)

## 🔹 Left Shift (`<<`) — “move bits left”

### What happens

* Bits move **left**
* Zeros come in from the **right**
* Value **increases**

### Rule (just remember this)

```
a << b  =  a × 2^b
```

### Example

```
5 in binary = 101
5 << 1  → 1010
```

Binary `1010` = **10**

So:

```
5 << 1 = 10
```

One more:

```
5 << 2 = 20
```

👉 Every shift left = **multiply by 2**

---

## 🔹 Right Shift (`>>`) — “move bits right”

### What happens

* Bits move **right**
* Rightmost bits are **thrown away**
* Value **decreases**

### Rule

```
a >> b  =  a / 2^b
```

### Example

```
20 in binary = 10100
20 >> 1 → 1010
```

Binary `1010` = **10**

So:

```
20 >> 1 = 10
```

Another:

```
20 >> 2 = 5
```

👉 Every shift right = **divide by 2**

---

## 🔹 One-line memory hack

```
<<  multiply by 2
>>  divide by 2
```

---

## 🔹 Why people use shift instead of * or /

* Faster at machine level
* Used in DSA tricks
* Looks cool in interviews 😎

---

## 🔹 When NOT to overthink

If question says:

> “use bit manipulation”

Just think:

* Left shift → multiply
* Right shift → divide
