
---

# 🔍 LINEAR SEARCH USING RECURSION

## 🔹 What is Linear Search?

You check elements **one by one** until:

* you find the target ✅
* or you reach the end ❌

Recursion version =
👉 check current
👉 ask recursion to check rest

---

# 1️⃣ BASIC LINEAR SEARCH (returns TRUE / FALSE)

## ❓ Question

Check whether a target element exists in the array using recursion.

---

## 💻 Full Code

```java
static boolean find(int[] arr, int target, int index) {

    // 🛑 Base condition
    if (index == arr.length) {
        return false;
    }

    // 🔁 Check current OR search rest
    return arr[index] == target || find(arr, target, index + 1);
}
```

Call it like:

```java
find(arr, target, 0);
```

---

## 🧠 Explanation (VERY IMPORTANT)

This line is the heart:

```java
arr[index] == target || find(arr, target, index + 1);
```

Meaning:

* If current element matches → return `true`
* Else → ask recursion to check next elements

`||` means **OR**

* If left side is true → Java stops (short-circuit)
* If left is false → recursion runs

---

## 🔍 Dry Run Example

```java
arr = [3, 5, 7, 9]
target = 7
```

| Call          | index | arr[index] | Result          |
| ------------- | ----- | ---------- | --------------- |
| find(arr,7,0) | 0     | 3          | false → recurse |
| find(arr,7,1) | 1     | 5          | false → recurse |
| find(arr,7,2) | 2     | 7          | true → STOP     |

Returns `true` back up.

---

## ✅ Output

```
true
```

---

## 🔑 Key Points

✔ Stops immediately when found
✔ No extra memory except stack
✔ Uses **short-circuit OR**

---

# 2️⃣ FINDING THE FIRST INDEX (returns index or -1)

## ❓ Question

Find the **index** of the target element using recursion.
If not found, return `-1`.

---

## 💻 Full Code

```java
static int findIndex(int[] arr, int target, int index) {

    // 🛑 Base condition
    if (index == arr.length) {
        return -1;
    }

    // 🎯 If found
    if (arr[index] == target) {
        return index;
    }

    // 🔁 Search rest
    return findIndex(arr, target, index + 1);
}
```

---

## 🧠 Explanation

Here:

* We **cannot** use `||`
* Because we need an **index**, not true/false

Logic:

* Found → return index
* Not found → return result of recursion
* End reached → return -1

---

## 🔍 Dry Run

```java
arr = [10, 20, 30, 40]
target = 30
```

| Call    | index    | Action   |
| ------- | -------- | -------- |
| index 0 | 10 ≠ 30  | recurse  |
| index 1 | 20 ≠ 30  | recurse  |
| index 2 | 30 == 30 | return 2 |

---

## ✅ Output

```
2
```

If target = 99 → output:

```
-1
```

---

## 🔑 Key Points

✔ Returns FIRST occurrence
✔ Clean base condition
✔ No OR operator here

---

# 3️⃣ SEARCHING FROM THE BACK (LAST OCCURRENCE)

## ❓ Question

Find the **last index** of the target element using recursion.

---

## 💻 Full Code

```java
static int findIndexLast(int[] arr, int target, int index) {

    // 🛑 Base condition
    if (index == -1) {
        return -1;
    }

    // 🎯 If found
    if (arr[index] == target) {
        return index;
    }

    // 🔁 Move backward
    return findIndexLast(arr, target, index - 1);
}
```

Call it like:

```java
findIndexLast(arr, target, arr.length - 1);
```

---

## 🧠 Explanation

Instead of moving forward:

```
index + 1 ❌
```

We move backward:

```
index - 1 ✅
```

Base case becomes:

```
index == -1
```

---

## 🔍 Dry Run

```java
arr = [5, 7, 7, 9]
target = 7
```

| Call | index | arr[index]     |
| ---- | ----- | -------------- |
| 3    | 9     | no             |
| 2    | 7     | YES → return 2 |

---

## ✅ Output

```
2
```

(last occurrence)

---

## 🔑 Key Points

✔ Finds last occurrence
✔ Starts from end
✔ Same logic, different direction

---

# 🧠 BIG PATTERN YOU MUST REMEMBER

All 3 follow the SAME recursion rule:

> **Check current → trust recursion for rest**

Only these change:

* Return type (boolean / int)
* Direction (forward / backward)
* Base condition

---

## 🏁 Final Brain Lock

Recursion is NOT magic.

It’s literally:

> “If I can’t solve it now, I’ll ask the next call.”

Once you see that, DS problems become mechanical.

---
---
### Ques 4:
---
### (Linear Search on Multiple Occurences)
## ✅ QUESTION

**Find all indices of a target element in an array using recursion
by using a static (global) ArrayList.**

---

## ✅ CODE

```java
static ArrayList<Integer> list = new ArrayList<>();

static void find2(int[] arr, int target, int index) {

    // base condition
    if (index == arr.length) return;

    // check current index
    if (arr[index] == target) {
        list.add(index);
    }

    // recursive call
    find2(arr, target, index + 1);
}
```

Call:

```java
find2(arr, 2, 0);
System.out.println(list);
```

---

## ✅ SIMPLE EXPLANATION (NO OVERTHINKING)

* `list` is **static**, so it belongs to the **class**, not the function.
* All recursive calls **share the same list**.
* Each call:

  * checks one index
  * if match → adds index to the shared list
  * moves to the next index
* No return value is needed because results are stored globally.

---

## ✅ DRY RUN (STEP-BY-STEP)

### Input:

```text
arr = [1, 2, 3, 2, 2]
target = 2
```

| Call | index | arr[index] | Action   | list      |
| ---- | ----- | ---------- | -------- | --------- |
| 1    | 0     | 1          | no match | []        |
| 2    | 1     | 2          | add 1    | [1]       |
| 3    | 2     | 3          | no match | [1]       |
| 4    | 3     | 2          | add 3    | [1, 3]    |
| 5    | 4     | 2          | add 4    | [1, 3, 4] |
| 6    | 5     | —          | stop     | [1, 3, 4] |

---

## ✅ OUTPUT

```text
[1, 3, 4]
```

---

## 🚨 IMPORTANT CONCEPTS (INTERVIEWERS **WILL** ASK THIS)

### 🔹 1. WHY DOES THIS WORK WITHOUT RETURN?

Because:

* `list` is **static**
* Static variables are created **once**
* All recursive calls modify the **same object in heap**

👉 No need to return anything.

---

### 🔹 2. WHERE IS `list` STORED?

* `list` → **Heap memory**
* Reference stored in **class (static area)**
* Function just accesses it

---

### 🔹 3. STACK vs HEAP (VERY IMPORTANT)

| Stack                  | Heap             |
| ---------------------- | ---------------- |
| index, arr, target     | ArrayList object |
| separate per call      | shared object    |
| destroyed after return | stays alive      |

---

### 🔹 4. BIGGEST DRAWBACK (INTERVIEW GOLD ⚠️)

```java
find2(arr, 2, 0);
find2(arr, 2, 0);
```

Output:

```text
[1, 3, 4, 1, 3, 4]
```

💀 WHY?

* Static list **retains old data**
* Must manually clear list

---

### 🔹 5. WHY INTERVIEWERS DON’T PREFER THIS

❌ Uses global state
❌ Not reusable
❌ Not thread-safe
❌ Fails in tree recursion

They’ll ask:

> “What if multiple test cases?”

You must say:

```java
list.clear();
```

---

### 🔹 6. WHEN IS THIS METHOD OK?

✅ Simple linear recursion
✅ One-time execution
✅ Learning basics

---

## 🧠 FINAL ONE-LINER (MEMORIZE THIS)

> This approach works because all recursive calls share the same static ArrayList, so results are accumulated globally without returning values.

---

