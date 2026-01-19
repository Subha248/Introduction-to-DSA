
### Question:
Write a Java program to print a series of asterisks (`*`) in increasing order, separated by spaces. Each term contains as many asterisks as its position.  

**Example:**
- Input: `N = 3`  
- Output: `* ** ***`

---

### Code:
```java
import java.util.Scanner;

public class Main {
  public static void main(String[] args) {
    Scanner scan = new Scanner(System.in);
    int N = scan.nextInt();

    for (int i = 1; i <= N; i++) {
      for (int j = 1; j <= i; j++) {
        System.out.print("*");
      }
      System.out.print(" ");
    }
  }
}
```
### Explanation:

1. **Input:**  
   - Read `N`, which is the number of terms to print.

2. **Outer Loop (`i`):**  
   - Runs from `1` to `N`.  
   - Controls the number of groups of asterisks to print.

3. **Inner Loop (`j`):**  
   - Runs from `1` to `i`.  
   - Prints `i` asterisks in each group.

4. **Space:**  
   - After printing each group of asterisks, a space is added to separate the groups.

---

**Example Walkthrough (N = 3):**  
- For `i = 1`, print `*`.  
- For `i = 2`, print `**`.  
- For `i = 3`, print `***`.  
- Add a space after each group.  

**Output:**  
```
* ** ***
```


### Question 2: Print a Right-Angled Number Triangle

**Problem Statement**:  
Write a program to print a right-angled number triangle pattern. For a given input \(N\), the first row should contain numbers from 1 to \(N\), the second row from 1 to \(N-1\), and so on until the last row contains only the number 1.

---

### Code:
```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        int N = 4; // You can change N to any desired value
        for (int i = 1; i <= N; i++) {
            for (int j = 1; j <= N - i + 1; j++) {
                System.out.print(j);
            }
            System.out.println(""); // Move to the next line after each row
        }
    }
}
```

---

### Output (For N = 4):
```
1234
123
12
1
```

---

### Explanation:
1. **Outer Loop** (`for (int i = 1; i <= N; i++)`): Controls the number of rows. The value of \(i\) starts at 1 and increments up to \(N\).
2. **Inner Loop** (`for (int j = 1; j <= N - i + 1; j++)`): Prints numbers from 1 to \(N - i + 1\) for each row. As \(i\) increases, the number of columns decreases.
3. **Line Break** (`System.out.println("")`): Moves to the next line after printing each row.

Here’s a clean, copy-paste-ready format for your GitHub:

---

### Sample 1:

**Input:**
```plaintext
n = 4
```

**Expected Output:**
```plaintext
****
***
**
*
```

---

### Code:
```java

import java.util.*;

public class Main {
    public static void main(String[] args) {
      Scanner scan=new  Scanner(System.in);
      int N= scan.nextInt();
      for(int i=1;i<=N;i++){
        for(int j=1;j<=N-i+1;j++){
          System.out.print("*");
        }
      
      System.out.println("");
      }
  }
}
```

---

This program prints an inverted triangle of stars (\(*\)) based on user input \(N\).

### Steps:
1. **Input**: User enters a number \(N\) (size of the triangle).
2. **Outer Loop**: Runs \(N\) times (for each row).
3. **Inner Loop**: Prints \(N - i + 1\) stars in each row, decreasing as rows increase.
4. **Line Break**: Moves to the next row after printing stars.

### Example:
**Input**: `4`  
**Output**:
```plaintext
****
***
**
*
``` 


To ensure that the formatting, including **bold text**, headers, and code blocks, works properly when you copy and paste it into GitHub, you need to follow **Markdown syntax** correctly.

Here’s how your program and explanation should look when formatted for GitHub:

---

### Sample 2

**Input**:
```
n = 6
```

**Output**:
```
******
*****
****
***
**
*
```

---

### Code
```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in); // Create Scanner object for user input
        System.out.print("Enter the value of n: "); // Prompt for input
        int N = scan.nextInt(); // Take user input for n
        
        for (int i = 1; i <= N; i++) { // Outer loop for rows
            for (int j = 1; j <= N - i + 1; j++) { // Inner loop for stars
                System.out.print("*");
            }
            System.out.println(""); // Move to the next row
        }
        scan.close(); // Close Scanner to prevent resource leak
    }
}
```

---

### Explanation

1. **Input**:  
   - The program takes a number \( n \) as input from the user.
2. **Logic**:  
   - The outer loop (`for (int i = 1; i <= N; i++)`) controls the number of rows.  
   - The inner loop (`for (int j = 1; j <= N - i + 1; j++)`) controls the number of stars (\(*\)) in each row.  
   - As the row number increases, the number of stars decreases.
3. **Output**:  
   - The program prints \( n \) stars in the first row, \( n-1 \) in the second, and so on until the last row contains 1 star.

---

---

### Problem Statement 3:
You are tasked with building a star pattern that first increases row by row up to \(n\) rows, then decreases back to 1 row. For \(n = 5\), the pattern should look like this:

**Expected Output**:
```
* 
* * 
* * * 
* * * * 
* * * * *
* * * *
* * *
* *
*
```

---

### Full Code:
```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in); // Create Scanner object for input
        System.out.print("Enter the number of rows (n): ");
        int n = scan.nextInt(); // Take input for n

        // First Loop: Create the increasing triangle
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print("* ");
            }
            System.out.println(""); // Move to the next row
        }

        // Second Loop: Create the decreasing triangle
        for (int i = 2; i <= n; i++) {
            for (int j = 1; j <= n - i + 1; j++) {
                System.out.print("* ");
            }
            System.out.println(""); // Move to the next row
        }

        scan.close(); // Close Scanner to avoid resource leak
    }
}
```

---

### Explanation:

1. **Input**:
   - The program prompts the user to enter the number of rows (\(n\)) for the pattern.

2. **First Loop (Increasing Triangle)**:
   ```java
   for (int i = 1; i <= n; i++) {
       for (int j = 1; j <= i; j++) {
           System.out.print("* ");
       }
       System.out.println("");
   }
   ```
   - The outer loop controls the rows for the upper (increasing) triangle.
   - The inner loop prints \(i\) stars for each row.
   - A line break is added after each row.

3. **Second Loop (Decreasing Triangle)**:
   ```java
   for (int i = 2; i <= n; i++) {
       for (int j = 1; j <= n - i + 1; j++) {
           System.out.print("* ");
       }
       System.out.println("");
   }
   ```
   - The outer loop starts at row 2 (to avoid repeating the middle row) and continues until \(n\).
   - The inner loop prints decreasing stars for each row: \(n - i + 1\) stars.
   - A line break is added after each row.

4. **Line Break**:
   - The `System.out.println("")` ensures that stars in each row are printed on a new line.

---

### Example Walkthrough for \(n = 5\):

**Input**:
```
Enter the number of rows (n): 5
```

**Output**:
```
* 
* * 
* * * 
* * * * 
* * * * *
* * * *
* * *
* *
*
```

- **First Loop**:
  - Row 1: 1 star (\(i = 1\)).
  - Row 2: 2 stars (\(i = 2\)).
  - Row 3: 3 stars (\(i = 3\)).
  - Row 4: 4 stars (\(i = 4\)).
  - Row 5: 5 stars (\(i = 5\)).

- **Second Loop**:
  - Row 1: 4 stars (\(i = 2\), \(j = 1, 2, 3, 4\)).
  - Row 2: 3 stars (\(i = 3\), \(j = 1, 2, 3\)).
  - Row 3: 2 stars (\(i = 4\), \(j = 1, 2\)).
  - Row 4: 1 star (\(i = 5\), \(j = 1\)).

---

### Final Output for \(n = 5\):
```
* 
* * 
* * * 
* * * * 
* * * * *
* * * *
* * *
* *
*
```

---

### Summary:
- The program builds the pattern in two steps:
  1. An increasing triangle using a nested loop.
  2. A decreasing triangle using another nested loop.
- It's well-structured and handles any input size \(n\).

  Here’s the formatted explanation and code for your GitHub documentation:

---

### Problem 4: Print a Centered Triangle Pattern

**Task**:  
Given an integer \( n \), print a centered triangle pattern with \( n \) rows. For each row, stars (\(*\)) are aligned in the center, and the number of stars increases as the row number increases.

---

### Example Input and Output

**Input**:
```
n = 5
```

**Output**:
```
    *
   ***
  *****
 *******
*********
```

---

### Code:
```java
class Solution {
    void printTriangle(int n) {
        // Outer loop for rows
        for (int i = 1; i <= n; i++) {
            // Print spaces
            for (int j = 1; j <= n - i; j++) {
                System.out.print(" ");
            }
            // Print stars
            for (int j = 1; j <= 2 * i - 1; j++) {
                System.out.print("*");
            }
            // Move to the next row
            System.out.println();
        }
    }
}
```

---

### Explanation:

1. **Outer Loop**:
   - `for (int i = 1; i <= n; i++)`: Controls the rows of the triangle. Each iteration corresponds to one row.

2. **Space Loop**:
   - `for (int j = 1; j <= n - i; j++)`: Prints spaces to align the stars in the center. The number of spaces decreases as `i` increases.

3. **Star Loop**:
   - `for (int j = 1; j <= 2 * i - 1; j++)`: Prints the stars for each row. The number of stars follows the formula \(2 \times i - 1\), which increases with each row.

4. **Line Break**:
   - `System.out.println();`: Moves to the next line after printing all spaces and stars for the current row.

---

### Example Walkthrough for \(n = 5\):

1. **Row 1**:
   - Spaces: \(n - i = 5 - 1 = 4\) → `"    "`
   - Stars: \(2 * 1 - 1 = 1\) → `"*"`
   - Output: `"    *"`

2. **Row 2**:
   - Spaces: \(n - i = 5 - 2 = 3\) → `"   "`
   - Stars: \(2 * of 2 - 1 = 3\) → `"***"`
   - Output: `"   ***"`

3. **Row 3**:
   - Spaces: \(n - i = 5 - 3 = 2\) → `"  "`
   - Stars: \(2 * 3 - 1 = 5\) → `"*****"`
   - Output: `"  *****"`

4. **Row 4**:
   - Spaces: \(n - i = 5 - 4 = 1\) → `" "`
   - Stars: \(2 * 4 - 1 = 7\) → `"*******"`
   - Output: `" *******"`

5. **Row 5**:
   - Spaces: \(n - i = 5 - 5 = 0\) → `""`
   - Stars: \(2 * 5 - 1 = 9\) → `"*********"`
   - Output: `"*********"`

---
---

### Problem 5: Print an Inverted Pyramid Pattern

**Task**:  
Given an integer \(n\), print an inverted pyramid pattern with \(n\) rows. The pattern consists of spaces followed by stars (\(*\)), and the number of stars decreases row by row.

---

### Example Input and Output:

**Input**:
```
5
```

**Output**:
```
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
        for (int i = 1; i <= n; i++) {
            // Print spaces
            for (int j = 1; j <= i - 1; j++) {
                System.out.print(" ");
            }

            // Print stars
            for (int j = 1; j <= (2 * n) - (2 * i - 1); j++) {
                System.out.print("*");
            }

            // Move to the next line
            System.out.println();
        }
    }
}
```

---

### Explanation:

1. **Outer Loop**:
   - `for (int i = 1; i <= n; i++)`: Controls the number of rows in the pyramid.
   - \(i\) is the current row number.

2. **First Inner Loop (Spaces)**:
   - `for (int j = 1; j <= i - 1; j++)`: Prints spaces before the stars in each row.
   - The number of spaces increases with the row number.

3. **Second Inner Loop (Stars)**:
   - `for (int j = 1; j <= (2 * n) - (2 * i - 1); j++)`: Prints stars. The number of stars decreases with each row:
     - Row 1: \(2n - 1\) stars.
     - Row 2: \(2n - 3\) stars.
     - Row \(i\): \(2n - (2i - 1)\) stars.

4. **Line Break**:
   - `System.out.println();`: Moves the cursor to the next line after printing all spaces and stars for a row.

---

### Walkthrough for \(n = 5\):

1. **Row 1**:
   - Spaces: \(i - 1 = 1 - 1 = 0\) → `""`
   - Stars: \((2 \times 5) - (2 \times 1 - 1) = 9\) → `"*********"`
   - Output: `"*********"`

2. **Row 2**:
   - Spaces: \(i - 1 = 2 - 1 = 1\) → `" "`
   - Stars: \((2 \times 5) - (2 \times 2 - 1) = 7\) → `"*******"`
   - Output: `" *******"`

3. **Row 3**:
   - Spaces: \(i - 1 = 3 - 1 = 2\) → `"  "`
   - Stars: \((2 \times 5) - (2 \times 3 - 1) = 5\) → `"*****"`
   - Output: `"  *****"`

4. **Row 4**:
   - Spaces: \(i - 1 = 4 - 1 = 3\) → `"   "`
   - Stars: \((2 \times 5) - (2 \times 4 - 1) = 3\) → `"***"`
   - Output: `"   ***"`

5. **Row 5**:
   - Spaces: \(i - 1 = 5 - 1 = 4\) → `"    "`
   - Stars: \((2 \times 5) - (2 \times 5 - 1) = 1\) → `"*"`
   - Output: `"    *"`

---

### Complexity:

1. **Time Complexity**: \(O(n^2)\)
   - Outer loop runs \(n\) times.
   - Inner loops for spaces and stars combined run approximately \(n^2 / 2\) iterations.

2. **Space Complexity**: \(O(1)\)
   - No additional data structures are used.

---




