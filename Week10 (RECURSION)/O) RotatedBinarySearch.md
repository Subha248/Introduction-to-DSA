

---

# 📌 QUESTION: ROTATED BINARY SEARCH (BEGINNER VERSION)

### What is asked?

You are given:

* an **array**
* the array was **sorted**, then **rotated**
* a **target number**

Your task:
👉 **Find the index of the target**
👉 If not found, return `-1`

---

## 🧠 WHAT DOES “ROTATED SORTED ARRAY” MEAN?

First, a normal sorted array:

```
[1, 2, 3, 4, 5, 6, 7]
```

Rotate it (cut and paste):

```
[4, 5, 6, 7, 1, 2, 3]
```

It is **not fully sorted**,
BUT 👉 **one half is always sorted**.

This one sentence runs the whole code.

---

# ✅ COMPLETE JAVA CODE (WITH MAIN)

```java
public class Main {

    public static void main(String[] args) {

        int[] arr = {4, 5, 6, 7, 0, 1, 2};
        int target = 0;

        int result = search(arr, target, 0, arr.length - 1);
        System.out.println(result);
    }

    static int search(int[] arr, int target, int s, int e) {

        // 1️⃣ BASE CASE
        if (s > e) {
            return -1;
        }

        // 2️⃣ FIND MID
        int m = s + (e - s) / 2;

        // 3️⃣ CHECK IF MID IS TARGET
        if (arr[m] == target) {
            return m;
        }

        // 4️⃣ CHECK IF LEFT HALF IS SORTED
        if (arr[s] <= arr[m]) {

            // 5️⃣ CHECK IF TARGET IS IN LEFT HALF
            if (target >= arr[s] && target <= arr[m]) {
                return search(arr, target, s, m - 1);
            }

            // 6️⃣ ELSE SEARCH RIGHT HALF
            return search(arr, target, m + 1, e);
        }

        // 7️⃣ RIGHT HALF IS SORTED
        if (target >= arr[m] && target <= arr[e]) {
            return search(arr, target, m + 1, e);
        }

        // 8️⃣ ELSE SEARCH LEFT HALF
        return search(arr, target, s, m - 1);
    }
}
```

---

# 🧩 LINE-BY-LINE EXPLANATION (SUPER SIMPLE)

---

## 🔹 `main()` FUNCTION

```java
int[] arr = {4, 5, 6, 7, 0, 1, 2};
```

This array **was sorted**, then rotated.

```java
int target = 0;
```

This is the number we want to find.

```java
search(arr, target, 0, arr.length - 1);
```

We start searching from:

* `s = 0` (start)
* `e = 6` (end)

---

## 🔹 `search()` FUNCTION

---

### 1️⃣ BASE CASE

```java
if (s > e) return -1;
```

Means:
👉 “Nothing left to search”
👉 Target not found

---

### 2️⃣ FIND MID

```java
int m = s + (e - s) / 2;
```

Find middle index safely.

---

### 3️⃣ CHECK MID

```java
if (arr[m] == target) return m;
```

If middle element is target → STOP.

---

### 4️⃣ CHECK LEFT HALF SORTED

```java
if (arr[s] <= arr[m])
```

If true:
👉 Left side is sorted

---

### 5️⃣ TARGET IN LEFT HALF?

```java
if (target >= arr[s] && target <= arr[m])
```

YES → search left:

```java
search(arr, target, s, m - 1);
```

---

### 6️⃣ ELSE SEARCH RIGHT

```java
search(arr, target, m + 1, e);
```

---

### 7️⃣ RIGHT HALF SORTED

If left is not sorted, right must be sorted.

Check if target is in right.

---

### 8️⃣ ELSE SEARCH LEFT

Final option.

---

# 🔄 FULL WORKING (STEP BY STEP THINKING)

Array:

```
[4,5,6,7,0,1,2]
```

Target = `0`

| Call | s | e | m | arr[m] | Decision |
| ---- | - | - | - | ------ | -------- |
| 1    | 0 | 6 | 3 | 7      | Go right |
| 2    | 4 | 6 | 5 | 1      | Go left  |
| 3    | 4 | 4 | 4 | 0      | FOUND    |

---

## 📤 OUTPUT

```
4
```

---

# 🎯 IMPORTANT THINGS TO REMEMBER

✔ Recursion creates **new s and e**, it does NOT update old ones
✔ One half is always sorted
✔ We decide direction logically
✔ `s == e` is valid
✔ `s > e` means stop

---

## 🧠 ONE SENTENCE TO LOCK IT IN

> Rotated binary search works by finding the sorted half and checking if the target lies in that range.

---

