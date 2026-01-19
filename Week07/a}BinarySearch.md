
---

### **Your Binary Search Code (Corrected)**

```java
public class Binary {
    public static void main(String[] args) {
        int[] arr = {-18, -12, -4, 0, 2, 3, 4, 15, 16, 18, 22, 45, 89};
        int target = 2;

        int ans = binarysearch(arr, target);
        System.out.print(ans);
    }

    public static int binarysearch(int[] arr, int target) {
        int start = 0;
        int end = arr.length - 1;

        while (start <= end) {                 // loop until search space exists
            int mid = start + (end - start)/2; // safe mid calculation

            if (target < arr[mid]) {           // target is smaller → go left
                end = mid - 1;
            } else if (target > arr[mid]) {    // target is bigger → go right
                start = mid + 1;
            } else {                            // target == arr[mid]
                return mid;                     // return index
            }
        }

        return -1;  // target not found
    }
}
```

---

### **Step-by-step explanation with your array**

Array:

```
arr = {-18, -12, -4, 0, 2, 3, 4, 15, 16, 18, 22, 45, 89}
indexes = 0   1   2  3  4  5  6   7   8   9   10  11  12
target = 2
```

---

#### **Step 0: Initialize**

```
start = 0
end = 12
```

---

#### **Step 1: Calculate mid**

```
mid = start + (end - start)/2
mid = 0 + (12 - 0)/2
mid = 6
arr[mid] = arr[6] = 4
```

* Compare: `2 < 4` → move left
* Update `end = mid - 1 = 5`

Pointers now:

```
start = 0, end = 5
```

---

#### **Step 2: Calculate mid**

```
mid = start + (end - start)/2
mid = 0 + (5 - 0)/2
mid = 2
arr[mid] = arr[2] = -4
```

* Compare: `2 > -4` → move right
* Update `start = mid + 1 = 3`

Pointers now:

```
start = 3, end = 5
```

---

#### **Step 3: Calculate mid**

```
mid = start + (end - start)/2
mid = 3 + (5 - 3)/2
mid = 3 + 2/2
mid = 3 + 1 = 4
arr[mid] = arr[4] = 2
```

* Compare: `2 == 2` → **found target**
* Return `mid = 4` ✅

---

### **Pointer movement visual**

| Step | start | end | mid | arr[mid] | Action             |
| ---- | ----- | --- | --- | -------- | ------------------ |
| 1    | 0     | 12  | 6   | 4        | 2 < 4 → end = 5    |
| 2    | 0     | 5   | 2   | -4       | 2 > -4 → start = 3 |
| 3    | 3     | 5   | 4   | 2        | 2 == 2 → return 4  |

---

### ✅ **Summary**

1. Start with full array → calculate mid.
2. If target < mid → go left. If target > mid → go right.
3. Repeat until `start > end` or target is found.
4. Return `-1` if target isn’t in the array.

---

