https://leetcode.com/problems/search-in-rotated-sorted-array/description/
---

# **Code: Rotated Binary Search (RBS)**

```java
public class RBS {
    public static void main(String[] args) {
        int[] nums = { 4, 5, 6, 7, 0, 1, 2, 3 }; // rotated sorted array
        int target = 6;                          // value we want to find
        int ans = search(nums, target);          // call search
        System.out.println(ans);                 // print index of target
    }

    // Search function using pivot
    public static int search(int[] nums, int target) {
        int pivot = findPivot(nums); // find where the rotation happens

        if (pivot == -1) {
            // No rotation → normal ascending array
            return binarySearch(nums, target, 0, nums.length - 1);
        } else {
            // Pivot found → array split into two ascending parts
            if (nums[pivot] == target) return pivot;  // target is pivot itself

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
    public static int binarySearch(int[] nums, int target, int start, int end) {
        while (start <= end) {
            int mid = start + (end - start) / 2;

            if (nums[mid] == target) return mid;      // found target
            else if (target < nums[mid]) end = mid - 1; // go left
            else start = mid + 1;                     // go right
        }
        return -1; // target not found
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

# **Step-by-Step Explanation with Example**

### **Array**

```
nums = [4, 5, 6, 7, 0, 1, 2, 3]
target = 6
```

---

## **Step 1: Find Pivot**

Variables: `start=0`, `end=7`

| Iter | start | end | mid | nums[mid] | Case fired | Action                    |
| ---- | ----- | --- | --- | --------- | ---------- | ------------------------- |
| 1    | 0     | 7   | 3   | 7         | Case 1     | nums[3]>nums[4] → pivot=3 |

* Pivot index = 3
* Pivot value = 7
* Array split: `[4,5,6,7]` (left), `[0,1,2,3]` (right)

---

## **Step 2: Decide which half to search**

* Compare target (6) with `nums[0]` = 4
* `6 >= 4` → target is in left half `[0..pivot-1] = [0..2]`

---

## **Step 3: Binary Search in left half**

Array slice: `[4,5,6]` → start=0, end=2

| Iter | start | end | mid | nums[mid] | Action                       |
| ---- | ----- | --- | --- | --------- | ---------------------------- |
| 1    | 0     | 2   | 1   | 5         | 6>5 → start=mid+1=2          |
| 2    | 2     | 2   | 2   | 6         | nums[mid]==target → return 2 |

✅ Found target at index = 2

---

## **Step 4: How Cases in `findPivot` work**

* **Case 1:** mid > next → pivot is mid
* **Case 2:** mid < previous → pivot is mid-1
* **Case 3:** mid >= start → mid in left sorted part → go right
* **Case 4:** mid < start → mid in right rotated part → go left

> These four cases **guarantee the pivot is found** in O(log n) time.

---

### **Key Notes**

1. `search()` checks if pivot exists → decides which half to binary search
2. `binarySearch()` is normal ascending BS
3. `findPivot()` is modified BS for rotated array

---

💡 **Visual Summary**

```
Original rotated array: [4,5,6,7,0,1,2,3]
Pivot found at index 3 (value=7)

Left half:  [4,5,6]   -> target=6 → found at index 2
Right half: [0,1,2,3] -> not searched
```

---


