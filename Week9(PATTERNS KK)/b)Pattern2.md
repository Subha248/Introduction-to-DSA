
---

## Pattern Problem — 3-Step Approach (Standard Method)

### Pattern Type

Right-angled triangle using `*`

---

## **Approach 1: Number of Lines (Rows)**

* The **number of rows** decides how many times the **outer loop** runs.
* Here, `n = 4`, so we need **4 rows**.

```java
for (int i = 1; i <= n; i++)
```

👉 Each iteration of `i` represents **one row**.

---

## **Approach 2: Number of Columns in Each Row**

* The number of columns depends on the **current row number**.
* In row `i`, we print `i` columns.

```java
for (int j = 1; j <= i; j++)
```

👉 Columns increase as rows increase.

---

## **Approach 3: What to Print**

* For every column, print a star followed by a space.
* After completing one row, move to the next line.

```java
System.out.print("* ");
System.out.println();
```

---

## **Complete Code**

```java
public class Main {
    public static void main(String[] args) {
        pattern2(4);
    }

    public static void pattern2(int n) {
        for (int i = 1; i <= n; i++) {          // Approach 1: rows
            for (int j = 1; j <= i; j++) {      // Approach 2: columns
                System.out.print("* ");         // Approach 3: print
            }
            System.out.println();               // next line after each row
        }
    }
}
```

---

## **Output**

```
* 
* * 
* * * 
* * * * 
```

---

### **Key Rule (Remember This)**

* **Outer loop → rows**
* **Inner loop → columns**
* **Print statement → pattern**

This is the **base pattern logic**. Master this and 80% of pattern questions are already dead.
