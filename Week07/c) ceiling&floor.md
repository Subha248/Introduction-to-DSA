
---

# ✅ **CEILING & FLOOR (Your Code + Straight Explanation)**

We’ll break both down **with your exact code** and show **why `start` gives ceiling** and **why `end` gives floor**.

Array:
`{2, 3, 5, 9, 14, 16, 18}`
Target: `15`

---

# ⭐ 1. **CEILING FUNCTION**

*(smallest element ≥ target)*

### **Your code**

```java
public static int ceiling(int[] arr, int target) {
    int start = 0;
    int end = arr.length - 1;

    while (start <= end) {
        int mid = start + (end - start)/2;

        if (target < arr[mid]) {
            end = mid - 1;
        } else if (target > arr[mid]) {
            start = mid + 1;
        } else {
            return arr[mid];
        }
    }

    return arr[start];
}
```

---

# **CEILING — Step-by-Step Working**

### Initial

```
start = 0 (2)
end = 6 (18)
```

---

### **Step 1**

mid = 3 → arr[3] = 9
9 < 15 → target is bigger

```
start = mid + 1 = 4
```

---

### **Step 2**

start = 4, end = 6
mid = 5 → arr[5] = 16
16 > 15 → target is smaller

```
end = mid - 1 = 4
```

---

### **Step 3**

start = 4, end = 4
mid = 4 → arr[4] = 14
14 < 15 → target is bigger

```
start = mid + 1 = 5
```

---

### **Loop ends**

```
start = 5
end = 4
```

Since `start > end`, while-loop stops.

Now:

* `start` points to **16** → the first value greater than or equal to 15.
* That is exactly the **ceiling**.

### Final return:

```
return arr[start]; // arr[5] = 16
```

---

# ⭐ 2. **FLOOR FUNCTION**

*(largest element ≤ target)*

### **Your code**

```java
public static int floor(int[] arr, int target) {
    int start = 0;
    int end = arr.length - 1;

    while (start <= end) {
        int mid = start + (end - start)/2;

        if (target < arr[mid]) {
            end = mid - 1;
        } else if (target > arr[mid]) {
            start = mid + 1;
        } else {
            return arr[mid];
        }
    }

    return arr[end];
}
```

---

# **FLOOR — Step-by-Step Working**

The steps are **exactly the same** as ceiling until exit:

Final pointer values:

```
start = 5   (pointing at 16)
end   = 4   (pointing at 14)
```

For floor:

* We need the **largest value ≤ target**.
* `end` always lands on the closest **smaller** element.

### Final return:

```
return arr[end]; // arr[4] = 14
```

---

# 🎯 **THE CORE IDEA**

### ✔ Ceiling → return `arr[start]`

Because `start` always stops on the **first element that is bigger or equal to target**.

### ✔ Floor → return `arr[end]`

Because `end` always stops on the **last element that is smaller or equal to target**.

This behavior comes directly from the update rules:

```
start = mid + 1; // moves right
end   = mid - 1; // moves left
```

Once the loop ends:

* `start` overshoots to the next bigger
* `end` settles on the last smaller

This is why the return lines work.

---

