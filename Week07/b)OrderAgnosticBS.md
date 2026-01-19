
```java
public class Binary {

    public static void main(String[] args) {
        // Sorted array (ascending in this case)
        int[] arr = {-18, -12, -4, 0, 2, 3, 4, 15, 16, 18, 22, 45, 89};
        int target = 2;

        // Call the order-agnostic binary search function
        int ans = orderAgnosticBS(arr, target);

        // Print the index of target (or -1 if not found)
        System.out.print(ans);
    }

    // Order-agnostic binary search function
    public static int orderAgnosticBS(int[] arr, int target) {

        int start = 0;                // start index
        int end = arr.length - 1;     // end index

        // Detect if the array is ascending or descending
        boolean asc = arr[start] < arr[end];

        // Keep searching while there is a valid search space
        while (start <= end) {

            // Find the middle element safely
            int mid = start + (end - start) / 2;

            // Check if mid is the target
            if (arr[mid] == target) {
                return mid;  // target found, return index
            }

            // If array is ascending
            if (asc) {
                if (target < arr[mid]) {
                    end = mid - 1;   // go left
                } else {
                    start = mid + 1; // go right
                }
            } 
            // If array is descending
            else {
                if (target > arr[mid]) {
                    end = mid - 1;   // go left in descending
                } else {
                    start = mid + 1; // go right in descending
                }
            }
        }

        // Target not found
        return -1;
    }
}
```

---

### ✅ How it works step by step for your example:

Array:

```
{-18, -12, -4, 0, 2, 3, 4, 15, 16, 18, 22, 45, 89}
```

Target: `2`

| Step | start | end | mid | arr[mid] | Action             |
| ---- | ----- | --- | --- | -------- | ------------------ |
| 1    | 0     | 12  | 6   | 4        | 2 < 4 → end = 5    |
| 2    | 0     | 5   | 2   | -4       | 2 > -4 → start = 3 |
| 3    | 3     | 5   | 4   | 2        | 2 == 2 → return 4  |

Output: `4` ✅

---

