https://leetcode.com/problems/first-missing-positive/
---
### HARD QUES AMAZON
### **Code **

```java
import java.util.Arrays;

public class sort {
    public static void main(String[] args) {
        int[] nums = {1, 2, 0};           // input array
        int missing = cyclic(nums);        // call method to find missing
        System.out.println(missing);       // print result
    }

    public static int cyclic(int[] nums) {
        int i = 0;                         // start index
        while (i < nums.length) {
            int correct = nums[i] - 1;     // correct index for nums[i]
            if (nums[i] > 0 && nums[i] <= nums.length && nums[i] != nums[correct]) {
                swap(nums, i, correct);    // swap into correct position
            } else {
                i++;                       // move to next
            }
        }

        for (int index = 0; index < nums.length; index++) {
            if (nums[index] != index + 1) return index + 1; // first mismatch = missing
        }

        return nums.length + 1;             // all 1..n present → missing is n+1
    }

    public static void swap(int[] nums, int first, int next) {
        int temp = nums[first];             // store first
        nums[first] = nums[next];           // swap
        nums[next] = temp;                  // complete swap
    }
}
```

---

### **Explanation**

1. **Cyclic sort idea**:

   * Place each number `x` at index `x-1` if valid (`1..n`).
   * Ignore invalid numbers (like `0` or numbers > n).

2. **Finding missing number**:

   * After sorting, array indices should match numbers (`nums[i] = i+1`).
   * First index where this is false → `i+1` is the missing number.

3. **Return `n+1`**:

   * If array contains all numbers from `1..n`, then the smallest missing positive is `n+1`.

---

### **Dry Run: nums = [1, 2, 0]**

**Step 1: While loop**

| i | nums[i] | correct | Action                   | Array after step |
| - | ------- | ------- | ------------------------ | ---------------- |
| 0 | 1       | 0       | already correct → i++    | [1,2,0]          |
| 1 | 2       | 1       | already correct → i++    | [1,2,0]          |
| 2 | 0       | -1      | nums[i] ≤ 0 → skip → i++ | [1,2,0]          |

**Step 2: For loop**

| index | nums[index] | expected | Match? |
| ----- | ----------- | -------- | ------ |
| 0     | 1           | 1        | ✅      |
| 1     | 2           | 2        | ✅      |
| 2     | 0           | 3        | ❌      |

* First mismatch → missing number = `3`

**Step 3: Output**

```
3
```

