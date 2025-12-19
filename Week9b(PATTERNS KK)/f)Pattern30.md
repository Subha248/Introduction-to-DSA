

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
