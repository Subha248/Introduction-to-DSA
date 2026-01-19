

# **📌 Insertion Sort **

---

# **🔹 1. Code **

```java
import java.util.Arrays;

public class sort{
  public static void main(String[] args){
    int[] arr={5,3,4,1,2};
    insertion(arr);
    System.out.print(Arrays.toString(arr));
  }

  public static void insertion(int[] arr){
    for(int i=0;i<arr.length-1;i++){
      for(int j=i+1;j>0;j--){
        if(arr[j]<arr[j-1]) {
          swap(arr,j,j-1);
        }
      }
    }
  }

  public static void swap(int[] arr, int start,int second){
    int temp=arr[start];
    arr[start]=arr[second];
    arr[second]=temp;
  }
}
```

---

# **🔹 2. Step-by-Step Explanation**

## **▶ main()**

* Creates array: `{5,3,4,1,2}`
* Calls `insertion(arr)`
* Prints final sorted array

---

## **▶ insertion(arr)**

### **Outer loop:**

`for (int i = 0; i < arr.length - 1; i++)`

* Picks the next element to insert

### **Inner loop:**

`for (int j = i + 1; j > 0; j--)`

* Moves that element left until it reaches correct sorted position

### **Swap condition:**

`if (arr[j] < arr[j - 1])`

* If current element is smaller than previous → swap them

---

## **▶ swap(arr, j, j-1)**

Standard 3-variable swap.

---

# **🔹 3. Dry Run (Iteration by Iteration)**

Initial array:

```
[5, 3, 4, 1, 2]
```

---

## **🟦 Iteration 1 — i = 0**

### `j = 1`

* Compare 3 and 5
* 3 < 5 → swap
  Result:

```
[3, 5, 4, 1, 2]
```

---

## **🟦 Iteration 2 — i = 1**

### j = 2

* 4 < 5 → swap
  → `[3, 4, 5, 1, 2]`

### j = 1

* 4 < 3? → No
  Array stays:

```
[3, 4, 5, 1, 2]
```

---

## **🟦 Iteration 3 — i = 2**

### j = 3

* 1 < 5 → swap
  → `[3, 4, 1, 5, 2]`

### j = 2

* 1 < 4 → swap
  → `[3, 1, 4, 5, 2]`

### j = 1

* 1 < 3 → swap
  → `[1, 3, 4, 5, 2]`

---

## **🟦 Iteration 4 — i = 3**

### j = 4

* 2 < 5 → swap
  → `[1, 3, 4, 2, 5]`

### j = 3

* 2 < 4 → swap
  → `[1, 3, 2, 4, 5]`

### j = 2

* 2 < 3 → swap
  → `[1, 2, 3, 4, 5]`

### j = 1

* 2 < 1? → No

---

# **🔹 4. Final Output**

```
[1, 2, 3, 4, 5]
```

---
---
### **Time Complexity**

* **Worst case:** O(n²)
  (when the array is reverse-sorted → every element keeps shifting)
* **Average case:** O(n²)
* **Best case:** O(n)
  (when the array is already sorted → only one pass, no swaps)

---

### **Why Insertion Sort is Stable**

Because it **never jumps over equal elements**.

When `arr[j] < arr[j-1]`, it swaps.
But when `arr[j] == arr[j-1]`, it **does nothing**.
So the original order of equal elements stays the same.

Example:

```
(5a, 5b)
```

Both equal.
Insertion sort won’t flip them.
Order is preserved → **stable**.

---


