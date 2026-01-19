
---

### 2D Array Loops Explained Easily

Imagine a **table**:

```
row\col | 0  1
--------+-----
0       | ?  ?
1       | ?  ?
2       | ?  ?
```

We want to fill every `?` with a number.

---

### Step 1 — Outer Loop (rows)

```java
for (int row = 0; row < 3; row++) { ... }
```

* Goes **from top to bottom**
* `row = 0 → 2`
* Each time, we move to a **new row**

---

### Step 2 — Inner Loop (columns)

```java
for (int col = 0; col < 2; col++) { ... }
```

* Goes **from left to right** inside the current row
* `col = 0 → 1`
* Each time, we move to the **next column in that row**

---

### Step 3 — Fill the value

```java
arr[row][col] = sc.nextInt();
```

* Takes input and stores it in **current row and column**

---

### Step 4 — How loops work together

Think like this:

1. `row = 0`

   * `col = 0` → fill arr[0][0]
   * `col = 1` → fill arr[0][1]
2. `row = 1`

   * `col = 0` → fill arr[1][0]
   * `col = 1` → fill arr[1][1]
3. `row = 2`

   * `col = 0` → fill arr[2][0]
   * `col = 1` → fill arr[2][1]

---

---

```java
import java.util.*;  // Import Scanner for input

public class Array2D {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in); // Create Scanner object

        // Step 1: Take array size from user
        System.out.print("Enter number of rows: ");
        int rows = in.nextInt();  // Number of rows
        System.out.print("Enter number of columns: ");
        int cols = in.nextInt();  // Number of columns

        // Step 2: Create 2D array
        int[][] arr = new int[rows][cols];

        // Step 3: Input elements
        System.out.println("Enter array elements:");
        for (int row = 0; row < rows; row++) {
            for (int col = 0; col < cols; col++) {
                arr[row][col] = in.nextInt(); // Fill each cell
            }
        }

        // Step 4: Output the array
        System.out.println("Your 2D array:");
        for (int row = 0; row < rows; row++) {
            for (int col = 0; col < cols; col++) {
                System.out.print(arr[row][col] + " "); // Print element
            }
            System.out.println(); // Move to next row
        }
    }
}
```

---

### 💡 **Explanation**

1. `rows` → number of rows
2. `cols` → number of columns
3. `arr[row][col]` → each cell in the 2D array
4. **First nested loop** → takes input row by row
5. **Second nested loop** → prints the array like a table

---

### ✅ **Example**

**Input:**

```
Enter number of rows: 2
Enter number of columns: 3
Enter array elements:
1 2 3
4 5 6
```

**Output:**

```
Your 2D array:
1 2 3
4 5 6
```

---


---

### Given:

* Rows = 3
* Columns = 2 (each row has 2 elements)
* Array: `int[][] arr = new int[3][2];`

---

### How nested loops work:

```java
for (int r = 0; r < 3; r++) {        // row loop
    for (int c = 0; c < arr[r].length; c++) {  // column loop
        arr[r][c] = ...;  // input or print
    }
}
```

---

### Step by Step:

#### 1️⃣ First outer loop: `r = 0` (0th row)

* Inner loop: `c = 0 → arr[0][0]`
* Inner loop: `c = 1 → arr[0][1]`
* Done with row 0 → move to next row

#### 2️⃣ Second outer loop: `r = 1` (1st row)

* Inner loop: `c = 0 → arr[1][0]`
* Inner loop: `c = 1 → arr[1][1]`
* Done with row 1 → move to next row

#### 3️⃣ Third outer loop: `r = 2` (2nd row)

* Inner loop: `c = 0 → arr[2][0]`
* Inner loop: `c = 1 → arr[2][1]`
* Done with row 2 → loops end

---

### ✅ Visual:

```
arr[0][0]  arr[0][1]   --> first row
arr[1][0]  arr[1][1]   --> second row
arr[2][0]  arr[2][1]   --> third row
```

* Outer loop → moves **down the rows**
* Inner loop → moves **across the columns in that row**

---
Absolutely! Let’s give you a **clean, fully corrected, and GitHub-ready version** of your 2D array program using your `Arrays.toString()` approach. I’ll also make it **properly formatted** and **commented**, so it’s easy to revise later.

---

### GitHub-Ready Code

```java
import java.util.Arrays;
import java.util.Scanner;

public class ArrayMatrix {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // 1️⃣ Input: number of rows and columns
        System.out.print("Enter number of rows: ");
        int n = sc.nextInt();
        System.out.print("Enter number of columns: ");
        int m = sc.nextInt();

        // 2️⃣ Create a 2D array
        int[][] demo = new int[n][m];

        // 3️⃣ Input elements into the array
        System.out.println("Enter the elements of the array:");
        for (int r = 0; r < n; r++) {
            for (int c = 0; c < m; c++) {
                demo[r][c] = sc.nextInt();
            }
        }

        // 4️⃣ Output: print each row using Arrays.toString()
        System.out.println("The 2D array is:");
        for (int r = 0; r < n; r++) {
            System.out.println(Arrays.toString(demo[r]));
        }

        sc.close(); // close the scanner
    }
}
```

---

### ✅ Example Run

**Input:**

```
Enter number of rows: 2
Enter number of columns: 3
Enter the elements of the array:
1 2 3
4 5 6
```

**Output:**

```
The 2D array is:
[1, 2, 3]
[4, 5, 6]
```

---

### Explanation for Revision

1. **`demo[r][c] = sc.nextInt();`** → stores user input at row `r` and column `c`.
2. **`Arrays.toString(demo[r])`** → converts the row array into a readable string, showing all elements in that row.
3. **Nested loops** → outer loop goes row by row, inner loop goes column by column.

---




