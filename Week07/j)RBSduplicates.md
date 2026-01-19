
**SEARCH IN ROATED SORTED ARRAY WITH DUPLICATE VALUES**
```java
public class RBS {
    public static void main(String[] args) {
        int[] nums = {4,5,6,6,7,0,1,2,4,4};
        int target = 7;
        int ans = search(nums, target);
        System.out.println(ans); // expected 4
    }

    public static int search(int[] nums, int target) {
        if (nums == null || nums.length == 0) return -1;
        if (nums.length == 1) return nums[0] == target ? 0 : -1;

        int pivot = findPivotWithDups(nums);

        if (pivot == -1) { // array not rotated
            return binarySearch(nums, target, 0, nums.length - 1);
        } else { // pivot found
            if (nums[pivot] == target) return pivot;
            if (target >= nums[0]) return binarySearch(nums, target, 0, pivot - 1);
            return binarySearch(nums, target, pivot + 1, nums.length - 1);
        }
    }

    public static int binarySearch(int[] nums, int target, int start, int end) {
        while (start <= end) {
            int mid = start + (end - start) / 2;
            if (nums[mid] == target) return mid;
            else if (target < nums[mid]) end = mid - 1;
            else start = mid + 1;
        }
        return -1;
    }

    public static int findPivotWithDups(int[] nums) {
        int start = 0;
        int end = nums.length - 1;

        while (start <= end) {
            int mid = start + (end - start) / 2;

            // CASE 1: mid is pivot (mid > mid+1)
            if (mid < end && nums[mid] > nums[mid + 1]) return mid;

            // CASE 2: mid-1 is pivot (mid < mid-1)
            if (mid > start && nums[mid] < nums[mid - 1]) return mid - 1;

            // CASE 3: duplicates at start, mid, end -> shrink safely
            if (nums[mid] == nums[start] && nums[mid] == nums[end]) {
                // check if start is pivot (safe check: start+1 exists)
                if (start < end && nums[start] > nums[start + 1]) return start;
                start++;

                // check if end-1 is pivot (safe check: end-1 >= start)
                if (end > start && nums[end - 1] > nums[end]) return end - 1;
                end--;
                continue;
            }

            // CASE 4: decide which side to go based on sorted halves
            if (nums[mid] > nums[start] || (nums[mid] == nums[start] && nums[mid] > nums[end])) {
                // left side is strictly increasing -> pivot must be on the right
                start = mid + 1;
            } else {
                // pivot is on the left side
                end = mid - 1;
            }
        }

        return -1; // pivot not found -> array fully sorted ascending
    }
}
```

---

# Line-by-line explanation (neat & short)

### Top-level / `main`

* `int[] nums = {...}` — your rotated array with duplicates.
* `int target = 7` — value to search.
* `int ans = search(nums, target)` — runs the algorithm.
* `System.out.println(ans)` — prints index or `-1`.

### `search(nums, target)`

* Guard for empty or single-element arrays.
* `pivot = findPivotWithDups(nums)` — find index of max element where rotation happens.
* If `pivot == -1`: array not rotated → binary search whole array.
* Else:

  * If `nums[pivot] == target` → return pivot.
  * If `target >= nums[0]` → target is in left sorted chunk `0..pivot-1`.
  * Else → target is in right sorted chunk `pivot+1..end`.

### `binarySearch(nums, target, start, end)`

* Standard iterative binary search: compute `mid`, compare, move `start` or `end`.
* Return index when found, else `-1`.

### `findPivotWithDups(nums)`

Goal: return index `i` such that `nums[i] > nums[i+1]` (the pivot), or `-1` if array is strictly sorted.

Loop invariant: searching for the drop point.

1. `mid = start + (end - start)/2` — safe mid.
2. **Case 1:** `if (mid < end && nums[mid] > nums[mid+1]) return mid;`

   * Found pivot at `mid`.
3. **Case 2:** `if (mid > start && nums[mid] < nums[mid-1]) return mid - 1;`

   * Found pivot at `mid-1`.
4. **Case 3 (duplicates at edges):** `if nums[start] == nums[mid] == nums[end]`

   * We can’t infer the pivot side → check ends safely:

     * If `start < end && nums[start] > nums[start+1]` → `start` is pivot.
     * Else `start++` (shrink from left).
     * If `end > start && nums[end-1] > nums[end]` → `end-1` is pivot.
     * Else `end--` (shrink from right).
   * `continue` after shrinking (skip the normal-case logic for this iteration).
   * These safe checks prevent `start+1` or `end-1` going out of bounds.
5. **Case 4 (normal non-duplicate decision):**

   * If left half is strictly increasing (`nums[mid] > nums[start]`) OR `nums[mid] == nums[start]` but `nums[mid] > nums[end]`, pivot is to the **right** → `start = mid + 1`.
   * Else pivot is to the **left** → `end = mid - 1`.
6. If loop finishes, return `-1` (no pivot found).

---

# Dry runs (two examples) — show indices & checks

## Dry run A — your array (expected output `4`)

Array: `4,5,6,6,7,0,1,2,4,4`
Indices: 0..9, target = 7

1. `search` → `findPivotWithDups`.
2. `start=0`, `end=9`, `mid=4`.

   * Check `nums[4] > nums[5]`? `7 > 0` → true → return `4`.
3. Back in `search`: `pivot=4`. `nums[4] == target` → return `4`.
   Output: `4`.

---

## Dry run B — fully sorted (no rotation) `[1,2,3,4,5]`, target 3 (expected output `2`)

Array: `1,2,3,4,5`, indices 0..4

1. `findPivotWithDups`:

   * `start=0,end=4,mid=2`.
   * `nums[2] > nums[3]?` `3>4` false.
   * `nums[2] < nums[1]?` `3<2` false.
   * Dups case? `nums[start]==nums[mid]==nums[end]?` no.
   * `nums[mid] > nums[start]?` `3>1` true → `start = mid+1 = 3`.
   * Next iter: `start=3,end=4,mid=3`.
   * Check `nums[3] > nums[4]?` `4>5` false.
   * `nums[3] < nums[2]?` `4<3` false.
   * Not dup block. `nums[3] > nums[start]?` `4>4` false. `(nums[mid]==nums[start] && nums[mid]>nums[end])?` false.
   * Else `end = mid-1 = 2`.
   * Now `start(3) > end(2)` → loop exits → return `-1`.
2. `pivot == -1` → binary search whole array → finds target at index `2`.
   Output: `2`.

---

# Complexity & notes

* Time: average/best `O(log n)`. Worst-case `O(n)` if many duplicates force linear shrinking (Case 3).
* Space: `O(1)` extra.
* Behavior: returns *any* valid index holding `target`. If duplicates of `target` exist, not guaranteed to be first/last occurrence.

---

