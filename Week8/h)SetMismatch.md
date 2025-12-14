https://leetcode.com/problems/set-mismatch/
645. Set Mismatch
---

## **CODE **

```java
class Solution {
    public int[] findErrorNums(int[] nums) {
        int i = 0;

        while (i < nums.length) {
            int correct = nums[i] - 1;          // correct index
            if (nums[i] != nums[correct]) {
                swap(nums, i, correct);         // place number correctly
            } else {
                i++;                            // already correct or duplicate
            }
        }

        for (int index = 0; index < nums.length; index++) {
            if (nums[index] != index + 1) {
                return new int[]{nums[index], index + 1}; // duplicate, missing
            }
        }
        return new int[]{-1, -1};
    }

    void swap(int[] nums, int a, int b) {
        int temp = nums[a];
        nums[a] = nums[b];
        nums[b] = temp;
    }
}
```

---

## **DRY RUN**

### **Input:** `nums = [1,2,2,4]`

**Start:** `[1,2,2,4]`

* i=0 → nums[0]=1 ✔ → i++
* i=1 → nums[1]=2 ✔ → i++
* i=2 → nums[2]=2 ≠ 3
  correct=1 → nums[2]==nums[1] → duplicate → i++
* i=3 → nums[3]=4 ✔ → i++

**After cyclic sort:**
`[1,2,2,4]`

---

### **Scan Array**

* index 0 → 1 ✔
* index 1 → 2 ✔
* index 2 → 2 ❌ (should be 3)

👉 **Duplicate = 2**
👉 **Missing = 3**

---

## **OUTPUT**

```java
[2, 3]
```

