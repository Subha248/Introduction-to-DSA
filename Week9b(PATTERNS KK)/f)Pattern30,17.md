

---

## **Pattern30 — Centered Palindromic Number Pyramid**

This pattern prints a **center-aligned pyramid** where numbers **decrease to 1** and then **increase back**, forming a palindrome in each row.

---

## **Code**

```java
public class Pattern30 {
    public static void main(String[] args) {
        pattern30(4);
    }

    public static void pattern30(int n) {
        for (int row = 1; row <= n; row++) {

            // spaces
            for (int s = 1; s <= n - row; s++) {
                System.out.print("  ");   // double space for alignment
            }

            // decreasing numbers
            for (int col = row; col >= 1; col--) {
                System.out.print(col + " ");
            }

            // increasing numbers
            for (int col = 2; col <= row; col++) {
                System.out.print(col + " ");
            }

            System.out.println();          // next row
        }
    }
}
```

---

## **Step 1: Number of Rows (Outer Loop)**

```java
for (int row = 1; row <= n; row++)
```

* Controls the **number of rows**
* For `n = 4` → **4 rows**
* Each iteration prints **one complete line**

---

## **Step 2: Leading Spaces (Center Alignment)**

```java
for (int s = 1; s <= n - row; s++)
    System.out.print("  ");
```

* Spaces decrease as row increases
* Double space `"  "` is used to match number width
* This centers the pyramid

---

## **Step 3: Left Half (Decreasing Numbers)**

```java
for (int col = row; col >= 1; col--)
```

* Prints numbers from `row` down to `1`
* Forms the **left side** of the palindrome

Example for `row = 4`:

```
4 3 2 1
```

---

## **Step 4: Right Half (Increasing Numbers)**

```java
for (int col = 2; col <= row; col++)
```

* Starts from `2` to avoid repeating `1`
* Prints numbers increasing back to `row`
* Completes the **palindromic shape**

Example:

```
2 3 4
```

---

## **Dry Run (n = 4)**

### Row-wise breakdown:

| Row | Spaces | Left Part | Right Part | Output          |
| --- | ------ | --------- | ---------- | --------------- |
| 1   | 3      | 1         | –          | `      1`       |
| 2   | 2      | 2 1       | 2          | `    2 1 2`     |
| 3   | 1      | 3 2 1     | 2 3        | `  3 2 1 2 3`   |
| 4   | 0      | 4 3 2 1   | 2 3 4      | `4 3 2 1 2 3 4` |

---

## **Final Output**

```
      1 
    2 1 2 
  3 2 1 2 3 
4 3 2 1 2 3 4 
```

---

## **Professional Summary (3-Approach Mapping)**

1. **Rows** → `row = 1 to n`
2. **Spaces** → `n - row`
3. **Pattern content**

   * Left → decreasing numbers
   * Right → increasing numbers (without repeating 1)

---

### Why this solution is **excellent**

* Clear separation of **spacing**, **left half**, and **right half**
* Perfect symmetry
* Very readable and **exam-ready**
* Works for any `n`

You’re now doing **advanced pattern composition**, not beginner stuff anymore.
---
---
### **Pattern17— Diamond-Shaped Palindromic Number Pattern**

**Output for `n = 4`:**

```
      1 
    2 1 2 
  3 2 1 2 3 
4 3 2 1 2 3 4 
  3 2 1 2 3 
    2 1 2 
      1 
```

---

## **Simple Explanation (Clean & Professional)**

This pattern prints a **center-aligned diamond** where:

* Numbers **decrease to 1** and then **increase back** (palindrome)
* The pattern **grows** till the middle row, then **shrinks**

---

## **Code**

```java
public class Pattern17{
    public static void main(String[] args) {
        pattern17(4);
    }

    public static void pattern17(int n) {
        for (int row = 1; row < 2 * n; row++) {
            int c = row > n ? 2 * n - row : row;

            // spaces
            for (int s = 1; s <= n - c; s++) {
                System.out.print("  ");
            }

            // decreasing numbers
            for (int col = c; col >= 1; col--) {
                System.out.print(col + " ");
            }

            // increasing numbers
            for (int col = 2; col <= c; col++) {
                System.out.print(col + " ");
            }

            System.out.println();
        }
    }
}
```

---

## **How It Works (3-Step Approach)**

### **1️⃣ Rows**

```java
for (int row = 1; row < 2 * n; row++)
```

* Total rows = `2*n - 1`
* For `n = 4` → **7 rows**
* Upper half grows, lower half shrinks

---

### **2️⃣ Columns / Numbers Count**

```java
int c = row > n ? 2 * n - row : row;
```

* `c` decides:

  * how many numbers to print
  * which number to start from
* Before middle → `c = row`
* After middle → `c = 2*n - row`

---

### **3️⃣ What to Print**

* **Spaces** → `n - c` (for centering)
* **Left side** → numbers from `c` down to `1`
* **Right side** → numbers from `2` up to `c`
* This avoids repeating `1` and keeps symmetry

---

## **Quick Dry Run (n = 4)**

| Row | c | Spaces | Numbers         |
| --- | - | ------ | --------------- |
| 1   | 1 | 3      | `1`             |
| 2   | 2 | 2      | `2 1 2`         |
| 3   | 3 | 1      | `3 2 1 2 3`     |
| 4   | 4 | 0      | `4 3 2 1 2 3 4` |
| 5   | 3 | 1      | `3 2 1 2 3`     |
| 6   | 2 | 2      | `2 1 2`         |
| 7   | 1 | 3      | `1`             |

---

## **In One Line**

* **Rows** → `2*n - 1`
* **Spaces** → `n - c`
* **Numbers** → palindrome from `c` to `1` to `c`
