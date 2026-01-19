
---

# **LEETCODE153. Find Minimum in Rotated Sorted Array**

```java
public class RBS {
    public static void main(String[] args) {
        int[] nums = { 2, 3, 4, 5, 1 }; // rotated sorted array
        int ans = count(nums);          // call function to find minimum
        System.out.println(ans);        // print the minimum element
    }

    // Function to find minimum element using pivot
    public static int count(int[] nums) {
        int pivot = findpivot(nums);
        if (pivot == -1) return nums[0]; // array not rotated, first element is minimum
        else return nums[pivot + 1];     // minimum is element after pivot
    }

    // Function to find pivot (index of largest element)
    public static int findpivot(int[] nums) {
        int start = 0;
        int end = nums.length - 1;
        while (start <= end) {
            int mid = start + (end - start) / 2;

            // Case 1: mid > next element → pivot at mid
            if (end > mid && nums[mid] > nums[mid + 1]) return mid;

            // Case 2: mid < previous element → pivot at mid-1
            if (start < mid && nums[mid - 1] > nums[mid]) return mid - 1;

            // Case 3 & 4: decide which side to search
            if (nums[mid] >= nums[start]) start = mid + 1; // left side sorted → pivot on right
            else end = mid - 1;                             // pivot on left
        }
        return -1; // no pivot found → array not rotated
    }
}
```

---

# **Line-by-Line Explanation**

### **1. main()**

```java
int[] nums = { 2, 3, 4, 5, 1 };
int ans = count(nums);
System.out.println(ans);
```

* Initializes a rotated, sorted array.
* Calls `count(nums)` to find the **minimum element**.
* Prints the minimum.

---

### **2. count(int[] nums)**

```java
int pivot = findpivot(nums);
if (pivot == -1) return nums[0];
else return nums[pivot + 1];
```

* Calls `findpivot()` to locate the pivot (largest element).
* If pivot = -1 → array not rotated → first element is the minimum.
* Otherwise, minimum element is **immediately after the pivot** (`nums[pivot + 1]`).

---

### **3. findpivot(int[] nums)**

```java
int start = 0;
int end = nums.length - 1;
while (start <= end) {
    int mid = start + (end - start) / 2;

    if (end > mid && nums[mid] > nums[mid + 1]) return mid;
    if (start < mid && nums[mid - 1] > nums[mid]) return mid - 1;

    if (nums[mid] >= nums[start]) start = mid + 1;
    else end = mid - 1;
}
return -1;
```

* Binary search to find the pivot index.
* Pivot is the largest element where the drop occurs (`nums[i] > nums[i+1]`).
* If `nums[mid] >= nums[start]`, left side is sorted → pivot is on right.
* Else, pivot is on left.
* Returns `-1` if no pivot is found (array is fully ascending).

---

# **Dry Run Example**

Array: `{2,3,4,5,1}`

1. `start=0`, `end=4`, `mid=2` → `nums[2]=4`

   * `nums[2] > nums[3]?` → false
   * `nums[1] > nums[2]?` → false
   * `nums[2] >= nums[0]?` → true → `start = mid + 1 = 3`

2. Next iteration: `start=3`, `end=4`, `mid=3` → `nums[3]=5`

   * `nums[3] > nums[4]?` → `5 > 1` → true → pivot = 3

3. In `count()` → minimum = `nums[pivot + 1] = nums[4] = 1`

**Output:**

```
1
```

---

# **Notes**

1. Correctly handles rotated arrays with distinct elements.
2. Time complexity: O(log n)
3. Space complexity: O(1)
4. Edge case: If array is empty → currently not handled (would throw exception).

---

