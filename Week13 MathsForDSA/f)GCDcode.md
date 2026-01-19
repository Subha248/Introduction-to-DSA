
---

# 1️⃣ **QUESTION**

Find the GCD of **4** and **9** using Euclid’s Algorithm (using recursion).

---

# 2️⃣ **FULL CODE**

```java
public class GCD_LCM {
    public static void main(String[] args) {
        System.out.println(gcd(4, 9));
    }

    static int gcd(int a, int b) {
        if (a == 0) {
            return b;
        }
        return gcd(b % a, a);
    }
}
```

---

# 3️⃣ **EXPLANATION (LINE BY LINE)**

### **`public class GCD_LCM {`**

→ Starts the class. Java needs everything inside a class.

---

### **`public static void main(String[] args) {`**

→ Entry point. Java starts execution here.

---

### **`System.out.println(gcd(4, 9));`**

→ Calls the `gcd` function with **4** and **9**.
→ Whatever the result is, print it.

---

### **`static int gcd(int a, int b) {`**

→ Defines a function named **gcd** which takes `a` and `b`.

---

### **`if (a == 0) { return b; }`**

→ Base case.
→ If `a` becomes 0 → GCD is the other number `b`.

---

### **`return gcd(b % a, a);`**

→ The Euclidean step.
→ Calculate remainder `b % a`.
→ Swap positions → call gcd again.

---

# 4️⃣ **DRY RUN (STEP BY STEP)**

### **Step 1: gcd(4, 9)**

* a = 4, b = 9
* 4 != 0
* compute `9 % 4 = 1`
  → Next call: `gcd(1, 4)`

---

### **Step 2: gcd(1, 4)**

* a = 1, b = 4
* 1 != 0
* compute `4 % 1 = 0`
  → Next call: `gcd(0, 1)`

---

### **Step 3: gcd(0, 1)**

* a = 0, b = 1
  → Base case triggered
  → return 1

---

### **Recursive Return Path**

* gcd(0, 1) returns 1
* gcd(1, 4) returns 1
* gcd(4, 9) returns 1

---

# 5️⃣ **OUTPUT**

```
1
```

---

