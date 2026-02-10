
---

# ❓ QUESTION

**Implement Bubble Sort using recursion (Triangle-1 pattern)**

---

# 🧠 THE APPROACH (THIS IS THE MONEY PART)

### 👉 **PRE-ORDER RECURSION**

* **Do the work FIRST**
* **Then go to the recursive call**

💡 One-line mental model (burn this into your brain):

> **“Work while going down. No work while coming back.”**

This is **exactly Triangle-1** behavior.

---

# 🔺 WHY BUBBLE SORT = TRIANGLE 1

Triangle-1 (inverted triangle):

* Print **before** recursion
* Work happens **during downward calls**

Bubble Sort:

* Swap **before** recursion
* Sorting happens **during downward calls**

📌 Same structure. Only the “work” changes:

* Triangle → `print("*")`
* Bubble Sort → `compare + swap`

---

# 🔁 VARIABLE MAPPING (INTERVIEW GOLD)

| Triangle Pattern | Bubble Sort Meaning          |
| ---------------- | ---------------------------- |
| `r` (row)        | Last index of unsorted array |
| `c` (col)        | Current index being compared |
| `c < r`          | Inner loop                   |
| `r - 1, 0`       | Next pass                    |

Say this confidently → interviewer nods immediately.

---

# ✅ FULL CODE (WITH `main`)

```java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] arr = {4, 3, 2, 1};

        bubble(arr, arr.length - 1, 0);

        System.out.println(Arrays.toString(arr));
    }

    static void bubble(int[] arr, int r, int c) {
        // Base case: array is fully sorted
        if (r == 0) {
            return;
        }

        // Inner loop logic
        if (c < r) {
            // Work FIRST (Triangle-1 behavior)
            if (arr[c] > arr[c + 1]) {
                int temp = arr[c];
                arr[c] = arr[c + 1];
                arr[c + 1] = temp;
            }

            // Move right
            bubble(arr, r, c + 1);
        } 
        // Outer loop logic
        else {
            // One pass finished, shrink range
            bubble(arr, r - 1, 0);
        }
    }
}
```

---

# 🧩 LINE-BY-LINE EXPLANATION (EASY MODE)

```java
if (r == 0) return;
```

🛑 No elements left to sort → stop.

---

```java
if (c < r)
```

👉 We are inside **one pass** of Bubble Sort.

---

```java
if (arr[c] > arr[c + 1])
```

🔍 Compare adjacent elements.

---

```java
swap
```

🔥 **Work happens here**
This is why it’s **Triangle-1**.

---

```java
bubble(arr, r, c + 1);
```

➡️ Move forward (like `c++` in loop).

---

```java
bubble(arr, r - 1, 0);
```

⬇️ One full pass done.
Largest element is fixed at index `r`.

---

# 🧠 DRY RUN (THINKING PROCESS)

Initial array:

```
[4, 3, 2, 1]
```

Call:

```
bubble(arr, 3, 0)
```

### Pass 1 (r = 3)

* 4 > 3 → swap → [3,4,2,1]
* 4 > 2 → swap → [3,2,4,1]
* 4 > 1 → swap → [3,2,1,4]

👉 4 is fixed.

### Pass 2 (r = 2)

* 3 > 2 → swap → [2,3,1,4]
* 3 > 1 → swap → [2,1,3,4]

👉 3 fixed.

### Pass 3 (r = 1)

* 2 > 1 → swap → [1,2,3,4]

DONE ✅

---

# 📤 OUTPUT

```
[1, 2, 3, 4]
```

---

# 🧠 WHY THIS WORKS (STACK LOGIC)

* Recursive calls go **down**
* Swaps happen **before recursion**
* No work during stack unwinding
* Exactly matches **Bubble Sort philosophy**

👉 **First in, first fixed**

---

# 💣 FINAL CLARITY BOMB (MEMORIZE THIS)

### One-liner for exam + interview:

> **“Recursive Bubble Sort uses Triangle-1 logic:
> Work (swap) happens before recursion, during downward calls.
> `r` shrinks the array, `c` traverses it.”**

