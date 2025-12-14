https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/

# Complete Code with Step-by-Step Explanation

```java
import java.util.List;
import java.util.ArrayList;

class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        // STEP 1: Apply Cyclic Sort to put each number in its correct position
        int i = 0;
        while (i < nums.length) {
            // Correct index for the current number
            // Since numbers are from 1 to n, correct index = number - 1
            int correctIndex = nums[i] - 1;
            
            // Check if the number is not at its correct position
            // Also check if the number at correct position is different from current number
            if (nums[i] != nums[correctIndex]) {
                // Swap current number with the number at its correct position
                swap(nums, i, correctIndex);
            } else {
                // If number is already at correct position OR
                // Duplicate number found (can't be placed), move to next index
                i++;
            }
        }
        
        // STEP 2: Find missing numbers
        List<Integer> missingNumbers = new ArrayList<>();
        for (int index = 0; index < nums.length; index++) {
            // After cyclic sort, each number should be at index (number-1)
            // So if nums[index] != index + 1, then (index + 1) is missing
            if (nums[index] != index + 1) {
                missingNumbers.add(index + 1);
            }
        }
        
        // STEP 3: Return the list of missing numbers
        return missingNumbers;
    }
    
    // Helper method to swap two elements in the array
    private void swap(int[] arr, int first, int second) {
        int temp = arr[first];
        arr[first] = arr[second];
        arr[second] = temp;
    }
}
```

## Step-by-Step Walkthrough with Example:

Let's use `nums = [4, 3, 2, 7, 8, 2, 3, 1]` (n = 8, numbers should be 1-8)

### **STEP 1: Cyclic Sort Phase**

**i = 0:** `nums[0] = 4`

* `correctIndex = 4 - 1 = 3`
* Check: `nums[0] (4) != nums[3] (7)` → True
* Swap index 0 with index 3: `[7, 3, 2, 4, 8, 2, 3, 1]`
* i stays at 0 (because we swapped)

**i = 0:** `nums[0] = 7`

* `correctIndex = 7 - 1 = 6`
* Check: `nums[0] (7) != nums[6] (3)` → True
* Swap: `[3, 3, 2, 4, 8, 2, 7, 1]`

**i = 0:** `nums[0] = 3`

* `correctIndex = 3 - 1 = 2`
* Check: `nums[0] (3) != nums[2] (2)` → True
* Swap: `[2, 3, 3, 4, 8, 2, 7, 1]`

**i = 0:** `nums[0] = 2`

* `correctIndex = 2 - 1 = 1`
* Check: `nums[0] (2) != nums[1] (3)` → True
* Swap: `[3, 2, 3, 4, 8, 2, 7, 1]`

**i = 0:** `nums[0] = 3`

* `correctIndex = 3 - 1 = 2`
* Check: `nums[0] (3) != nums[2] (3)` → False (duplicate!)
* i++ → i = 1

**i = 1:** `nums[1] = 2`

* `correctIndex = 2 - 1 = 1`
* Check: `nums[1] (2) != nums[1] (2)` → False (already correct!)
* i++ → i = 2

**Continue this process...**

**Final sorted array after cyclic sort:**
`[1, 2, 3, 4, 3, 2, 7, 8]`

Notice: Positions 0-3 are correct (1,2,3,4), but positions 4-7 have wrong values!

### **STEP 2: Find Missing Numbers**

Now scan the sorted array:

* Index 0: `nums[0] = 1` should be `1` ✓
* Index 1: `nums[1] = 2` should be `2` ✓
* Index 2: `nums[2] = 3` should be `3` ✓
* Index 3: `nums[3] = 4` should be `4` ✓
* Index 4: `nums[4] = 3` should be `5` ❌ → **5 is missing!**
* Index 5: `nums[5] = 2` should be `6` ❌ → **6 is missing!**
* Index 6: `nums[6] = 7` should be `7` ✓
* Index 7: `nums[7] = 8` should be `8` ✓

### **STEP 3: Return Result**

Missing numbers:
`[5, 6]`

## Why This Works:

1. **Cyclic Sort puts each number at index (number-1)**

   * After sorting, number `x` will be at position `x-1` (if it exists in array)

2. **Missing numbers reveal themselves**

   * If position `i` doesn't contain `i+1`, then `i+1` is missing
   * Duplicates occupy positions of missing numbers

3. **Time Complexity: O(n)**

   * Each element is placed at its correct position at most once
   * We traverse array twice: once for sorting, once for finding missing

4. **Space Complexity: O(1)** (excluding output list)

   * Sorting is done in-place
   * Only extra space is for the output

## Key Insight:

The magic is that **duplicates don't break the algorithm** — they just mean some numbers are missing! When we encounter duplicates, we skip them and continue.

Clean. Solid. Interview-ready. 🚀
