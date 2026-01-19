

---

### 🌼 **Program: Shadowing in Java**

```java
package com.kunal;

public class Shadowing {
    // 🌍 Class-level (static) variable
    static int x = 90;  // This will be shadowed inside main()

    public static void main(String[] args) {
        System.out.println(x);  // prints 90 (uses class-level variable)

        int x = 40;  // 🎭 This local variable shadows the class-level 'x'
        System.out.println(x);  // prints 40 (uses local variable)

        fun();  // call another method
    }

    static void fun() {
        // No local variable 'x' here,
        // so it uses the class-level variable instead.
        System.out.println(x);  // prints 90
    }
}
```

---

### 💡 **Explanation (Line by Line):**

1. **`static int x = 90;`**
   → A class-level static variable named `x` is created with a value of 90.
   This variable belongs to the *class itself*, not to any single method.

2. **`public static void main(String[] args)`**
   → The main method starts. Inside it, you can access class variables directly.

3. **`System.out.println(x);`**
   → No local variable named `x` exists yet, so it prints the **class variable’s value (90)**.

4. **`int x = 40;`**
   → A new *local variable* named `x` is declared inside `main()`.
   This local `x` **shadows** (hides) the class-level `x` inside this method only.

5. **`System.out.println(x);`**
   → Prints **40**, since the local variable `x` is used instead of the class one.

6. **`fun();`**
   → Calls the static method `fun()`.

7. **Inside `fun()`**
   → There is no local `x` declared here, so Java looks for `x` in the outer (class) scope.
   → Finds the **class-level `x = 90`**, so it prints **90**.

---

### 🔎 **Output:**

```
90
40
90
```

---

### 💬 **Key Takeaway (for GitHub summary):**

> **Shadowing in Java** occurs when a variable declared within a narrower scope (like a method) has the same name as one in an outer scope (like the class).
> The inner variable hides — or *“shadows”* — the outer one within that method.
> Outside the method, the outer (class) variable is still accessible.

---

