
---

## **Pattern3 — Inverted Right-Angled Triangle**

### **Code Overview**

```java
public class Main {
    public static void main(String[] args) {
        pattern3(4);
    }

    static void pattern3(int n) {
        for (int row = 1; row <= n; row++) {              // rows
            for (int col = 1; col <= n + 1 - row; col++) { // columns 
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

---

## **Step 1: Number of Rows (Outer Loop)**

```java
for (int row = 1; row <= n; row++)
```

* `n = 4` → outer loop runs 4 times → 4 rows.
* Each iteration of `row` corresponds to **one line** of output.
* ✅ This is the **first key approach**: number of lines = number of rows = outer loop iterations.

---

## **Step 2: Number of Columns (Inner Loop)**

```java
for (int col = 1; col <= n + 1 - row; col++)
```

* Columns depend on the **current row number**:

  * Row 1 → 4 stars
  * Row 2 → 3 stars
  * Row 3 → 2 stars
  * Row 4 → 1 star
* Formula: `columns = n + 1 - row` → **classic inverted triangle logic**
* ✅ This is the **second key approach**: determine how many columns per row.

---

## **Step 3: What to Print**

```java
System.out.print("* ");
System.out.println();
```

* `System.out.print("* ")` → prints one star per column
* `System.out.println()` → moves to next row after finishing the columns
* ✅ This is the **third key approach**: decide what each element prints and manage line breaks.

---

## **Output (n = 4)**

```
* * * * 
* * * 
* * 
* 
```

---

## **Professional Summary**

1. **Outer loop** → controls **number of rows**
2. **Inner loop** → controls **number of columns per row**
3. **Print statement** → prints stars; `println()` moves to the next row
4. **Logic** → `columns = n + 1 - row` → natural formula for **inverted triangle**

* This code is **clean, readable, and exam/interview-friendly**.
* Using `row` starting from 1 makes it **intuitive to visualize** the pattern.

---

