
---

## 🌸 The Code:

```java
import java.util.*;
public class array {
    public static void main(String[] args) {
        int[] nums = {3, 4, 5, 6};
        System.out.println(Arrays.toString(nums));
        change(nums);
        System.out.println(Arrays.toString(nums));
    }

    public static void change(int[] arr) {
        arr[2] = 8;
    }
}
```

---

## 🧠 Step-by-Step Explanation

### 1️⃣ Array Creation

```java
int[] nums = {3, 4, 5, 6};
```

* Java creates an **array object** `[3, 4, 5, 6]` in **Heap memory**.
* The variable `nums` is in **Stack memory** and stores the **reference** (address) to this array.

**Memory view:**

```
Stack: nums → [3, 4, 5, 6] (Heap)
```

---

### 2️⃣ First Print

```java
System.out.println(Arrays.toString(nums));
```

* Prints the **current content** of the array:

```
[3, 4, 5, 6]
```

---

### 3️⃣ Function Call

```java
change(nums);
```

* `nums` is passed to `change()` method.
* Java passes the **reference** by value → `arr` is a new variable in the **Stack** of the method, but it points to the **same array** in Heap.

**Memory view during `change()` call:**

```
Stack (main): nums → [3, 4, 5, 6] (Heap)
Stack (change): arr → same [3, 4, 5, 6] (Heap)
```

---

### 4️⃣ Change Inside Function

```java
arr[2] = 8;
```

* Modifies the **3rd element** (index 2) of the array in Heap.
* Since `nums` in `main()` points to the **same array**, this change is visible there too.

**Heap after modification:**

```
[3, 4, 8, 6]
```

---

### 5️⃣ Second Print

```java
System.out.println(Arrays.toString(nums));
```

* Prints the **modified array**:

```
[3, 4, 8, 6]
```

---

## ✅ Final Output:

```
[3, 4, 5, 6]
[3, 4, 8, 6]
```

---

## 🌼 Key Points to Remember

1. Arrays are **objects** in Java → stored in **Heap**.
2. Variables like `nums` store **reference to array** in **Stack**.
3. Passing an array to a function sends the **reference by value** → the function can **modify the original array**.
4. Modifying `arr[2]` inside the function **changes the actual array in Heap**, so `nums` reflects the change.

---

