https://leetcode.com/problems/search-a-2d-matrix-ii/
---
**PROBLEM 1,2**
# ** 1) Search in a Sorted Matrix (Your BS2D Code Explained)**

---

# ✅ **FULL CODE (YOURS, UNCHANGED)**

```java
import java.util.Arrays;

public class SARAN {
    public static void main(String[] args) {
        int[][] matrix = {
            {10, 20, 30, 40},
            {11, 22, 33, 45},
            {28, 29, 37, 46},
            {33, 34, 38, 50}
        };

        int target = 37;
        int[] result = BS2D(matrix, target);
        System.out.println(Arrays.toString(result));
    }

    public static int[] BS2D(int[][] matrix, int target) {
        int r = 0;  
        int c = matrix[0].length - 1; 

        while (r < matrix.length && c >= 0) {
            if (matrix[r][c] == target) return new int[]{r, c};

            if (matrix[r][c] > target) c--; 
            else r++; 
        }

        return new int[]{-1, -1};
    }
}
```

---

# 🔥 **NOW THE EXPLANATION (PROFESSIONAL + STRAIGHTFORWARD)**

---

## **1. Import**

```java
import java.util.Arrays;
```

– You need this to use `Arrays.toString()` for printing the result array.

---

## **2. Main Class**

```java
public class SARAN {
```

– Just the class name. Nothing fancy.

---

## **3. Matrix Initialization**

```java
int[][] matrix = {
    {10, 20, 30, 40},
    {11, 22, 33, 45},
    {28, 29, 37, 46},
    {33, 34, 38, 50}
};
```

This is a **sorted matrix**:

* Rows sorted left → right
* Columns sorted top → bottom

Classic LeetCode 2D search type.

---

## **4. Set target**

```java
int target = 37;
```

Self-explanatory.

---

## **5. Call Search Function**

```java
int[] result = BS2D(matrix, target);
```

This returns the **row and column** where target is found.

---

## **6. Print Result**

```java
System.out.println(Arrays.toString(result));
```

`result` is a **1D array**, so `toString()` is correct.

Output will be:

```
[2, 2]
```

---

# ⭐ **NOW THE CORE: Your BS2D Algorithm**

---

## **Step 1: Starting Position**

```java
int r = 0;
int c = matrix[0].length - 1;
```

You start at:

### 👉 **Top-right corner**

* `r = 0` → first row
* `c = last column`

Why top-right?
Because from here:

* Moving left → values get smaller
* Moving down → values get bigger

Perfect for binary-like search.

---

## **Step 2: Main Loop**

```java
while (r < matrix.length && c >= 0) {
```

Loop until:

* You fall below the last row (`r` too big), OR
* You go left past column 0 (`c` negative)

---

## **Step 3: Check if match**

```java
if (matrix[r][c] == target) return new int[]{r, c};
```

If we found the target → return its coordinates immediately.

---

## **Step 4: Move Left or Down**

```java
if (matrix[r][c] > target) 
    c--;      // move left
else 
    r++;      // move down
```

### Why this works:

* If the current value is **too big**, go left to find smaller numbers.
* If the current value is **too small**, go down to find larger numbers.

This keeps the search O(n), not O(n²).

---

## **Step 5: Not Found Case**

```java
return new int[]{-1, -1};
```

If loop ends → target isn't anywhere in matrix.

---

# 🎯 **TL;DR (in Gen Z style)**

* Start top-right
* Too big? go left
* Too small? go down
* Exact equal? return the coords
* Fall out of bounds? target doesn’t exist, rip

