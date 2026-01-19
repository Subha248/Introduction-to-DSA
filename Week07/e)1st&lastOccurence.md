 **First + last occurrence code** with **full working Java code**
---

## ✅ Full Code

```java
class Solution {

    public int[] searchRange(int[] nums, int target) {
        // Step 1: Initialize answer array with default -1
        int[] ans = {-1, -1};

        // Step 2: Find first occurrence
        ans[0] = search(nums, target, true);

        // Step 3: Only if target exists, find last occurrence
        if (ans[0] != -1) {
            ans[1] = search(nums, target, false);
        }

        // Step 4: Return the range [first, last]
        return ans;
    }

    // Binary search helper function
    public int search(int[] nums, int target, boolean findStartIndex) {
        int ans = -1;                 // default answer if target not found
        int start = 0;
        int end = nums.length - 1;

        while (start <= end) {
            int mid = start + (end - start) / 2;  // safe middle calculation

            if (target < nums[mid]) {
                end = mid - 1;          // target is smaller → search left
            } 
            else if (target > nums[mid]) {
                start = mid + 1;        // target is bigger → search right
            } 
            else {
                // target == nums[mid] → potential answer found
                ans = mid;

                if (findStartIndex) {
                    end = mid - 1;      // move left to find first occurrence
                } else {
                    start = mid + 1;    // move right to find last occurrence
                }
            }
        }

        return ans;                     // return the first/last index found, or -1
    }

}
```

---

## 🔍 Explanation Step by Step

### 1️⃣ `int[] ans = {-1, -1};`

* Initialize answer array with **-1** for both first and last indices.
* This is the “target not found” value.

### 2️⃣ `ans[0] = search(nums, target, true);`

* Calls `search()` to find **first occurrence**.
* `true` → tells the search function to **move left** if target is found (keep checking for earlier occurrences).

### 3️⃣ `if (ans[0] != -1) { ans[1] = search(nums, target, false); }`

* Only search for last occurrence if first occurrence exists.
* `false` → tells search to **move right** if target is found (keep checking for later occurrences).

### 4️⃣ `return ans;`

* Returns `[firstIndex, lastIndex]`.
* Example:

```java
nums = [1,2,2,2,3]
target = 2
ans = [1,3]
```

---

### 5️⃣ `search()` function

* Standard binary search with a small twist:

  * Whenever we find `target == nums[mid]`:

    * Store `mid` in `ans`
    * Move `end = mid - 1` if finding **first**
    * Move `start = mid + 1` if finding **last**
* Keeps searching until the **best index** is found.

---

### ✅ Why `ans` is needed

* You **can’t return immediately** because you need **first or last occurrence**, not just any occurrence.
* `ans` stores the best index seen so far.
* Returns `-1` if target never exists.

---

### 6️⃣ Flow Visualization (Example)

`nums = [1,2,2,2,3]`, `target = 2`

**First occurrence search**:

```
start=0, end=4
mid=2 → nums[2]=2 → match → ans=2 → move left → end=1
mid=0 → nums[0]=1 → target>nums[mid] → start=1
mid=1 → nums[1]=2 → match → ans=1 → move left → end=0
loop ends → first occurrence = ans=1
```

**Last occurrence search**:

```
start=0, end=4
mid=2 → nums[2]=2 → match → ans=2 → move right → start=3
mid=3 → nums[3]=2 → match → ans=3 → move right → start=4
mid=4 → nums[4]=3 → target<nums[mid] → end=3
loop ends → last occurrence = ans=3
```

Result → `[1,3]` ✅

---


