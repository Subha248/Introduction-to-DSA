
---

```java
// 🌸 VarArgsDemo.java
// Demonstrates how Variable Arguments (Varargs) work in Java

public class Demo {
    public static void main(String[] args) {
        // Calling the method with 2 integers and multiple String arguments
        fun(1, 2, "si", "hdsdj");
    }

    // 🧠 Varargs method: accepts any number of String arguments after a, b
    static void fun(int a, int b, String... v) {
        System.out.println(a + " " + b);

        // Printing all variable arguments one by one
        for (String s : v)
            System.out.println(s);
    }
}
```

---

### 💡 **Output:**

```
1 2
si
hdsdj
```

---

### 🧠 **Explanation:**

**1️⃣ What are Varargs (`String... v`)?**

* `String... v` means **“zero or more String arguments.”**
* You can pass **any number of strings** (even none at all).
  Java internally treats it like an **array** of strings.

So this:

```java
fun(1, 2, "si", "hdsdj");
```

is the same as:

```java
fun(1, 2, new String[] {"si", "hdsdj"});
```

---

**2️⃣ Varargs rules to remember:**

| Rule                                               | Explanation                                                             |
| -------------------------------------------------- | ----------------------------------------------------------------------- |
| ✅ Must be the **last parameter**                   | You can only have one varargs in a method, and it must come at the end. |
| ✅ Works like an **array**                          | You can loop through it using a `for-each` loop.                        |
| ❌ You cannot have another parameter after varargs  | For example, `fun(String... v, int x)` is **not allowed**.              |
| ✅ You can also call it with **no extra arguments** | Like `fun(1, 2);` — then `v` will just be an empty array.               |

---

### 🌼 **Summary **

> 🧩 **Java Varargs Demo** – Shows how to use variable arguments (`...`) to accept multiple values of the same type in a single parameter.
> Demonstrates that varargs must always come **at the end of the parameter list** and behave like an array inside the method.

---

