
---

## **Question**

Write a program in Java to print a triangular pattern of numbers where each row consists of the same number repeated.  
The number of repetitions in each row equals the row number.

### Example:
For an input \( n = 8 \), the output should look like:
```
1
22
333
4444
55555
666666
7777777
88888888
```

---

## **Program**

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int n = scan.nextInt(); // Input number of rows

        for (int i = 1; i <= n; i++) { // Outer loop for rows
            for (int j = 1; j <= i; j++) { // Inner loop for columns
                System.out.print(i); // Print the current row number
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
8
```

### Output:
```
1
22
333
4444
55555
666666
7777777
88888888
```

---

## **Explanation**

1. **Outer Loop (`i`)**: Controls the rows of the triangle.  
   - Row 1 will have `1` number, Row 2 will have `2` numbers, and so on up to Row `n`.

2. **Inner Loop (`j`)**: Controls how many numbers are printed in each row.  
   - For Row `i`, it runs `i` times.

3. **Printing Numbers:**
   - `System.out.print(i);` prints the current row number multiple times, where the count equals the row number.

4. **Line Break (`System.out.println()`):** Ensures each row is printed on a new line.

---

## **Tracking `i` and `j` in a Table**

The following table shows how `i` and `j` change as the program runs:

| **Row (i)** | **Iteration (j)** | **Printed Value** |
|-------------|-------------------|-------------------|
| 1           | 1                 | 1                 |
| 2           | 1                 | 2                 |
| 2           | 2                 | 2                 |
| 3           | 1                 | 3                 |
| 3           | 2                 | 3                 |
| 3           | 3                 | 3                 |
| 4           | 1                 | 4                 |
| 4           | 2                 | 4                 |
| 4           | 3                 | 4                 |
| 4           | 4                 | 4                 |
| 5           | 1                 | 5                 |
| 5           | 2                 | 5                 |
| 5           | 3                 | 5                 |
| 5           | 4                 | 5                 |
| 5           | 5                 | 5                 |

---

## **Walkthrough Example:**

### Input:
```
4
```

### Output:
```
1
22
333
4444
```

### Explanation for \( n = 4 \):

- **Row 1:** Prints `1`, repeats `1` time.  
- **Row 2:** Prints `2`, repeats `2` times.  
- **Row 3:** Prints `3`, repeats `3` times.  
- **Row 4:** Prints `4`, repeats `4` times.  

---

