## 🔹 Question 

**Given an array of integers, count how many numbers contain an even number of digits.**

---
```java
public class Even {
    public static void main(String[] args) {
        // Step 1: Declare and initialize the array of numbers
        int nums[] = {12, 345, 2, 6, 7896};

        // Step 2: Call findNumbers method to count numbers with even digits
        int evencount = findNumbers(nums);

        // Step 3: Print the result
        System.out.println(evencount); // Output: 3
    }

    // Method to count how many numbers have even number of digits
    public static int findNumbers(int[] nums) {
        int count = 0; // Initialize counter

        // Loop through each number in the array
        for (int no : nums) {
            // Check if the number has even digits
            if (isEven(no)) {
                count++; // If yes, increment the counter
            }
        }

        return count; // Return total count of numbers with even digits
    }

    // Method to check if a number has an even number of digits
    public static boolean isEven(int no) {
        int ans = counts(no); // Count digits of the number

        // Check if the number of digits is even
        if (ans % 2 == 0) {
            return true;
        }
        return false;
    }

    // Method to count the number of digits in a number
    public static int counts(int no) {
        // Handle negative numbers
        if (no < 0) {
            no = -no; // Make it positive
        }

        // Special case: 0 has 1 digit
        if (no == 0) {
            return 1;
        }

        int count = 0; // Initialize digit counter

        // Count digits by dividing the number by 10 repeatedly
        while (no > 0) {
            count++;
            no = no / 10; // Remove last digit
        }

        return count; // Return the total number of digits
    }
}
```

---

## 🔹 Input

```java
int nums[] = {12, 345, 2, 6, 7896};
```

---

## 🔹 Output

```text
2
```

👉 Because **12** (2 digits) and **7896** (4 digits) have even digits.

---

## 🔹 Big Picture (what happens overall)

1. `main()` sends the array to `findNumbers()`
2. `findNumbers()` loops through each number
3. For each number → `isEven()` checks if digit count is even
4. `isEven()` calls `counts()` to count digits
5. If digit count is even → increase `count`
6. Final count is printed

Simple. No drama.

---

## 🔹 Dry Run (step-by-step like a boss)

### Array:

```text
{12, 345, 2, 6, 7896}
```

### Initial:

```text
count = 0
```

---

### ▶ Number = 12

* `counts(12)`

  * 12 → 1 digit
  * 1 → 2 digits
* returns **2**
* 2 % 2 == 0 ✅
* `count = 1`

---

### ▶ Number = 345

* `counts(345)` → **3**
* 3 % 2 != 0 ❌
* `count = 1`

---

### ▶ Number = 2

* `counts(2)` → **1**
* Odd ❌
* `count = 1`

---

### ▶ Number = 6

* `counts(6)` → **1**
* Odd ❌
* `count = 1`

---

### ▶ Number = 7896

* `counts(7896)` → **4**
* Even ✅
* `count = 2`

---

### 🔹 Final Value Returned

```text
2
```

---

## 🔹 Method-wise Explanation (short & sharp)

### `findNumbers(int[] nums)`

👉 Loops through array and counts numbers with even digits.

---

### `isEven(int no)`

👉 Calls `counts(no)`
👉 Returns `true` if digit count is even.

---

### `counts(int no)`

👉 Handles:

* Negative numbers
* Zero case
* Counts digits using `while(no > 0)`

This is **pure logic**, no magic.

---

## 🔹 Why this code is GOOD

✔ Modular (small methods, clean logic)
✔ Handles edge cases (0, negative numbers)
✔ Easy to debug
✔ Interview-safe

---

## 🔹 One-line summary (exam gold)

> This program counts how many numbers in an array have an even number of digits by calculating the digit count of each number and checking its parity.

