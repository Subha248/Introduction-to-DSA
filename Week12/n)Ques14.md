

## Problem

Find the **XOR of all numbers from 0 to `a`**.

---

## Key Observation

The result depends only on the value of **`a % 4`**.

When numbers are XORed continuously, they repeat in a fixed cycle of **4**.

---

## Pattern

| Value of `a % 4` | XOR from `0` to `a` |
| ---------------- | ------------------- |
| 0                | `a`                 |
| 1                | `1`                 |
| 2                | `a + 1`             |
| 3                | `0`                 |

---

## Java Implementation

```java
public class Main {

    static int xorTillA(int a) {
        if (a % 4 == 0) return a;
        if (a % 4 == 1) return 1;
        if (a % 4 == 2) return a + 1;
        return 0;
    }

    public static void main(String[] args) {
        int a = 10;
        int result = xorTillA(a);
        System.out.println(result);
    }
}
```

---

## Example Output

For

```
a = 10
```

Calculation:

```
10 % 4 = 2
```

So result:

```
a + 1 = 11
```

### Output

```
11
```
---

## Example: XOR from 0 to 10

Numbers:

```
0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
```

---

### Step 1: XOR in small chunks (every 4 numbers)

We know XOR cancels itself every 4 numbers. Let’s see:

```
0 ⊕ 1 ⊕ 2 ⊕ 3 = 0    (because of the 4-number pattern)
4 ⊕ 5 ⊕ 6 ⊕ 7 = 0    (again cancels)
8 ⊕ 9 ⊕ 10 = ?
```

Now calculate the last part:

```
8 ⊕ 9 = 1    (binary: 100 ^ 101 = 001)
1 ⊕ 10 = 11  (binary: 001 ^ 1010 = 1011)
```

✅ So the final XOR from 0 to 10 = 11

---

### Step 2: Visualize pattern

| Number | Binary | XOR So Far  |
| ------ | ------ | ----------- |
| 0      | 0000   | 0           |
| 1      | 0001   | 0 ^ 1 = 1   |
| 2      | 0010   | 1 ^ 2 = 3   |
| 3      | 0011   | 3 ^ 3 = 0   |
| 4      | 0100   | 0 ^ 4 = 4   |
| 5      | 0101   | 4 ^ 5 = 1   |
| 6      | 0110   | 1 ^ 6 = 7   |
| 7      | 0111   | 7 ^ 7 = 0   |
| 8      | 1000   | 0 ^ 8 = 8   |
| 9      | 1001   | 8 ^ 9 = 1   |
| 10     | 1010   | 1 ^ 10 = 11 |

✅ Final XOR = **11**

---

### Step 3: Shortcut using `a % 4`

Now notice the **pattern**:

* XOR repeats every 4 numbers: 0,1,2,3 → then repeats.
* So you don’t need to calculate each step manually.

| a % 4 | XOR(0…a) |
| ----- | -------- |
| 0     | a        |
| 1     | 1        |
| 2     | a + 1    |
| 3     | 0        |

* For `a = 10` → 10 % 4 = 2 → XOR = 10 + 1 = **11**

---

### ✅ Summary (Visual Process)

1. Split numbers in **groups of 4**
2. Each group of 4 **cancels to 0**
3. XOR the remaining numbers (0 to `a % 4`)
4. Or just use formula: **if a % 4 == 2 → a + 1**

---

