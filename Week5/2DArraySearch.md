```java
import java.util.Arrays;

public class TwoDSearch {
    public static void main(String[] args) {
        int[][] arr = {               // 2D array (array of arrays)
            {1, 2, 3},
            {4, 7, 5, 6},
            {8, 9, 13, 23}
        };

        int target = 5;               // number we want to find
        int[] ans = Array2D(arr, target); // call the method to get position
        System.out.println(Arrays.toString(ans)); // print result as [row, col]
    }

    public static int[] Array2D(int[][] arr, int target) {
        for (int row = 0; row < arr.length; row++) {           // loop through each row
            for (int col = 0; col < arr[row].length; col++) {  // loop through each element in the row
                if (arr[row][col] == target) {                // if current element == target
                    return new int[]{row, col};              // return its position
                }
            }
        }
        return new int[]{-1, -1};                             // return -1,-1 if target not found
    }
}
```

---

### 🔹 Simple Explanation:

1. **`arr.length`** → total number of rows in 2D array
2. **`arr[row].length`** → total columns in the current row
3. Outer loop → goes through each **row**
4. Inner loop → goes through each **column in that row**
5. If `arr[row][col] == target` → return `[row, col]`
6. If target not found → return `[-1, -1]`

---

### ⚡ Example Output:

For `target = 5`:

```
[1, 2]
```

* Row 1, Column 2 (0-indexed).

---

