
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

---

## **Pattern4 — Increasing Numbers Triangle**

### **Code**

```java
public class Main {
    public static void main(String[] args) {
        pattern3(4);
    }

    static void pattern4(int n) {
        for (int row = 1; row <= n; row++) {         // rows
            for (int col = 1; col <= row; col++) {   // columns
                System.out.print(col + " ");         // print column number
            }
            System.out.println();                     // move to next row
        }
    }
}
```

---

## **Step 1: Rows (Outer Loop)**

```java
for (int row = 1; row <= n; row++)
```

* Outer loop runs `n` times → 4 rows.
* Each iteration corresponds to **one line of output**.

---

## **Step 2: Columns (Inner Loop)**

```java
for (int col = 1; col <= row; col++)
```

* Number of columns in each row = **row number**
* Row 1 → 1 column
* Row 2 → 2 columns
* Row 3 → 3 columns
* Row 4 → 4 columns

---

## **Step 3: What to Print**

```java
System.out.print(col + " ");
```

* Prints **the column number** instead of `*`.
* `System.out.println()` moves to the next row after each inner loop.

---

## **Output (n = 4)**

```
1 
1 2 
1 2 3 
1 2 3 4 
```

---

### **Summary**

1. Outer loop → controls rows
2. Inner loop → controls columns (depends on current row)
3. Print → shows **column index** for pattern
4. Logic → forms a **number-increasing triangle**

---


