### Example 1
This program is a **pattern printing program** in Java. It prints a rectangular block of `*` (asterisks) for a given value of `n` (rows and columns).

---

### Code Explanation:
```java
class Main {
    public static void main(String[] args) {
        int n = 4; // Number of rows and columns

        for (int i = 1; i <= n; i++) {         // Outer loop for rows
            for (int j = 1; j <= n; j++) {     // Inner loop for columns
                System.out.print("*");         // Print star without moving to the next line
            }
            System.out.println("");            // Move to the next line after each row
        }
    }
}
```

---

### How It Works:
1. **`int n = 4`**: Sets the number of rows and columns.
2. **Outer Loop (`i`)**:
   - Controls the **number of rows** (from `1` to `n`).

3. **Inner Loop (`j`)**:
   - Controls the **number of stars** printed in each row (from `1` to `n`).

4. **`System.out.print("*")`**:
   - Prints the star (`*`) without moving to the next line.

5. **`System.out.println("")`**:
   - Moves to the next line after printing all stars for one row.

---

### Execution for `n = 4`:

#### Step-by-Step:
- **Row 1**: Prints `****` → Moves to the next line.
- **Row 2**: Prints `****` → Moves to the next line.
- **Row 3**: Prints `****` → Moves to the next line.
- **Row 4**: Prints `****` → Moves to the next line.

---

### Output:
```
****
****
****
****
```

---

### Key Concepts:
1. **Nested Loops**:
   - Outer loop controls rows.
   - Inner loop controls columns (number of stars printed).

2. **`print()` vs `println()`**:
   - `print()` prints on the same line.
   - `println()` moves to the next line.

---

This program is the basic logic for **pattern printing** and can be modified to create various shapes like triangles, pyramids, etc.

### Example 2:
Code:
```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int n = scan.nextInt();

        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= n; j++) {
                System.out.print(j);
            }
            System.out.println();
        }
    }
}
```

---

### Explanation:
1. **Input**:  
   - Takes an integer `n` as input.

2. **Nested Loops**:
   - Outer loop → Runs `n` times for `n` rows.
   - Inner loop → Prints numbers from `1` to `n` on each row.

3. **Output**:
   - Prints a square pattern of numbers.

---

### Example Input/Output:

#### Input:
```
3
```

#### Output:
```
123
123
123
```

#### Input:
```
4
```

#### Output:
```
1234
1234
1234
1234
```
### Example 3

Write a Java program to print a number triangle with `N` rows. For example, if `N = 4`, the output should be:

```
1
12
123
1234
```

```java
public class Main {
  public static void main(String[] args) {
    int N = 15; // Total rows
    for (int i = 1; i <= N; i++) { // Loop through rows
      for (int j = 1; j <= i; j++) { // Print numbers from 1 to the current row number
        System.out.print(j);
      }
      System.out.println(); // Move to the next line after each row
    }
  }
}
```

### Simplified Explanation:
1. **Outer loop (`i`)**: Runs from `1` to `N` (15 rows).
2. **Inner loop (`j`)**: Prints numbers from `1` to the current row (`i`).
3. **Output**: Creates a triangle pattern of numbers.

Example for `N = 4`:
```
1
12
123
1234
``` 

This is a simple program to print a triangular number pattern.
