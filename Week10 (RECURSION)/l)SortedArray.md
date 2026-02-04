
We’re solving:

> **“Check if an array is sorted in increasing order using recursion.”**

---

## ✅ The Question

Given an array like:

```
[1, 2, 3, 4] → Sorted ✅
[1, 5, 3, 7] → Not Sorted ❌
```

We must write a **recursive function** that returns:

* `true` if sorted
* `false` if not

---

## 💻 Full Code

```java
static boolean isSorted(int[] arr, int index) {

    // 🛑 Base Condition
    if (index == arr.length - 1) {
        return true;
    }

    // 🔁 Recursive Condition
    return arr[index] < arr[index + 1] && isSorted(arr, index + 1);
}
```

You call it like:

```java
isSorted(arr, 0);
```

---

## 🧠 Thought Process (MOST IMPORTANT)

Recursion thinking =

> “I will check ONE step. Recursion will check the REST.”

So at any position `index`, we only worry about:

```
Is arr[index] smaller than arr[index + 1]?
```

If YES → ask recursion to check the rest
If NO → array is not sorted

---

## 🔁 Workflow Step-by-Step

Let’s take:

```
arr = [1, 2, 5, 3]
```

### 🧩 Call 1 → isSorted(arr, 0)

Check: `1 < 2` ✅
Now ask recursion: `isSorted(arr, 1)`

---

### 🧩 Call 2 → isSorted(arr, 1)

Check: `2 < 5` ✅
Now ask recursion: `isSorted(arr, 2)`

---

### 🧩 Call 3 → isSorted(arr, 2)

Check: `5 < 3` ❌
So this call returns **false**

---

### 🔙 Returning Back (Call Stack)

Now results go back up:

```
Call 3 → false
Call 2 → true && false = false
Call 1 → true && false = false
```

Final Output → **false (array not sorted)**

---

## 🛑 Base Condition Explained Again

```java
if (index == arr.length - 1)
    return true;
```

When we reach the last element, there’s **nothing left to compare**.

That means we checked all previous pairs and found no problem → so array is sorted.

---

## 📦 What Happens in Memory

This is where your earlier question connects 🔥

✔ The array is **NOT copied**
✔ Only the **reference (address)** is passed
✔ Every recursive call uses the **same array in memory**
✔ Only `index` changes in each call

So memory use is small — just stack frames storing `index`.

---

## ⏱ Complexity

| Type  | Value | Why                        |
| ----- | ----- | -------------------------- |
| Time  | O(n)  | One comparison per element |
| Space | O(n)  | Because of recursion stack |

---

## 🧩 The Recursion Pattern You Must Remember

This problem teaches the golden rule:

> **Check current step + Trust recursion for the rest**

Used in:

* Sum of array
* Max element
* Palindrome check
* Linked list problems
* Tree problems

---

## 🎯 Final Output Examples

| Array       | Output                                   |
| ----------- | ---------------------------------------- |
| `[1,2,3,4]` | `true`                                   |
| `[1,2,5,3]` | `false`                                  |
| `[10]`      | `true` (single element is always sorted) |

---

## 💬 Final Brain Line

Recursion is just:

> “I’ll handle this one comparison. The next version of me will handle the rest.”

That’s it. That’s the whole mindset.

---

