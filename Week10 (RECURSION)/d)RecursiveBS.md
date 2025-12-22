
---

## Recursive Binary Search – **Code + Internal Working (Complete Explanation)**

### ✅ **Java Code (as required)**

```java
static int search(int[] arr, int target, int s, int e) {
    // Base Condition: If start exceeds end, the target is not in the array
    if (s > e) {
        return -1;
    }

    // Body: Calculate the middle index for the current call
    int m = s + (e - s) / 2;

    // Check if the middle element is the target
    if (arr[m] == target) {
        return m;
    }

    // Recursive Calls:
    // If target is less than middle, search the left half
    if (target < arr[m]) {
        return search(arr, target, s, m - 1);
    }

    // Otherwise, search the right half
    return search(arr, target, m + 1, e);
}
```

---

## 1. Why Binary Search Uses Recursion

Binary search **breaks one big problem into smaller problems** by dividing the array into **two halves** each time.
That’s literally the definition of recursion + divide & conquer.

---

## 2. Base Condition (VERY IMPORTANT)

```java
if (s > e) {
    return -1;
}
```

* This means the search space is exhausted
* Target does **not exist**
* Prevents **infinite recursion**
* Without this → **StackOverflowError**

👉 This is where recursion **stops**

---

## 3. Function Body (Current Call Only)

```java
int m = s + (e - s) / 2;
```

* `m` is calculated **fresh for every call**
* Used only in the **current function**
* Not needed in future calls → stays in **body**, not arguments

This follows the speaker’s rule:

> Variables used only in the current call go in the body.

---

## 4. Return Type & Why `return` is Mandatory

```java
return search(arr, target, s, m - 1);
```

* Function return type is `int`
* So **every recursive call must be returned**
* Otherwise, the answer found deep inside recursion will be **lost**

📌 The value travels **back through the stack** to `main()`

---

## 5. Arguments (Passed to Next Calls)

```java
search(arr, target, s, m - 1);
search(arr, target, m + 1, e);
```

Arguments used:

* `s` (start)
* `e` (end)

These **define the next search space**, so they MUST be arguments.

Speaker rule:

> Whatever you put in arguments goes to the next function call.

---

## 6. Left First, Then Right (Execution Flow)

```java
if (target < arr[m]) {
    return search(arr, target, s, m - 1);
}
return search(arr, target, m + 1, e);
```

* Java executes **top to bottom**
* Only **one recursive call** happens per function call
* Not like Fibonacci (two calls)

So:

* First check left
* Else go right

---

## 7. Stack Behaviour (Core Concept)

Example: `search(arr, 7, 0, 6)`

Call stack looks like:

```
search(0,6)  ← waiting
search(4,6)  ← waiting
search(5,6)  ← waiting
search(5,5)  ← found → return index
```

* Every call stays in **stack**
* Each one waits for the next to finish
* Once found, result **travels back up**

---

## 8. Recurrence Relation

Each call:

* Does **O(1)** work (comparison)
* Calls itself on **half** the array

So recurrence relation:

[
f(n) = O(1) + f(n/2)
]

This is **divide and conquer recurrence**.

---

## 9. Types of Recurrence (Revision)

### 🔹 Linear Recurrence

* Example: Fibonacci
* Reduces by 1
* Very slow
* Repeated work

### 🔹 Divide & Conquer Recurrence

* Example: Binary Search
* Reduces by factor (n/2)
* Fast & efficient

---

## 10. Final Speaker Tips (Don’t Skip)

* First **solve the problem**
* Don’t overthink stack initially
* After solving:

  * Explain code
  * Draw recursion tree
  * Track stack frames
* Use debugger if confused
* Make sure return type matches returned value

---

## 🔥 Final One-Line Summary (Exam Gold)

Binary search recursion works by dividing the array into halves, storing each function call in the stack, stopping at a base condition, and returning the found index back through all waiting calls using proper return statements.

