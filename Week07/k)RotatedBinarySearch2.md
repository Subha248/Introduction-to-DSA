

```java
public class RBS {
    public static void main(String[] args) {
        int[] nums = { 4, 5, 6, 7, 0, 1, 2, 3 }; // rotated sorted array
        int target = 6;                          // value we want to find
        boolean ans = search(nums, target);          // call search
        System.out.println(ans);                 // print index of target
    }

    // Search function using pivot
    public static boolean search(int[] nums, int target) {
        int pivot = findPivot(nums); // find where the rotation happens

        if (pivot == -1) {
            // No rotation → normal ascending array
            return binarySearch(nums, target, 0, nums.length - 1);
        } else {
            // Pivot found → array split into two ascending parts
            if (nums[pivot] == target) return true;  // target is pivot itself

            if (target >= nums[0]) {
                // target lies in left part (start to pivot-1)
                return binarySearch(nums, target, 0, pivot - 1);
            } else {
                // target lies in right part (pivot+1 to end)
                return binarySearch(nums, target, pivot + 1, nums.length - 1);
            }
        }
    }

    // Normal binary search in ascending order
    public static boolean binarySearch(int[] nums, int target, int start, int end) {
        while (start <= end) {
            int mid = start + (end - start) / 2;

            if (nums[mid] == target) return true;      // found target
            else if (target < nums[mid]) end = mid - 1; // go left
            else start = mid + 1;                     // go right
        }
        return false; // target not found
    }

    // Find pivot index in rotated array
    public static int findPivot(int[] nums) {
        int start = 0;
        int end = nums.length - 1;

        while (start <= end) {
            int mid = start + (end - start) / 2;

            // Case 1: mid > next element → pivot at mid
            if (mid < end && nums[mid] > nums[mid + 1]) return mid;

            // Case 2: mid < previous element → pivot at mid-1
            if (mid > start && nums[mid] < nums[mid - 1]) return mid - 1;

            // Case 3 & 4: decide which side to search
            if (nums[mid] >= nums[start]) start = mid + 1; // mid in left sorted part → go right
            else end = mid - 1;                             // mid in right rotated part → go left
        }
        return -1; // no pivot found → array not rotated
    }
}
```

---

# Professional explanation — concise and structured

## Purpose

This program determines whether a given `target` exists in a rotated, sorted integer array `nums`. It uses a two-stage strategy:

1. Locate the **pivot** (index of the largest element, where the rotation occurs).
2. Run a binary search on the sorted half that could contain `target`.

Return type is `boolean` — `true` if `target` exists, `false` otherwise.

---

## High-level flow (method-by-method)

### `main`

* Builds the test array and `target`.
* Calls `search(...)`.
* Prints the boolean result.

### `search(int[] nums, int target)`

* Calls `findPivot(nums)` to detect rotation.

  * If `findPivot` returns `-1`, the array is not rotated → binary search the whole array.
  * If pivot is found:

    * If `nums[pivot] == target`, return `true`.
    * Else decide which side to search:

      * If `target >= nums[0]` → search left sorted segment `[0..pivot-1]`.
      * Otherwise search right sorted segment `[pivot+1..end]`.

Rationale: After rotation, array is two ascending subarrays (`nums[0..pivot]` and `nums[pivot+1..end]`).

### `binarySearch(int[] nums, int target, int start, int end)`

* Standard iterative binary search on inclusive interval `[start, end]`.
* Returns `true` if target found, otherwise `false`.

### `findPivot(int[] nums)`

* Binary-search style scan to find index `i` such that `nums[i] > nums[i+1]`.
* Checks:

  1. If `mid < end` and `nums[mid] > nums[mid+1]` ⇒ `mid` is pivot.
  2. If `mid > start` and `nums[mid] < nums[mid-1]` ⇒ `mid-1` is pivot.
  3. Else decide whether mid lies in left sorted part or right rotated part:

     * If `nums[mid] >= nums[start]` ⇒ left half sorted, pivot must be on the right ⇒ `start = mid + 1`.
     * Else ⇒ pivot on left ⇒ `end = mid - 1`.
* If loop completes without finding a pivot, return `-1` (array entirely sorted).

---

# Correctness notes

* The pivot-based split guarantees each half searched by `binarySearch` is sorted in ascending order, making binary search valid.
* The algorithm covers the case of no rotation (pivot = -1).
* `findPivot` assumes **no duplicates** or ignores duplicate-specific edge cases; behavior with duplicates may require additional handling if duplicates are expected.

---

# Complexity

* `findPivot`: O(log n) average, O(log n) best; works in O(log n) when elements provide a clear split.
* `binarySearch`: O(log n).
* Overall time: O(log n) average (two binary-search-like passes).
* Space: O(1).

---

# Dry run — concrete trace (your `main` example)

Input:

```
nums = [4, 5, 6, 7, 0, 1, 2, 3]
target = 6
```

### Step A — findPivot

* start = 0, end = 7, mid = 3 (value 7)
* Check `nums[3] > nums[4]` → `7 > 0` → true ⇒ pivot = 3

### Step B — search

* pivot = 3, `nums[3]` (7) != target (6)
* target >= nums[0]? → `6 >= 4` → true ⇒ search left half `[0 .. pivot-1]` i.e., indices `[0..2]`

### Step C — binarySearch on `[4,5,6]`

* start = 0, end = 2, mid = 1 → nums[1] = 5 → target > 5 → start = 2
* mid = 2 → nums[2] = 6 → match → return `true`

Final output printed: `true`

---

# Edge cases & recommendations (professional)

1. **Empty array**: `findPivot` and `binarySearch` assume `nums.length >= 1`. Add a guard `if (nums == null || nums.length == 0) return false;` in `search` if you need robustness.
2. **Single element**: Works fine (pivot = -1 and binary search checks single element).
3. **Duplicates**: Current `findPivot` logic (`nums[mid] >= nums[start]`) is correct for distinct elements. If array can contain duplicates, pivot detection can fail in edge cases — consider the duplicate-aware pivot routine (shrink edges when `nums[start] == nums[mid] == nums[end]`) if duplicates are expected.
4. **Return type**: Current API returns `boolean`. If you need the index of the target, change `binarySearch` and `search` to return `int` and preserve `-1` for not found.

---


