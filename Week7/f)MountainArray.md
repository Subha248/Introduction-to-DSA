
---

## ✅ Whole working code 

```java
public class peakindexMountainArray {
    public static void main(String[] args){
        int[] arr = {0, 10, 5, 2};
        int target = 10;
        System.out.println(search(arr, target)); // expected output: 1
    }

    // Top-level: find peak, search left; if not found, search right
    public static int search(int[] arr, int target){
        int peak = peakIM(arr);                            // find peak index
        int leftTry = AgnosticBS(arr, target, 0, peak);    // search left side (ascending)
        if (leftTry != -1) return leftTry;                // if found on left -> return
        return AgnosticBS(arr, target, peak + 1, arr.length - 1); // else search right (descending)
    }

    // Find index of peak (highest value) in mountain array
    public static int peakIM(int[] arr){
        int start = 0;
        int end = arr.length - 1;
        while (start < end) {
            int mid = start + (end - start) / 2;
            if (arr[mid] < arr[mid + 1])   // mid is on ascending slope
                start = mid + 1;
            else                           // mid is on descending slope (or at peak)
                end = mid;
        }
        return start; // start == end == peak index
    }

    // Order-agnostic binary search: works for ascending or descending ranges
    public static int AgnosticBS(int[] arr, int target, int start, int end){
        boolean isAsc = arr[start] < arr[end];

        while (start <= end) {
            int mid = start + (end - start) / 2;

            if (arr[mid] == target) return mid; // found

            if (isAsc) {
                // ascending order search
                if (target < arr[mid]) end = mid - 1;
                else start = mid + 1;
            } else {
                // descending order search
                if (target > arr[mid]) end = mid - 1;
                else start = mid + 1;
            }
        }
        return -1; // not found
    }
}
```

---

##  Explanation

**`main`**

* `int[] arr = {0,10,5,2}; int target = 10;` — set the array and the number we want.
* `System.out.println(search(arr, target));` — call the search routine and print its result.

**`search(arr, target)`**

1. `int peak = peakIM(arr);` — find the index of the mountain top (highest value).
2. `int leftTry = AgnosticBS(arr, target, 0, peak);` — binary-search the left half (0..peak). Left half is ascending.
3. `if (leftTry != -1) return leftTry;` — if found on left, return the index.
4. `return AgnosticBS(arr, target, peak + 1, arr.length - 1);` — otherwise search right half (peak+1..end), which is descending. Return whatever that returns (index or -1).

**`peakIM(arr)` (find peak)**

* `start = 0, end = last index`.
* Loop `while (start < end)`:

  * `mid = start + (end - start)/2` — safe middle.
  * `if (arr[mid] < arr[mid+1]) start = mid + 1;` → mid is on the ascending slope, so move `start` right.
  * `else end = mid;` → mid is on descending slope or peak, so move `end` to mid.
* When loop ends `start == end` — that index is the peak. Return it.

**`AgnosticBS(arr, target, start, end)`**

* `isAsc = arr[start] < arr[end]` — detect if this subsection increases or decreases.
* Standard binary-search loop `while (start <= end)`:

  * `mid = start + (end - start)/2`
  * If `arr[mid] == target` → return `mid`
  * If ascending:

    * If `target < arr[mid]` → shrink right: `end = mid - 1`
    * Else → `start = mid + 1`
  * If descending:

    * If `target > arr[mid]` → shrink right in descending sense: `end = mid - 1` (bigger values on left)
    * Else → `start = mid + 1`
* If loop exits → return `-1` (not found).

---

## 🔍 Working example — full trace tables (given array)

**Given**

```
arr = [0, 10, 5, 2]
target = 10
indices: 0  1  2  3
```

### A) `peakIM(arr)` trace (find peak index)

Initial: `start = 0`, `end = 3`

| Iter | start | end | mid = start + (end-start)/2 |  arr[mid] | arr[mid+1] | Condition (arr[mid] < arr[mid+1])? | Action                |
| ---- | ----- | --- | --------------------------: | --------: | ---------: | ---------------------------------: | --------------------- |
| 1    | 0     | 3   |                     mid = 1 | arr[1]=10 |   arr[2]=5 |                  10 < 5 ? → **No** | `end = mid = 1`       |
| 2    | 0     | 1   |                     mid = 0 |  arr[0]=0 |  arr[1]=10 |                 0 < 10 ? → **Yes** | `start = mid + 1 = 1` |

Now `start == end == 1`. Loop ends.
**peak = 1** (value `10`).

---

### B) `AgnosticBS(arr, target, 0, peak)` — search left half `[0..1]` (ascending)

Subarray indices: `start=0, end=1`, isAsc? `arr[0]=0 < arr[1]=10` → `isAsc = true`

| Iter | start | end | mid |  arr[mid] | Compare with target | Action                                    |
| ---- | ----- | --- | --- | --------: | ------------------: | ----------------------------------------- |
| 1    | 0     | 1   | 0   |  arr[0]=0 |        0 == 10 ? No | target > arr[mid] → `start = mid + 1 = 1` |
| 2    | 1     | 1   | 1   | arr[1]=10 |  10 == 10 ? **Yes** | return `mid = 1`                          |

Left search returns **1**.

Since leftTry != -1, `search()` returns `1` immediately. Done.

---

## Final output

```
1
```

(Which is correct — `10` is at index `1`.)

---

