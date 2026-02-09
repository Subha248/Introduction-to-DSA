
---

# ❓ MAIN QUESTION

**How does passing an ArrayList as a parameter work in recursion, and how does it store values?**

---

# ✅ FULL CODE (PASSING LIST AS PARAMETER)

```java
import java.util.ArrayList;

public class Main {

    public static void main(String[] args) {

        int[] arr = {2, 3, 1, 4, 4, 5};
        int target = 4;

        ArrayList<Integer> list = new ArrayList<>();

        findAllIndex(arr, target, 0, list);

        System.out.println(list);
    }

    static void findAllIndex(int[] arr, int target, int index, ArrayList<Integer> list) {

        // Base case: if index is beyond array length, return
        if (index == arr.length) {
            return;
        }

        // If current element matches the target, add index to list
        if (arr[index] == target) {
            list.add(index);
        }

        // Recursive call to the next index
        findAllIndex(arr, target, index + 1, list);
    }
}
```

---

# 🧠 LINE-BY-LINE EXPLANATION

## 1️⃣ `main()` function

```java
int[] arr = {2, 3, 1, 4, 4, 5};
int target = 4;
```

* **arr** is the input array.
* **target** is the number we want to find.

---

```java
ArrayList<Integer> list = new ArrayList<>();
```

* We create **one ArrayList** in `main`.
* This list will store all the indices of the target.

---

```java
findAllIndex(arr, target, 0, list);
```

* We start the recursion from **index 0**.
* We pass the **same list** to every recursive call.

---

## 2️⃣ `findAllIndex()` function

```java
if (index == arr.length) {
    return;
}
```

* **Base case**: When the index reaches the end of the array, we stop the recursion.

---

```java
if (arr[index] == target) {
    list.add(index);
}
```

* If the element at the current index matches the target, we add that index to our list.

---

```java
findAllIndex(arr, target, index + 1, list);
```

* We call the function recursively for the next index.
* We pass the **same list** each time.

---

# 🔥 HOW VALUES ARE STORED (WORKING PROCESS)

## 🧩 MEMORY & STACK DIAGRAM

### Initial Call (index = 0)

* **Heap**: One `ArrayList` object.
* **Stack**: `main()` calls `findAllIndex(arr, target, 0, list)`.

### Call 1 (index = 0)

* Check `arr[0]` = 2 (no match for target 4).
* List remains empty `[]`.
* Call next index: `findAllIndex(arr, target, 1, list)`.

### Call 2 (index = 1)

* Check `arr[1]` = 3 (no match).
* List still `[]`.
* Call next index: `findAllIndex(arr, target, 2, list)`.

### Call 3 (index = 2)

* Check `arr[2]` = 1 (no match).
* List still `[]`.
* Call next index: `findAllIndex(arr, target, 3, list)`.

### Call 4 (index = 3)

* Check `arr[3]` = 4 (match).
* Add index 3 to list: `list = [3]`.
* Call next index: `findAllIndex(arr, target, 4, list)`.

### Call 5 (index = 4)

* Check `arr[4]` = 4 (match).
* Add index 4 to list: `list = [3, 4]`.
* Call next index: `findAllIndex(arr, target, 5, list)`.

### Call 6 (index = 5)

* Check `arr[5]` = 5 (no match).
* List remains `[3, 4]`.
* Call next index: `findAllIndex(arr, target, 6, list)`.

### Call 7 (index = 6)

* Base case reached (`index == arr.length`).
* Return.

---

## 🧠 FINAL OUTPUT

After all recursive calls complete, the `list` in `main` now contains all indices where the target was found.

```java
System.out.println(list);
```

**Output:**

```
[3, 4]
```

---

# 🧠 WHY THIS WORKS

* **Single List**: By passing the same `ArrayList` as a parameter, all recursive calls modify the same object in memory.
* **No Copies**: No new lists are created, so the indices are added directly to the original list.
* **Shared Reference**: Each call has the same reference to the list, so all changes persist.

---

# 🔥 KEY TAKEAWAYS

1. **Efficiency**: Only one `ArrayList` is created, making it memory efficient.
2. **Shared State**: All calls operate on the same list, so no need to merge or return values.
3. **Simplicity**: This method is straightforward and commonly used in real-world code.

---

---

# ✅ PROBLEM

**Find ALL indices of a target in an array using recursion**
❌ Not allowed to pass `ArrayList` as parameter

---

## ✅ FULL CODE (WITH `main`)

```java
import java.util.ArrayList;

public class Main {

    public static void main(String[] args) {

        int[] arr = {1, 2, 3, 2, 4};
        int target = 2;

        ArrayList<Integer> result = findAllIndex(arr, target, 0);
        System.out.println(result);
    }

    static ArrayList<Integer> findAllIndex(int[] arr, int target, int index) {

        // 1️⃣ Create a NEW list for THIS call
        ArrayList<Integer> list = new ArrayList<>();

        // 2️⃣ Base case: index crossed array
        if (index == arr.length) {
            return list;   // empty list
        }

        // 3️⃣ Check current index
        if (arr[index] == target) {
            list.add(index);
        }

        // 4️⃣ Ask recursion to solve for remaining array
        ArrayList<Integer> ansFromBelow =
                findAllIndex(arr, target, index + 1);

        // 5️⃣ Merge future answers into current list
        list.addAll(ansFromBelow);

        // 6️⃣ Return final list for THIS call
        return list;
    }
}
```

---

# 🔥 NOW THE EXPLANATION (FROM INDEX = 0)

## STEP 0 — `main()`

```java
findAllIndex(arr, target, 0);
```

🧠 Meaning:

> “Start checking from index 0.”

This is **exactly like starting a loop from 0**, but recursion replaces the loop.

---

## STEP 1 — index = 0

```java
ArrayList<Integer> list = new ArrayList<>();
```

💡 **IMPORTANT**

* This line creates a **NEW ArrayList in HEAP**
* Every recursive call executes this line
* So **every call gets its OWN list**

At index 0:

```
list = []
arr[0] = 1 ❌
```

Then:

```java
ansFromBelow = findAllIndex(arr, target, 1);
```

⏸️ Execution PAUSES here.
Java goes to index 1.

---

## STEP 2 — index = 1

New call → new stack frame → new list.

```
list = []
arr[1] = 2 ✅
list = [1]
```

Calls:

```java
findAllIndex(arr, target, 2);
```

---

## STEP 3 — index = 2

```
list = []
arr[2] = 3 ❌
```

Calls index 3.

---

## STEP 4 — index = 3

```
list = []
arr[3] = 2 ✅
list = [3]
```

Calls index 4.

---

## STEP 5 — index = 4

```
list = []
arr[4] = 4 ❌
```

Calls index 5.

---

## STEP 6 — index = 5 (BASE CASE)

```java
if (index == arr.length)
    return [];
```

🧠 Meaning:

> “Array finished. Nothing left.”

Returns **empty list** `[]`.

---

# 🔁 NOW RETURNING STARTS (THIS IS THE KEY)

### Back to index = 4

```
list = []
ansFromBelow = []
list.addAll([]) → []
return []
```

---

### Back to index = 3

```
list = [3]
ansFromBelow = []
list.addAll([]) → [3]
return [3]
```

---

### Back to index = 2

```
list = []
ansFromBelow = [3]
list.addAll([3]) → [3]
return [3]
```

---

### Back to index = 1

```
list = [1]
ansFromBelow = [3]
list.addAll([3]) → [1, 3]
return [1, 3]
```

---

### Back to index = 0

```
list = []
ansFromBelow = [1, 3]
list.addAll([1, 3]) → [1, 3]
return [1, 3]
```

---

## ✅ FINAL OUTPUT

```text
[1, 3]
```

---

# 🔥 NOW ANSWERING **ALL YOUR DOUBTS**

## ❓ “ansFromBelow just calls the function, how is it storing anything?”

❌ Wrong thought
✅ Correct thought:

```java
ArrayList<Integer> ansFromBelow =
        findAllIndex(...);
```

Means:

> “Call the function, WAIT for it to finish, and STORE what it RETURNS.”

It stores a **REFERENCE** to the ArrayList in **HEAP**.

---

## ❓ “Where is the list actually stored?”

✔️ The list is stored in **HEAP**
✔️ Variables like `list`, `ansFromBelow` store **references**
✔️ Stack frame dies, heap object survives

---

## ❓ “Does recursion create a new list every time?”

✅ YES
Every call runs:

```java
new ArrayList<>();
```

❌ But they are NOT all kept forever.

---

## ❓ “Then what happens to old lists?”

* Values are copied using `addAll`
* Old lists lose references
* Garbage Collector removes them later

Only **final merged list survives**.

---

## ❓ “Why not just use this simpler code?”

```java
static ArrayList<Integer> list = new ArrayList<>();
```

Because ❌:

* Uses **global shared state**
* Breaks recursion purity
* Interviewers HATE it
* You don’t learn return flow

This question exists **ONLY** to teach recursion returns.

---

## ❓ “Why can’t we just return list directly without ansFromBelow?”

Because:

* Current call does NOT know future answers
* It must WAIT for recursion
* `ansFromBelow` captures that returned result

---

# 🧠 ONE SENTENCE THAT EXPLAINS EVERYTHING

> “Each recursive call creates its own list, adds its own result, waits for the next call to return a list, merges it, and returns the combined list upward.”

If this sentence makes sense → **you’re done**.

---

## 🔑 WHAT TO REMEMBER FOR EXAMS / INTERVIEWS

✔ Start call from index 0
✔ Base case returns empty list
✔ Each call has its own list
✔ `ansFromBelow` stores returned reference
✔ `addAll` = bubbling up
✔ Conceptual, not optimal

---

You’re not weak.
You pushed until the **memory model clicked** — that’s rare.

