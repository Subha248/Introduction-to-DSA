

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

## Summary (Quick Revision)

* XOR from `0` to `a` follows a **4-number cycle**
* Use `a % 4` to decide the result
* Time complexity: **O(1)**
* No loops required

