

---

```java
// 🌸 BlockScopeDemo.java
// 🧩 Java Scope Demo – Shows how variable scope works inside and outside blocks

public class BlockScopeDemo {
    public static void main(String[] args) {

        int a = 10;
        String name = "Kunal";

        // 👉 This is just a block (not a new method or class)
        {
            // Reassigning existing variables declared outside
            a = 78;          // modifies outer 'a'
            a = 100;         // modifies outer 'a' again
            System.out.println("Inside block - a: " + a);  // prints 100

            name = "Rahul";  // modifies outer 'name'
            System.out.println("Inside block - name: " + name);  // prints Rahul
        }

        // ✅ Still accessible here because we didn't redeclare them inside
        System.out.println("Outside block - a: " + a);    // prints 100
        System.out.println("Outside block - name: " + name);  // prints Rahul

        // 🌼 Example of variable declared inside a block (goes out of scope)
        {
            int b = 50;
            System.out.println("Inside block - b: " + b);
        }

        // ❌ The following line would cause an error, because 'b' is out of scope
        // System.out.println(b); 
    }
}
```

---

### 💡 **Output:**

```
Inside block - a: 100
Inside block - name: Rahul
Outside block - a: 100
Outside block - name: Rahul
Inside block - b: 50
```

---

### 🧠 **Summary:**

* Variables declared **outside** a block remain accessible *inside*.
* Modifying them inside a block **changes their values outside** as well.
* Variables declared **inside a block** disappear once the block ends (out of scope).

---

### 📌 **GitHub-style short description / tag:**

> “🧩 Java Scope Demo – Shows how variable shadowing and block scoping work inside methods.”

---

