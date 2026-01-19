### Question 1:

**Print a Diamond Pattern**

Write a program that takes an integer input \( n \) and prints a diamond pattern of stars (\(*\)). The diamond should have \( n - 1 \) rows in the upper part and \( n \) rows in the lower part. The stars should be aligned symmetrically.

---

### Input:
An integer \( n \) representing the number of rows for the lower part of the diamond, plus one for the middle row.

### Output:
A diamond pattern of stars.

---

### Example:

**Input:**
```
5
```

**Output:**
```
    * 
   *** 
  ***** 
 ******* 
********* 
 ******* 
  ***** 
   *** 
    * 
```

---

### Code:

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int n = scan.nextInt();

        // Upper part of the diamond
        for (int i = 1; i <= n - 1; i++) {
            for (int j = 1; j <= n - i; j++) {
                System.out.print(" ");
            }
            for (int j = 1; j <= 2 * i - 1; j++) {
                System.out.print("*");
            }
            System.out.println(" ");
        }

        // Lower part of the diamond
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= i - 1; j++) {
                System.out.print(" ");
            }
            for (int j = 1; j <= (2 * n) - (2 * i - 1); j++) {
                System.out.print("*");
            }
            System.out.println(" ");
        }
    }
}
```

---

### Explanation:

1. **Input**: 
   - The user enters \( n \), which defines the number of rows in the lower part of the diamond and one additional row for the middle.

2. **Upper Part of the Diamond**:
   - Controlled by the first loop (`i` from 1 to \( n - 1 \)).
   - For each row:
     - Spaces: \( n - i \) spaces are printed at the beginning.
     - Stars: \( 2 \times i - 1 \) stars are printed to form the increasing triangle.

3. **Lower Part of the Diamond**:
   - Controlled by the second loop (`i` from 1 to \( n \)).
   - For each row:
     - Spaces: \( i - 1 \) spaces are printed at the beginning.
     - Stars: \( (2 \times n) - (2 \times i - 1) \) stars are printed to form the decreasing triangle.

---

### Walkthrough for \( n = 5 \):

**Upper Part**:
- Row 1: \( n - 1 = 4 \) spaces, \( 1 \) star → `    *`
- Row 2: \( n - 2 = 3 \) spaces, \( 3 \) stars → `   ***`
- Row 3: \( n - 3 = 2 \) spaces, \( 5 \) stars → `  *****`
- Row 4: \( n - 4 = 1 \) space, \( 7 \) stars → ` *******`

**Lower Part**:
- Row 1: \( 0 \) spaces, \( 9 \) stars → `*********`
- Row 2: \( 1 \) space, \( 7 \) stars → ` *******`
- Row 3: \( 2 \) spaces, \( 5 \) stars → `  *****`
- Row 4: \( 3 \) spaces, \( 3 \) stars → `   ***`
- Row 5: \( 4 \) spaces, \( 1 \) star → `    *`

---

### Output for \( n = 5 \):

```
    * 
   *** 
  ***** 
 ******* 
********* 
 ******* 
  ***** 
   *** 
    * 
```


## **Question 2:**

Write a program in Java to print a triangular pattern of numbers.  
The triangle starts with `1` and increments sequentially, row by row, based on the number of rows entered by the user.

### Example:
For an input \( n = 5 \), the output should look like:
```
1
2 3
4 5 6
7 8 9 10
11 12 13 14 15
```

---

## **Program**

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int n = scan.nextInt(); // Input for number of rows
        int count = 1; // Initialize count variable

        for (int i = 1; i <= n; i++) { // Outer loop for rows
            for (int j = 1; j <= i; j++) { // Inner loop for numbers in the row
                System.out.print(count + " "); // Print the current number
                count++; // Increment the count
            }
            System.out.println(); // Move to the next line after each row
        }
    }
}
```

---

## **Output**

### Input:
```
5
```

### Output:
```
1
2 3
4 5 6
7 8 9 10
11 12 13 14 15
```

---

## **Explanation**

1. **Outer Loop (`i`)**: Controls the rows of the triangle.  
   - Row 1 will have `1` number, Row 2 will have `2` numbers, and so on up to Row `n`.

2. **Inner Loop (`j`)**: Controls how many numbers are printed in each row.  
   - For Row `i`, it runs `i` times.

3. **Counter (`count`)**: A variable to keep track of the current number to print.  
   - Starts at `1` and increments after each number is printed.

4. **Line Break (`System.out.println()`):** Ensures each row is printed on a new line.

---

## **Tracking `i`, `j`, and `count` in a Table**

The following table shows how `i`, `j`, and `count` change as the program runs:

| **Row (i)** | **Iteration (j)** | **Printed Value (count)** | **Next Value of count** |
|-------------|-------------------|---------------------------|--------------------------|
| 1           | 1                 | 1                         | 2                        |
| 2           | 1                 | 2                         | 3                        |
| 2           | 2                 | 3                         | 4                        |
| 3           | 1                 | 4                         | 5                        |
| 3           | 2                 | 5                         | 6                        |
| 3           | 3                 | 6                         | 7                        |
| 4           | 1                 | 7                         | 8                        |
| 4           | 2                 | 8                         | 9                        |
| 4           | 3                 | 9                         | 10                       |
| 4           | 4                 | 10                        | 11                       |
| 5           | 1                 | 11                        | 12                       |
| 5           | 2                 | 12                        | 13                       |
| 5           | 3                 | 13                        | 14                       |
| 5           | 4                 | 14                        | 15                       |
| 5           | 5                 | 15                        | 16                       |

---

## **Walkthrough Example:**

### Input:
```
4
```

### Output:
```
1
2 3
4 5 6
7 8 9 10
```

### Explanation for `n = 4`:

- **Row 1:** Prints `1`, increments `count` to `2`.  
- **Row 2:** Prints `2 3`, increments `count` to `4`.  
- **Row 3:** Prints `4 5 6`, increments `count` to `7`.  
- **Row 4:** Prints `7 8 9 10`, increments `count` to `11`.

---



