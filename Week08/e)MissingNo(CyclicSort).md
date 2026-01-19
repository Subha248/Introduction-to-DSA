

---

```java
import java.util.Arrays;                   // Unused import - can be removed

public class sort {                        // Class name (should be Sort per Java conventions)
    public static void main(String[] args) {  // Main method - program entry point
        int[] arr = {0, 3, 1, 2, 5};      // Initialize array with numbers 0-5 (4 is missing)
        int missing = cyclic(arr);         // Call cyclic sort method to find missing number
        System.out.println(missing);       // Print result: 4
    }
    
    public static int cyclic(int[] arr) {  // Method that finds missing number using cyclic sort
        int i = 0;                         // Initialize index pointer for while loop
        
        while (i < arr.length) {           // Loop through array until end
            int correct = arr[i];          // Get value at current position - this is where it should be
            
            // Check: 1) Value is within array bounds (0 to n-1)
            //        2) Value is NOT at its correct position
            if (arr[i] < arr.length && arr[i] != arr[correct]) {
                swap(arr, i, correct);     // Swap current element to its correct position
            } else {
                i++;                       // Move to next element (either in correct position or out of range)
            }
        }
        
        // After sorting, find first index where value doesn't match index
        for (int index = 0; index < arr.length; index++) {
            if (arr[index] != index) {     // If value at index is not equal to index
                return index;              // This index is the missing number
            }
        }
        
        return arr.length;                 // If all indices match values, missing number is n
    }
    
    public static void swap(int[] arr, int first, int next) {  // Standard swap utility
        int temp = arr[first];            // Store first element in temporary variable
        arr[first] = arr[next];           // Replace first element with second element
        arr[next] = temp;                 // Replace second element with stored first element
    }
}
```

---

## Explanation

This solution uses **Cyclic Sort logic** to find the **missing number** in an array containing numbers from `0` to `n`.

Core idea:

* Every number should be placed at the index equal to its value.
* If a number is within range `0 to n-1` and not at its correct index, swap it.
* After rearranging, the index where `arr[index] != index` is the missing number.

---

## Dry Run

### Initial array

```
arr = [0, 3, 1, 2, 5]
length = 5
```

---

### While loop execution

**i = 0**

* arr[0] = 0
* correct = 0
* arr[0] == arr[correct] → correct position
  → i++

Array: `[0, 3, 1, 2, 5]`

---

**i = 1**

* arr[1] = 3
* correct = 3
* arr[1] != arr[3] → swap(1, 3)

After swap:

```
[0, 2, 1, 3, 5]
```

---

**i = 1 (again)**

* arr[1] = 2
* correct = 2
* arr[1] != arr[2] → swap(1, 2)

After swap:

```
[0, 1, 2, 3, 5]
```

---

**i = 1**

* arr[1] == 1 → correct
  → i++

---

**i = 2**

* arr[2] == 2 → correct
  → i++

---

**i = 3**

* arr[3] == 3 → correct
  → i++

---

**i = 4**

* arr[4] = 5
* arr[4] < arr.length → false (5 < 5 ❌)
  → i++

---

### Array after cyclic placement

```
[0, 1, 2, 3, 5]
```

---

### Final for-loop check

* index 0 → arr[0] = 0 ✔
* index 1 → arr[1] = 1 ✔
* index 2 → arr[2] = 2 ✔
* index 3 → arr[3] = 3 ✔
* index 4 → arr[4] = 5 ❌

Mismatch found at **index 4**

---

## Output

```
4
```

---

## Time Complexity

* **O(n)**
  Each element is swapped at most once.

## Space Complexity

* **O(1)**
  In-place algorithm.

## Stability

* **Not stable**
  Swapping can change relative order.

---

