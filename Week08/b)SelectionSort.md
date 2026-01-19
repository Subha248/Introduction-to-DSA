# Selection-sort logic (find max and swap to end)

---

# ✅ Full working code

```java
import java.util.Arrays;

public class sort {
    public static void main(String[] args) {
        int[] arr = {3, 1, 5, 4, 2};
        selection(arr);
        System.out.println(Arrays.toString(arr)); // print sorted array
    }

    public static void selection(int[] arr) {
        for (int i = 0; i < arr.length; i++) {
            int start = 0;
            int last = arr.length - i - 1;      // unsorted portion ends here
            int maxindex = getMax(arr, start, last);
            swapped(arr, maxindex, last);       // put max at 'last'
        }
    }

    public static int getMax(int[] arr, int start, int last) {
        int max = start;
        for (int i = start; i <= last; i++) {
            if (arr[i] > arr[max]) {
                max = i;
            }
        }
        return max;
    }

    static void swapped(int[] arr, int first, int second) {
        int temp = arr[first];
        arr[first] = arr[second];
        arr[second] = temp;
    }
}
```

---

# 📝 Explanation (short, like code comments)

* `main`

  * Initializes the array and calls `selection(arr)`.
  * Prints the sorted array using `Arrays.toString()`.

* `selection(int[] arr)`

  * Outer loop `i` = number of elements already placed at the end.
  * `last = arr.length - i - 1` → index of the last element in the *current unsorted* portion.
  * `getMax(arr, start, last)` finds the index of the maximum element inside `[start..last]`.
  * `swapped(arr, maxindex, last)` swaps the found max into the `last` position, shrinking the unsorted window.

* `getMax(int[] arr, int start, int last)`

  * Linear scan from `start` to `last`.
  * Maintains `max` index; updates when a larger element is found.
  * Returns index of maximum in that subarray.

* `swapped(int[] arr, int first, int second)`

  * Standard three-line swap using a temp variable.
  * Swaps values at indices `first` and `second`.

---
---

# 🔥 **DETAILED DRY RUN**

Array:

```
[3, 1, 5, 4, 2]
```

---

## **Iteration 1 (i = 0)**

* `last = arr.length - i - 1 = 5 - 0 - 1 = 4`
* We search from index `0` to `4` for max.

### getMax scanning:

* Start: max = index 0 → value 3
* i=1 → value 1 → smaller → ignore
* i=2 → value 5 → bigger → max = 2
* i=3 → value 4 → smaller than 5
* i=4 → value 2 → smaller
  👉 Final maxindex = **2** (value=5)

### Swap

Swap arr[2] ↔ arr[4]:

Before: `[3,1,5,4,2]`
After:  `[3,1,2,4,5]`

**Largest element 5 is now placed correctly.**

---

## **Iteration 2 (i = 1)**

* `last = 5 - 1 - 1 = 3`
* Search from index `0` to `3`.

### getMax scanning:

* max = index 0 → value 3
* i=1 → value 1 → ignore
* i=2 → value 2 → ignore
* i=3 → value 4 → bigger → max = 3
  👉 maxindex = **3** (value 4)

### Swap

Swap arr[3] with arr[3] (same index):

Array stays:
`[3,1,2,4,5]`

**4 is now in correct second-last position.**

---

## **Iteration 3 (i = 2)**

* `last = 5 - 2 - 1 = 2`

### getMax scanning:

* max = index 0 → value 3
* i=1 → value 1 → ignore
* i=2 → value 2 → ignore
  👉 maxindex = **0** (value 3)

### Swap

Swap arr[0] ↔ arr[2]:

Before: `[3,1,2,4,5]`
After:  `[2,1,3,4,5]`

**3 is now correctly placed.**

---

## **Iteration 4 (i = 3)**

* `last = 5 - 3 - 1 = 1`

### getMax scanning:

* max = index 0 → value 2
* i=1 → value 1 → ignore
  👉 maxindex = **0** (value 2)

### Swap

Swap arr[0] ↔ arr[1]:

Before: `[2,1,3,4,5]`
After:  `[1,2,3,4,5]`

**2 is now in place.**

---

## **Iteration 5 (i = 4)**

* `last = 5 - 4 - 1 = 0`

Only one element in the “unsorted” zone.
maxindex = 0.

Swap arr[0] ↔ arr[0] → no change.

---

# ✅ **Final Sorted Output**

```
[1, 2, 3, 4, 5]
```

---

