
---

## **Problem**

Given an array:

```java
int[] arr = {1, 2, 3, 4, 5};
```

Reverse it **in-place** so it becomes:

```
{5, 4, 3, 2, 1}
```

---

## **Approach 1: Two-pointer swap (in-place, O(n))**

**Idea:**

* Start with two pointers: `start = 0` and `end = arr.length - 1`
* Swap elements at `start` and `end`
* Move `start++` and `end--`
* Repeat until `start >= end`

**Code:**

```java
public class Main {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};

        int start = 0;
        int end = arr.length - 1;

        while (start < end) {
            // swap arr[start] and arr[end]
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;

            start++;
            end--;
        }

        // print reversed array
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

**Output:**

```
5 4 3 2 1
```

---
### EXPLANATION
### **Initial Array**

```
arr = {1, 2, 3, 4, 5}
start = 0, end = 4
```

---

### **Step 1: Swap first and last**

* Swap `arr[start]` and `arr[end]` → `arr[0]` ↔ `arr[4]`
* Array after swap:

```
arr = {5, 2, 3, 4, 1}
```

* Move pointers: `start = 1`, `end = 3`

---

### **Step 2: Swap second and second-last**

* Swap `arr[start]` and `arr[end]` → `arr[1]` ↔ `arr[3]`
* Array after swap:

```
arr = {5, 4, 3, 2, 1}
```

* Move pointers: `start = 2`, `end = 2`

---

### **Step 3: Stop Condition**

* `start = 2`, `end = 2` → `start >= end` → stop
* Final reversed array:

```
arr = {5, 4, 3, 2, 1}
```

---

### **Pointer Movement Summary**

| Step | start | end | Swap Elements       | Array State     |
| ---- | ----- | --- | ------------------- | --------------- |
| 1    | 0     | 4   | 1 ↔ 5               | {5, 2, 3, 4, 1} |
| 2    | 1     | 3   | 2 ↔ 4               | {5, 4, 3, 2, 1} |
| 3    | 2     | 2   | Stop (start >= end) | {5, 4, 3, 2, 1} |

---

✅ **Result:** Array is reversed **in-place** without extra space.


💡 **Tips for DSA:**

* Always try **in-place swap first**.
* Think: “swap first & last, then move inwards.”
* Works for arrays, strings (char arrays), and sometimes linked lists.

---

---
