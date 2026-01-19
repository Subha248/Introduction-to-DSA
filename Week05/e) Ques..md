
---

### 📝 **SWAPPING ARRAY ELEMENTS IN JAVA**

```java
import java.util.*;

public class ArraySwap {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input array size and elements
        int n = sc.nextInt();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }

        // Print original array
        System.out.println("Original array: " + Arrays.toString(arr));

        // Swap elements at index 1 and 2
        swap(arr, 1, 2);

        // Print array after swap
        System.out.println("After swap: " + Arrays.toString(arr));
    }

    // Method to swap two elements in the array
    static void swap(int[] arr, int index1, int index2) {
        int temp = arr[index1];
        arr[index1] = arr[index2];
        arr[index2] = temp;
    }
}
```

---

### 💡 **Concise Explanation**

1. **Why swap works on the array:**

   * Arrays in Java are **passed by reference**.
   * Modifying `arr[index]` inside the method **changes the original array**.

2. **Why swapping indices alone doesn’t work:**

   ```java
   static void swap(int[] arr, int index1, int index2){
       int temp = index1;
       index1 = index2;
       index2 = temp;
   }
   ```

   * `index1` and `index2` are just integers.
   * Swapping them changes the **local variables only**, not the array.

3. **Correct approach:**

   * Access the elements in the array using their indices:

     ```java
     int temp = arr[index1];
     arr[index1] = arr[index2];
     arr[index2] = temp;
     ```
   * This directly updates the original array.

4. **Optional trick (less common):**

   * Using arrays of length 1 for indices:

     ```java
     int[] index1 = {1}, index2 = {2};
     int temp = arr[index1[0]];
     arr[index1[0]] = arr[index2[0]];
     arr[index2[0]] = temp;
     ```
   * Still, you must access `arr[]` to modify elements — swapping `index1[0]` and `index2[0]` alone doesn’t change the array.

---

### ✅ **Key takeaway**

> To swap elements in an array, you **must change the array values** using their indices. Swapping the index variables alone never affects the array.

---

If you want, I can also make a **super concise version with a diagram** for your GitHub README — it will explain this in **one glance** for anyone reading your repo.

Do you want me to do that?


---

### 🧾 **File name:** `MaxValueInArray.java`

```java
/*
 * Program: Find Maximum Value in an Array
 * Description:
 *   This Java program takes the size of an array and its elements as input,
 *   then finds and prints the maximum value from the array.
 *
 * Steps:
 *   1. Take input for array size (n).
 *   2. Store n elements in the array.
 *   3. Print the array using Arrays.toString().
 *   4. Call the 'max()' method to find and return the largest value.
 *   5. Display the maximum value.
 */

import java.util.*;

public class MaxValueInArray {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input array size
        int n = sc.nextInt();
        int[] arr = new int[n];

        // Input array elements
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }

        // Print array elements
        System.out.println("Array: " + Arrays.toString(arr));

        // Call method and print maximum value
        System.out.println("Maximum value: " + max(arr));
    }

    // Method to find the maximum value in the array
    static int max(int[] arr) {
        int maxvalue = arr[0]; // Assume first element is max

        for (int i = 0; i < arr.length; i++) {
            if (arr[i] > maxvalue) {
                maxvalue = arr[i];
            }
        }

        return maxvalue; // Return the largest element
    }
}
```

---

### ✅ **Example Input**

```
5
1 3 23 9 18
```

### 🖥️ **Output**

```
Array: [1, 3, 23, 9, 18]
Maximum value: 23
```

---

### 💡 **Explanation (Concise for README)**

* The program reads `n` elements from the user and stores them in an array.
* It then iterates through the array to compare each element with the current maximum.
* If a larger value is found, it updates `maxvalue`.
* Finally, it returns and prints the maximum number.

---

