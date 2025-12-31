
---

## **1️⃣ Total combinations in n bits**

* Each bit = 0 or 1 → 2 choices
* n bits → 2 × 2 × … n times = 2ⁿ combinations

**Example:** 8 bits → 2⁸ = 256 combinations

✅ These are **all the unique bit patterns** a computer can make.

---

## **2️⃣ Signed numbers: Using a sign bit**

* One bit (MSB) is reserved for **sign**:

  * `0` = positive
  * `1` = negative

* Remaining bits = **n-1 bits** for magnitude

**Example:** 8 bits → 1 sign bit + 7 magnitude bits → 7 bits for actual number value

* 7 bits → 2⁷ = 128 possible values for magnitude

---

## **3️⃣ Positive numbers**

* Positive numbers **start at 0**
* Maximum positive number = all remaining bits 1

**8-bit example:**

```
00000000 → 0
00000001 → 1
...
01111111 → 127
```

* Total positive numbers = 128 (includes zero)

---

## **4️⃣ Negative numbers**

* Negative numbers use **Two’s Complement**
* MSB = 1
* They don’t include zero

**8-bit example:**

```
10000000 → -128
10000001 → -127
...
11111111 → -1
```

* Total negative numbers = 128

✅ Notice: negative side goes one further than positive (-128 to -1)
✅ Total patterns = 128 + 128 = 256 → matches all 8-bit combinations

---

## **5️⃣ Formula for any n bits**

```
Range = -2^(n-1)  to  2^(n-1) - 1
```

* n = number of bits
* Left = smallest negative number
* Right = largest positive number

**Example (8-bit):**

```
-2^(8-1) → -128
2^(8-1)-1 → 127
```

---

## **6️⃣ Simple hotel analogy**

* 8 bits = 256 “rooms”
* Split into 2 wings: negative and positive
* Positive wing starts at 0 → goes 0 to 127
* Negative wing starts at -1 → goes -1 to -128
* Total rooms = 256

---

## **7️⃣ Quick summary table (8-bit)**

| Side     | Range    | Number of values |
| -------- | -------- | ---------------- |
| Negative | -128…-1  | 128              |
| Positive | 0…127    | 128              |
| Total    | -128…127 | 256 patterns     |

---

💡 **Key takeaway:**

* **Zero counts as positive**, so positive numbers max out at 2^(n-1)-1
* Negative numbers can use all 128 slots → min = -2^(n-1)
* Total = 2ⁿ combinations

---

