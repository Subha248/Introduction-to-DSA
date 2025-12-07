
---

# **Full Bubble Sort Code (Optimized)**

```java
import java.util.Arrays;

public class SS {
    public static void main(String[] args) {
        int[] arr = {3, 1, 4, 5, 2}; // unsorted array
        bubble(arr);                 // sort the array
        System.out.println(Arrays.toString(arr)); // print sorted array
    }

    static void bubble(int[] arr) {
        boolean swapped;

        // Outer loop: each pass over the array
        for (int i = 0; i < arr.length; i++) {
            swapped = false; // reset swapped flag for this pass

            // Inner loop: compare adjacent elements
            for (int j = 1; j < arr.length - i; j++) {
                if (arr[j] < arr[j - 1]) {
                    // Swap if elements are out of order
                    swapped = true;
                    int temp = arr[j];
                    arr[j] = arr[j - 1];
                    arr[j - 1] = temp;
                }
            }

            // If no swaps happened in this pass → array is sorted, break early
            if (!swapped) break;
        }
    }
}
```

---

# **Bubble Sort Explanation (Logical Blocks)**

1. **Initialization**

   * `arr = {3,1,4,5,2}` → unsorted array.
   * Call `bubble(arr)` → sorts it **in-place**.

2. **Outer Loop**

   * Represents **passes** over the array.
   * Each pass “bubbles up” the largest unsorted element to its correct position.

3. **Inner Loop**

   * Compares adjacent elements: `arr[j-1]` vs `arr[j]`.
   * Swaps them if the left is bigger than the right.
   * `arr.length - i` → reduces comparisons because the last `i` elements are already sorted.

4. **Swapped Flag**

   * Tracks if any swaps happened in the current pass.
   * If no swaps → array is already sorted → break early → **optimization**.

5. **Swap Logic**

   * Uses a temporary variable `temp` to swap `arr[j]` and `arr[j-1]`.

6. **Result**

   * Array is sorted in **ascending order**.
   * Printed using `Arrays.toString()`.

---

# **Visual Dry Run (“Bubbling”)**

Array: `{3, 1, 4, 5, 2}`

**Pass 1:**

```
[3,1,4,5,2] → compare 3 & 1 → swap → [1,3,4,5,2]
[1,3,4,5,2] → compare 3 & 4 → no swap
[1,3,4,5,2] → compare 4 & 5 → no swap
[1,3,4,5,2] → compare 5 & 2 → swap → [1,3,4,2,5]
```

Largest `5` “bubbled” to the end.

**Pass 2:**

```
[1,3,4,2,5] → compare 1 & 3 → no swap
[1,3,4,2,5] → compare 3 & 4 → no swap
[1,3,4,2,5] → compare 4 & 2 → swap → [1,3,2,4,5]
```

Next largest `4` in place.

**Pass 3:**

```
[1,3,2,4,5] → compare 1 & 3 → no swap
[1,3,2,4,5] → compare 3 & 2 → swap → [1,2,3,4,5]
```

**Pass 4:** No swaps → break early.

✅ Sorted array: `[1, 2, 3, 4, 5]`

---
---

### **Bubble Sort: Stability**

1. **Stable:** Yes ✅

   * Equal elements **do not swap**, so their original relative order stays the same.

2. **Why:**

   * Swap only happens if `arr[j] < arr[j-1]`.
   * `arr[j] == arr[j-1]` → no swap → order preserved.

3. **When it matters:**

   * Sorting objects with keys, where secondary order matters (like names with same scores).

4. **Extra:**

   * Always stable, even in optimized version with `swapped` flag.

---

