

## **Pattern28 — Centered Diamond (Stars)**

This code prints a **center-aligned diamond-like pattern** using stars.

---

## **Code**

```java
public class Pattern5 {
    public static void main(String[] args) {
        pattern28(4);
    }

    public static void pattern28(int n) {
        for (int i = 1; i < 2 * n; i++) {          // rows
            int c = i > n ? 2 * n - i : i;        // stars in current row
            int noOfSpaces = n - c;               // leading spaces

            for (int s = 0; s <= noOfSpaces; s++) {
                System.out.print(" ");
            }

            for (int j = 1; j <= c; j++) {
                System.out.print("* ");
            }

            System.out.println();                  // next row
        }
    }
}
```

---

## **Step 1: Number of Rows (Outer Loop)**

```java
for (int i = 1; i < 2 * n; i++)
```

* Total rows = `2*n - 1`
* For `n = 4` → **7 rows**
* First half → increasing stars
* Second half → decreasing stars

---

## **Step 2: Number of Stars in Each Row**

```java
int c = i > n ? 2 * n - i : i;
```

* If `i ≤ n` → stars increase (`c = i`)
* If `i > n` → stars decrease (`c = 2*n - i`)
* This forms the **diamond shape vertically**

---

## **Step 3: Number of Spaces Before Stars**

```java
int noOfSpaces = n - c;
```

* Spaces are used to **center-align** the stars
* As stars increase → spaces decrease
* As stars decrease → spaces increase

```java
for (int s = 0; s <= noOfSpaces; s++)
    System.out.print(" ");
```

> This prints **leading spaces before stars**

---

## **Step 4: Printing the Stars**

```java
for (int j = 1; j <= c; j++)
    System.out.print("* ");
```

* Prints `c` stars in each row
* Space after `*` keeps alignment neat

---

## **Dry Run (n = 4)**

| Row (i) | c (stars) | Spaces (n-c) | Output     |
| ------- | --------- | ------------ | ---------- |
| 1       | 1         | 3            | `  *`      |
| 2       | 2         | 2            | ` * *`     |
| 3       | 3         | 1            | `* * *`    |
| 4       | 4         | 0            | `* * * * ` |
| 5       | 3         | 1            | `* * *`    |
| 6       | 2         | 2            | ` * *`     |
| 7       | 1         | 3            | `  *`      |

---

## **Final Output**

```
    * 
   * * 
  * * * 
 * * * * 
  * * * 
   * * 
    * 
```

---

## **Professional Summary (3-Step Approach)**

1. **Rows** → `2*n - 1`
2. **Stars per row** → `c = i > n ? 2*n - i : i`
3. **Spaces per row** → `n - c`
4. **Print order** → spaces → stars → new line

---

### Why this logic is GOOD

* One loop handles **both halves**
* Clear math-based centering
* Scales cleanly for any `n`
* Exactly how **textbooks & interviews** expect diamond patterns

You’re officially in **advanced pattern territory** now.
