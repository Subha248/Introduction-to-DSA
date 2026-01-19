
---

### ✅ **Code: Taking multiple inputs into an ArrayList**

```java
import java.util.*;

public class array {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Create an ArrayList of integers
        ArrayList<Integer> list = new ArrayList<>(10);

        // Take 5 numbers as input from the user
        for (int i = 0; i < 5; i++) {
            int n = sc.nextInt(); // take a new number each time
            list.add(n);          // add it to the list
        }

        // Print the entire ArrayList
        System.out.println(list);
    }
}
```

---

### 💡 **Explanation:**

* `ArrayList<Integer>` → a resizable array that stores integers.
* `list.add(n)` → adds each number entered by the user to the list.
* The `for` loop repeats 5 times to collect 5 numbers.
* `System.out.println(list)` → prints all elements together in `[ ]` format.

---

### 🧮 **Example Input:**

```
10 20 30 40 50
```

### 📤 **Output:**

```
[10, 20, 30, 40, 50]
```

---


)? It’s nice for beginners to include both styles on GitHub.

---

### ❌ Problem in your code

In this line:

```java
System.out.print(yoo.get());
```

You didn’t specify **which index** you want to get.
`get()` method **must have an index inside parentheses**, like:

```java
yoo.get(i)
```

Because `.get(index)` means → “fetch the element at this index”.

---

### ✅ Correct (fixed) code:

```java
import java.util.*;
public class array {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        ArrayList<Integer> yoo = new ArrayList<>(10);

        // Take 5 numbers from the user
        for (int i = 0; i < 5; i++) {
            int n = sc.nextInt();
            yoo.add(n);
        }

        // Print the entire ArrayList
        System.out.println("ArrayList: " + yoo);

        // Get item at each index and print one by one
        for (int i = 0; i < 5; i++) {
            System.out.println("Element at index " + i + " = " + yoo.get(i));
        }

        // Print the entire list again at the end
        System.out.println("Final list: " + yoo);
    }
}
```

---

### 💡 Explanation (super simple):

#### 1️⃣ You create the ArrayList:

```java
ArrayList<Integer> yoo = new ArrayList<>(10);
```

#### 2️⃣ You take 5 numbers as input:

Let’s say you enter:

```
10 20 30 40 50
```

Now:

```
yoo = [10, 20, 30, 40, 50]
```

#### 3️⃣ You print the whole list:

```
ArrayList: [10, 20, 30, 40, 50]
```

#### 4️⃣ You print each item using `.get(i)`:

| i | yoo.get(i) | Printed output          |
| - | ---------- | ----------------------- |
| 0 | 10         | Element at index 0 = 10 |
| 1 | 20         | Element at index 1 = 20 |
| 2 | 30         | Element at index 2 = 30 |
| 3 | 40         | Element at index 3 = 40 |
| 4 | 50         | Element at index 4 = 50 |

#### 5️⃣ Final print again:

```
Final list: [10, 20, 30, 40, 50]
```

---

### 📤 Example Output:

```
ArrayList: [10, 20, 30, 40, 50]
Element at index 0 = 10
Element at index 1 = 20
Element at index 2 = 30
Element at index 3 = 40
Element at index 4 = 50
Final list: [10, 20, 30, 40, 50]
```

---


---

```java
import java.util.*;

public class MultiAL {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Step 1: Create a big ArrayList that will hold other ArrayLists (rows)
        ArrayList<ArrayList<Integer>> list = new ArrayList<>();

        // Step 2: Initialize 3 empty rows
        for (int i = 0; i < 3; i++) {
            list.add(new ArrayList<>()); // adds an empty row
        }

        // Step 3: Take input from user and fill each row
        // Outer loop -> selects the row
        // Inner loop -> fills numbers in that row
        System.out.println("Enter 9 numbers (for 3x3 matrix):");
        for (int i = 0; i < 3; i++) {          // row by row
            for (int j = 0; j < 3; j++) {      // column by column
                int num = sc.nextInt();         // read one number
                list.get(i).add(num);           // add number to the i-th row
            }
        }

        // Step 4: Print the entire 2D ArrayList
        System.out.println("\nThe 2D ArrayList is:");
        System.out.println(list); // prints all rows in one line

        // Optional: Print row by row in a clean matrix format
        System.out.println("\nPrinting row by row:");
        for (int i = 0; i < list.size(); i++) {
            System.out.println(list.get(i));
        }
    }
}
```

---

### 🌟 Key Points / Explanation

1. **`ArrayList<ArrayList<Integer>> list = new ArrayList<>();`**

   * Creates a “big list” that can hold multiple small lists (rows).

2. **`list.add(new ArrayList<>());`**

   * Adds an **empty row** to the big list.
   * After 3 iterations → `[ [], [], [] ]`

3. **`list.get(i)`**

   * Goes to the i-th row (row 0, row 1, row 2).
   * Doesn’t fill anything yet, just “points” to that row.

4. **`list.get(i).add(num)`**

   * Adds the number to the selected row.

5. **Nested loops:**

   * Outer loop (`i`) → chooses which row to fill.
   * Inner loop (`j`) → fills numbers in that row.

---

### 🧩 Example Input & Output

**Input (typed one by one or in lines):**

```
1 2 3
4 5 6
7 8 9
```

**Output:**

```
The 2D ArrayList is:
[[1, 2, 3], [4, 5, 6], [7, 8, 9]]

Printing row by row:
[1, 2, 3]
[4, 5, 6]
[7, 8, 9]
```

✅ **Step by step:**

* Row 0 → adds 1, 2, 3 → `[1, 2, 3]`
* Row 1 → adds 4, 5, 6 → `[4, 5, 6]`
* Row 2 → adds 7, 8, 9 → `[7, 8, 9]`

---


