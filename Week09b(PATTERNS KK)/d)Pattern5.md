
---

## **Pattern5 — Increasing then Decreasing Stars (One-Based)**

### **Code**

```java
public class Pattern5 {
    public static void main(String[] args) {
        pattern5(5);
    }

    public static void pattern5(int n) {
        for (int i = 1; i < 2 * n; i++) {          // rows
            int c = i > n ? 2 * n - i : i;        // stars in current row
            for (int j = 1; j <= c; j++) {        // print stars
                System.out.print("* ");
            }
            System.out.println();                  // move to next row
        }
    }
}
```

---

## **Step 1: Number of Rows (Outer Loop)**

```java
for (int i = 1; i < 2 * n; i++)
```

* **Outer loop** controls **rows**.
* Runs from `i = 1` to `i = 2*n - 1` → total rows = `2*n - 1`.
* Example: `n = 5` → rows = 9

**Reasoning:**

* First `n` rows → stars increase
* Last `n-1` rows → stars decrease

---

## **Step 2: Number of Stars in Each Row**

```java
int c = i > n ? 2 * n - i : i;
```

* **Logic explained:**

  * If `i <= n` → row in **upper half** → stars = row number (`c = i`)
  * If `i > n` → row in **lower half** → stars decrease → `c = 2*n - i`

**Example for n = 5:**

| Row (i) | c = ? | Stars printed |
| ------- | ----- | ------------- |
| 1       | 1     | *             |
| 2       | 2     | * *           |
| 3       | 3     | * * *         |
| 4       | 4     | * * * *       |
| 5       | 5     | * * * * *     |
| 6       | 4     | * * * *       |
| 7       | 3     | * * *         |
| 8       | 2     | * *           |
| 9       | 1     | *             |

---

## **Step 3: Inner Loop — Printing Stars**

```java
for (int j = 1; j <= c; j++)
    System.out.print("* ");
```

* Prints exactly **c stars** for the current row.
* After finishing stars for a row, `System.out.println()` moves to the next row.

---

## **Step 4: Dry Run (n = 5)**

```
Row 1: * 
Row 2: * * 
Row 3: * * * 
Row 4: * * * * 
Row 5: * * * * * 
Row 6: * * * * 
Row 7: * * * 
Row 8: * * 
Row 9: * 
```

* **Pattern:** symmetric triangle (increasing → decreasing)

---

## **Professional Summary**

**Three-step pattern approach applied:**

1. **Outer loop → rows**

   * `for (i = 1; i < 2*n; i++)` → `2*n - 1` rows
2. **Inner loop → columns**

   * `c = i > n ? 2*n - i : i` → stars per row
3. **Print logic**

   * `for (j = 1; j <= c; j++) System.out.print("* ");`
   * `System.out.println();` → move to next row

**Why this is the best approach:**

* **One-based index → intuitive row numbering**
* **Formula for stars → simple ternary**
* **Works for any n** → scalable pattern

---
