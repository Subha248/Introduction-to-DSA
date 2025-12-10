
---

## ** Code **

```java
import java.util.Arrays;
public class sort{
  public static void main(String[] args){
    int[] arr={3,5,4,1,2};
    cyclic(arr);
    System.out.println(Arrays.toString(arr));
    
  }//cyclic sort always takes value from 1 to N in order like 1,2,3,... 
  public static void cyclic(int[] arr){
    int i=0;
    while(i<arr.length){
      int correctInd=arr[i]-1;   // because element 3 index is 2, that's the correct index of element 3 
      if(arr[i]!=arr[correctInd]){
        swap(arr,i,correctInd);
      }
      else i++;
    }
  }
  public static void swap(int[] arr, int first,int next){
    int temp=arr[first];
    arr[first]=arr[next];
    arr[next]=temp;
  }
}
```

---

## ** Explanation **

### **Line-by-line logic**

* The array must contain numbers from **1 to N**, no gaps.

* `i = 0` starts from the first index.

* `correctInd = arr[i] - 1;`
  Every element belongs to the index:
  `value 1 → index 0`
  `value 2 → index 1`
  …
  `value x → index x-1`

* If the element is **not** at its correct index → swap it to its correct position.

* If the element **is** at the correct index → move to the next index (`i++`).

* This keeps looping until every element is in the position it belongs.

* `swap()` just swaps two elements.

Cyclic sort basically says:
“Yo, if you don’t belong here, go home.”
And keeps throwing every value to its correct index.

---

## **Dry Run (your array: `[3,5,4,1,2]`)**

### **Start:**

```
i = 0  
arr = [3,5,4,1,2]
```

**arr[0] = 3 → correct index = 2**
`arr[0] != arr[2]`
Swap index 0 and 2.

→ `[4,5,3,1,2]`

---

### **i = 0 again** (we don't increase i until it's correct)

**arr[0] = 4 → correct index = 3**
`arr[0] != arr[3]`
Swap 0 and 3.

→ `[1,5,3,4,2]`

---

### **i = 0 again**

**arr[0] = 1 → correct index = 0**
`arr[0] == arr[0]`
Now it's at the right spot → `i++`

i = 1

---

### **i = 1**

**arr[1] = 5 → correct index = 4**
Swap 1 and 4.

→ `[1,2,3,4,5]`

---

### **i = 1 again**

arr[1] = 2 → correct index = 1
Correct → `i++` → i = 2

---

### **i = 2**

arr[2] = 3 → correct → `i++`

### **i = 3**

arr[3] = 4 → correct → `i++`

### **i = 4**

arr[4] = 5 → correct → `i++`

### **i = 5 → loop ends**

**Final Array:**
`[1,2,3,4,5]`

---

## **Important Points to Remember (only the critical ones)**

* Works ONLY when array contains **1 to N** numbers.
* Time complexity: **O(n)**
  (Each element goes straight to its correct index.)
* Space complexity: **O(1)**
* Not stable (swapping throws equal elements around).
* Perfect for:

  * Missing number
  * Duplicate number
  * Set mismatch
  * First missing positive
  * Sorting 1 to N arrays

---

