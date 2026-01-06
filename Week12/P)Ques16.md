
---

# **LeetCode Problem: 832. Flipping an Image**

**Problem Statement:**

> Given an `n x n` binary matrix `image`, first **flip the image horizontally**, then **invert it**, and return the resulting image.
>
> * **Flip horizontally**: Reverse each row.
> * **Invert**: Replace all 0s with 1s and all 1s with 0s.

**Example Input:**

```
image = [
 [1,0,0],
 [0,1,1],
 [1,1,0]
]
```

**Expected Output:**

```
[
 [1,1,0],
 [0,0,1],
 [1,0,0]
]
```

---

# **Java Code (with combined flip + invert in one loop)**

```java
class Solution {
    public int[][] flipAndInvertImage(int[][] image) {
        int n = image.length; // number of rows (also columns since n x n)

        // Loop through each row
        for (int i = 0; i < n; i++) {
            int start = 0;
            int end = image[i].length - 1; // last index of row

            // Swap and invert
            while (start <= end) {
                int temp = image[i][start] ^ 1;   // invert start
                image[i][start] = image[i][end] ^ 1; // invert end and assign to start
                image[i][end] = temp;             // assign inverted start to end
                start++;
                end--;
            }
        }

        return image;
    }
}
```

---

# **Dry Run (Step by Step)**

### **Initial Image:**

```
Row 0: 1 0 0
Row 1: 0 1 1
Row 2: 1 1 0
```

---

## **Step 1: First row `[1,0,0]`**

* `start = 0`, `end = 2`

**Iteration 1: start = 0, end = 2**

```java
temp = image[0][0] ^ 1 = 1 ^ 1 = 0
image[0][0] = image[0][2] ^ 1 = 0 ^ 1 = 1
image[0][2] = temp = 0
```

Row now: `[1,0,0]` ✅

* Move pointers: `start = 1`, `end = 1`

**Iteration 2: start = 1, end = 1 (middle element)**

```java
temp = image[0][1] ^ 1 = 0 ^ 1 = 1
image[0][1] = image[0][1] ^ 1 = 0 ^ 1 = 1
image[0][1] = temp = 1
```

Row after processing: `[1,1,0]` ✅

---

## **Step 2: Second row `[0,1,1]`**

* `start = 0`, `end = 2`

**Iteration 1: start = 0, end = 2**

```java
temp = image[1][0] ^ 1 = 0 ^ 1 = 1
image[1][0] = image[1][2] ^ 1 = 1 ^ 1 = 0
image[1][2] = temp = 1
```

Row now: `[0,1,1]` ✅

* Move pointers: `start = 1`, `end = 1`

**Iteration 2: start = 1, end = 1**

```java
temp = image[1][1] ^ 1 = 1 ^ 1 = 0
image[1][1] = image[1][1] ^ 1 = 1 ^ 1 = 0
image[1][1] = temp = 0
```

Row after processing: `[0,0,1]` ✅

---

## **Step 3: Third row `[1,1,0]`**

* `start = 0`, `end = 2`

**Iteration 1: start = 0, end = 2**

```java
temp = image[2][0] ^ 1 = 1 ^ 1 = 0
image[2][0] = image[2][2] ^ 1 = 0 ^ 1 = 1
image[2][2] = temp = 0
```

Row now: `[1,1,0]` ✅

* Move pointers: `start = 1`, `end = 1`

**Iteration 2: start = 1, end = 1**

```java
temp = image[2][1] ^ 1 = 1 ^ 1 = 0
image[2][1] = image[2][1] ^ 1 = 1 ^ 1 = 0
image[2][1] = temp = 0
```

Row after processing: `[1,0,0]` ✅

---

## **Step 4: Final Image**

```
[
 [1,1,0],
 [0,0,1],
 [1,0,0]
]
```

✅ Correct output!

---

# **Step 5: Explanation of Each Line in Code**

| Line                                       | What it does                                            |
| ------------------------------------------ | ------------------------------------------------------- |
| `int n = image.length;`                    | Gets number of rows (and columns, since square matrix)  |
| `for (int i=0; i<n; i++)`                  | Loops through each row                                  |
| `int start = 0, end = image[i].length -1;` | Pointers to first and last element of the row           |
| `while(start <= end)`                      | Swap until pointers meet/cross (handles middle element) |
| `int temp = image[i][start] ^ 1;`          | Store **inverted start element** in temp                |
| `image[i][start] = image[i][end] ^ 1;`     | Replace start with **inverted end**                     |
| `image[i][end] = temp;`                    | Replace end with **inverted start** (temp)              |
| `start++; end--;`                          | Move pointers inward                                    |
| `return image;`                            | Return the flipped + inverted 2D array                  |

---

# ✅ **Key Notes**

1. `^1` → flips 0 ↔ 1
2. `start <= end` → ensures **middle element of odd-length rows is inverted**
3. Flipping + inverting in **one pass** → efficient, O(n²) time, O(1) extra space

---

