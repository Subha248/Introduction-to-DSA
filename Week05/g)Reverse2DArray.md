### 2D array reversal program

We’ll use this array:

```java
int[][] arr = {
    {3, 2, 1},
    {6, 5, 4},
    {9, 8, 7},
};
```

---

## **Step 1: Program Start**

```java
public class Main {
    public static void main(String[] args) {
```

* Program starts execution.
* `main` is the entry point.

---

## **Step 2: Initialize the array**

```java
int[][] arr = {
    {3, 2, 1},
    {6, 5, 4},
    {9, 8, 7},
};
```

* Creates a **3x3 2D array** in memory:

```
Row 0: 3 2 1
Row 1: 6 5 4
Row 2: 9 8 7
```

---

## **Step 3: Get row and column counts**

```java
int row = arr.length;         // total number of rows
int col = arr[0].length;      // total number of columns in first row
```

* `row = 3` → number of rows
* `col = 3` → number of columns in a row

> ✅ Important: `arr.length - 1` would be **wrong**, because loops would skip the last row.

---

## **Step 4: Loop through each row**

```java
for(int i = 0; i < row; i++){
```

* Outer loop to process **each row** of the array.

### **Iteration 1:** `i = 0` → row 0 → `{3, 2, 1}`

---

### **Step 5: Initialize start and end pointers**

```java
int start = 0;
int end = col - 1;
```

* `start = 0` → first element of the row
* `end = 2` → last element of the row (`col - 1`)

**Pointers visual for row 0:**

```
start -> 3  2  1 <- end
```

---

### **Step 6: Swap using two pointers**

```java
while(start < end){
    int temp = arr[i][start];
    arr[i][start] = arr[i][end];
    arr[i][end] = temp;
    start++;
    end--;
}
```

* **Purpose:** Reverse the row **in-place** using `start` and `end`.

#### **Dry Run for Row 0: `{3,2,1}`**

| start | end | arr[i][start] | arr[i][end] | temp | Array After Swap    |
| ----- | --- | ------------- | ----------- | ---- | ------------------- |
| 0     | 2   | 3             | 1           | 3    | {1, 2, 3}           |
| 1     | 1   | 2             | 2           | -    | stop (start >= end) |

* **Final Row 0:** `{1, 2, 3}` ✅

**Pointer movement explanation:**

* First swap: first ↔ last element
* Move pointers inward: `start++`, `end--`
* When `start >= end`, row is fully reversed

---

### **Step 7: Next row: `i = 1` → row 1 → `{6,5,4}`**

* `start = 0`, `end = 2`

**Swap iterations:**

| start | end | Array Before | Array After Swap |
| ----- | --- | ------------ | ---------------- |
| 0     | 2   | {6,5,4}      | {4,5,6}          |
| 1     | 1   | {4,5,6}      | stop             |

* **Final Row 1:** `{4,5,6}` ✅

---

### **Step 8: Next row: `i = 2` → row 2 → `{9,8,7}`**

* `start = 0`, `end = 2`

**Swap iterations:**

| start | end | Array Before | Array After Swap |
| ----- | --- | ------------ | ---------------- |
| 0     | 2   | {9,8,7}      | {7,8,9}          |
| 1     | 1   | {7,8,9}      | stop             |

* **Final Row 2:** `{7,8,9}` ✅

---

## **Step 9: Print the array**

```java
for(int i = 0; i < row; i++){
    for(int j = 0; j < col; j++){
        System.out.print(arr[i][j] + " ");
    }
    System.out.println();
}
```

* Outer loop → iterate rows
* Inner loop → iterate columns in each row
* `System.out.print(arr[i][j] + " ")` → print element
* `System.out.println()` → move to next row

**Output:**

```
1 2 3
4 5 6
7 8 9
```

✅ This is the **reversed 2D array row-wise**.

---

## **Step 10: Conceptual Summary**

1. **Two-pointer technique** (`start` & `end`) is used **per row** to reverse it **in-place**.
2. Outer loop goes **row by row**.
3. Inner `while` loop swaps first ↔ last, second ↔ second-last… until row is reversed.
4. The **print loop** just displays the final array — it does **not modify anything**.
5. Time Complexity: O(rows × cols) → each element touched once
6. Space Complexity: O(1) → no extra array

---


Do you want me to do that?
