
---

### **Step 1: Understand the Pattern**

A magic number is **sum of powers of 5**. The powers you pick are **dictated by the binary representation of `n`**.

Example for clarity:

| n (decimal) | n (binary) | Magic Number Calculation | Magic Number |
| ----------- | ---------- | ------------------------ | ------------ |
| 1           | 001        | 5^1                      | 5            |
| 2           | 010        | 5^2                      | 25           |
| 3           | 011        | 5^2 + 5^1                | 30           |
| 4           | 100        | 5^3                      | 125          |
| 6           | 110        | 5^3 + 5^2                | 150          |

**Tip:** Binary bits are like switches: `1 = include this power of 5`, `0 = skip it`.

---

### **Step 2: How the Code Works**

```java
int ans = 0;
int base = 5;  // start with 5^1
while (n > 0) {
    int last = n & 1;    // check the last bit
    ans += last * base;  // add power of 5 if bit is 1
    base *= 5;           // move to next power of 5
    n = n >> 1;          // shift bits right to process next
}
System.out.print(ans);
```

**Walkthrough for n = 3:**

1. Binary of 3 = `11`
2. **First iteration:**

   * `last = 3 & 1 = 1`
   * `ans += 1 * 5 = 5`
   * `base = 5 * 5 = 25`
   * `n = 3 >> 1 = 1`
3. **Second iteration:**

   * `last = 1 & 1 = 1`
   * `ans += 1 * 25 = 30`
   * `base = 25 * 5 = 125`
   * `n = 1 >> 1 = 0`
4. Loop stops → **ans = 30** ✅

---

### **Step 3: Complexity**

* Only runs **as many times as there are bits in `n`** → `O(log n)` time.
* Very memory efficient → just two variables (`ans` and `base`).

---

### **Quick Analogy**

Think of each bit in `n` as a **switch for a magic weight**:

* Bit = 1 → put that power-of-5 weight in the box.
* Bit = 0 → skip it.
* After all switches checked → total weight = magic number.

---

