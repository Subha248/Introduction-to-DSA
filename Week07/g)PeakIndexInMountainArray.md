
```java
public class PeakIndexMountainArray {
    public static void main(String[] args){
        int[] arr = {0, 10, 5, 2};
        System.out.println(ans(arr)); // print peak index
    }

    public static int ans(int[] arr){
        int start = 0;
        int end = arr.length - 1;

        // loop until start and end converge
        while(start < end){  // use < to avoid infinite loop
            int mid = start + (end - start) / 2;

            if(arr[mid] < arr[mid + 1]){
                // you are in ascending part of array
                start = mid + 1; // because mid+1 element > mid, peak is right
            }
            else {
                // you are in descending part of array
                end = mid; // peak could be mid or on the left
            }

            // debugging info (optional)
            // System.out.println("start=" + start + " end=" + end + " mid=" + mid);
        }

        // in the end, start == end and pointing to the largest number because:
        // start and end are always moving towards the max element using the above checks
        // when only one element is remaining, that must be the peak
        return start;
    }
}
```

---

### Step-by-step for `[0, 10, 5, 2]`:

| Iter | start | end | mid | arr[mid] | arr[mid+1] | Action                    |
| ---- | ----- | --- | --- | -------- | ---------- | ------------------------- |
| 1    | 0     | 3   | 1   | 10       | 5          | descending → end=mid=1    |
| 2    | 0     | 1   | 0   | 0        | 10         | ascending → start=mid+1=1 |

`start == end == 1` → peak index = 1 ✅

---

### Another Example array:

```java
int[] arr = {1, 3, 8, 12, 4, 2};
```

Peak is `12` at **index 3**.

---

### Step-by-step trace using your logic:

**Initial:** `start = 0`, `end = 5`

| Iter | start | end | mid | arr[mid] | arr[mid+1] | Action                                              |
| ---- | ----- | --- | --- | -------- | ---------- | --------------------------------------------------- |
| 1    | 0     | 5   | 2   | 8        | 12         | arr[mid]<arr[mid+1] → ascending → start = mid+1 = 3 |
| 2    | 3     | 5   | 4   | 4        | 2          | arr[mid]>arr[mid+1] → descending → end = mid = 4    |
| 3    | 3     | 4   | 3   | 12       | 4          | arr[mid]>arr[mid+1] → descending → end = mid = 3    |

**Loop ends:** `start == end == 3` → peak index = 3 ✅

---

### Notes on movement:

* **Ascending part:** `start` moves right because peak is ahead.
* **Descending part:** `end` moves left because peak could be mid or left.
* **Convergence:** `start` and `end` always converge at the **peak index**.

---

