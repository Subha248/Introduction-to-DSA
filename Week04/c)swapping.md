
---

```java
// 🌸 Java Program: Swap Two Numbers Using a Temporary Variable
// Short explanation included for GitHub

public class Demo {

    public static void main(String[] args) {
        int a = 10;
        int b = 20;

        // Swap process:
        int temp = a;  // temp stores a (10)
        a = b;         // a stores b (20)
        b = temp;      // b stores temp (10)

        // Print swapped values
        System.out.print(a + " " + b); // Output: 20 10
    }
}

/* Short Explanation:
1. temp = a → store original a
2. a = b → move b to a
3. b = temp → move original a to b
*/
```

---
--- 
Ahhh sweetheart 😄 — I totally get why this feels confusing! Let’s break it down **step by step** and make it super clear 💖

---

### **1️⃣ First program**

```java
String name = "subha";
changename(name);

public static void changename(String naam){
    System.out.print(naam);
}
```

**What happens:**

1. `name = "subha"` in `main`.
2. You call `changename(name)`.
3. Inside `changename`, `naam` is a **copy of the reference** to `"subha"`.
4. You print `naam` → prints `"subha"`.

✅ **Output:**

```
subha
```

---

### **2️⃣ Second program**

```java
String name = "subha";
changename(name);

public static void changename(String naam){
    naam = "oo";
    System.out.print(naam);
}
```

**What happens:**

1. `name = "subha"` in `main`.
2. You call `changename(name)`.
3. Inside `changename`, `naam` is a **copy of the reference** to `"subha"`.
4. You do `naam = "oo"` → this makes **the local variable `naam` now point to a new string `"oo"`**.
5. You print `naam` → prints `"oo"`.

✅ **Output:**

```
oo
```

---

### **Important distinction**

* **Step 1:** You didn’t change `naam` → printed the original `"subha"`.
* **Step 2:** You assigned a new string `"oo"` to `naam` → printed `"oo"`.
* But notice: the original `name` in `main` **is still `"subha"`**, only the local copy `naam` changed.

If you print `name` after calling `changename(name)`, it will **still be `"subha"`** in both cases.

---

### **Short rule**

1. **Printing the parameter as-is** → prints the value passed.
2. **Assigning a new value to the parameter** → prints the new value, **but doesn’t affect the original variable in `main`**.

---

