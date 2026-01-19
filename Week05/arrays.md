

---

### 💫 Final Simple Explanation:

* In Java, **arrays of objects** are stored in the **heap memory**.
* **Heap memory** is used for **dynamic memory allocation** — meaning objects can be created and placed anywhere there’s free space.
* Because of that, **heap memory is not continuous**, so the **objects** inside an array are **not stored side by side**.
* The array itself only stores **references (addresses)** that point to those scattered objects.

---

### 🌸 In one short line:

> Array of objects in Java are not stored continuously because they are stored in heap memory, where objects are dynamically allocated.

---


---

### ✅ Correct For-Each Version

```java
import java.util.*;

public class Demo {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] arr = new int[n];

        // Input array elements
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }

        // Print array using for-each loop
        for (int num : arr) {
            System.out.print(num + " "); // num is the current element
        }
    }
}
```

---

### 🌸 Key Points:

1. `for(int num : arr)` → loops through **each element** of the array directly.
2. Inside the loop, `num` is **the current element**, not the index.
3. You **cannot use `arr[i]`** inside a for-each because there is no `i` index here.

---

### 🔹 Example Input & Output

**Input:**

```
4
5 10 15 20
```

**Output:**

```
5 10 15 20 
```

---


---

```java
// 🌸 Array Input and Print Example
// This program takes 'n' numbers from the user and prints the array using Arrays.toString()

import java.util.*;

public class Demo {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // 1️⃣ Take size of the array
        int n = sc.nextInt();
        int[] arr = new int[n];  // create array of size n

        // 2️⃣ Input values into the array
        for (int i = 0; i < arr.length; i++) {
            arr[i] = sc.nextInt();
        }

        // 3️⃣ Print array as string
        System.out.println(Arrays.toString(arr));
    }
}
```

---

### 📘 Notes for Revision

* `int[] arr = new int[n];` → creates an array of size `n`
* `arr[i] = sc.nextInt();` → stores user input in the array
* `Arrays.toString(arr)` → prints the array in a readable format like `[10, 20, 30, 40]`

---

### 🔹 Example Input & Output

**Input:**

```
5
10 20 30 40 50
```

**Output:**

```
[10, 20, 30, 40, 50]
```

**Input:**

```
3
1 2 3
```

**Output:**

```
[1, 2, 3]
```

---


---

### ✅ Your final code:

```java
import java.util.*;

public class demo {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        String[] str = new String[n];

        for (int i = 0; i < n; i++) {
            str[i] = sc.next();
        }

        System.out.println(Arrays.toString(str)); 
        str[1] = "subh";
        System.out.println(Arrays.toString(str)); 
    }
}
```

---

### 🌸 Why this version works perfectly:

#### 🧠 1. `sc.nextInt()` reads your number

Example input:

```
3
```

Now `n = 3`.

---

#### 🪣 2. `sc.next()` reads **one word at a time**

* `sc.next()` skips whitespace automatically (like spaces and newlines),
  so it doesn’t have the *leftover newline problem* we had with `nextLine()` earlier.

If you input:

```
apple banana cat
```

or even

```
apple
banana
cat
```

it works the same ✅

---

#### 💾 3. Loop stores each string inside the array

After the loop:

```
str = [apple, banana, cat]
```

---

#### 🖨️ 4. Printing with `Arrays.toString(str)`

This nicely prints the array as:

```
[apple, banana, cat]
```

Then you change one element:

```java
str[1] = "subh";
```

and print again:

```
[apple, subh, cat]
```

---

### ⚠️ Just one tiny safety tip:

If `n` might be `1`, this line will cause an error:

```java
str[1] = "subh";
```

because index 1 doesn’t exist in a 1-element array.

You can fix it easily:

```java
if (n > 1) {
    str[1] = "subh";
}
```

---

### 💡 Final Example:

**Input:**

```
3
apple banana cat
```

**Output:**

```
[apple, banana, cat]
[apple, subh, cat]
```

---

