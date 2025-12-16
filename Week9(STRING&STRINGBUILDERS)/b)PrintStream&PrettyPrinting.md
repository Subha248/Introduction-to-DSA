
---

### What to remember about `System.out.println`

* **`PrintStream` is a class**
* **`out` is NOT a class**
* `out` is a **variable (reference)** of type **`PrintStream`**
* `System.out` represents the **console (standard output)**
* `println()` is a **method** inside the `PrintStream` class
* Java already built all this so **printing is easy**
* **Don’t overthink internals now** — full breakdown comes later in OOP

---

### One-line memory lock 🔒

> `System.out` is a reference of type `PrintStream`, and `println()` is the method that prints to the console.
Cool. **ONLY what you need to get into your head. Nothing extra.**



---
### PRETTY PRINTING
```java
package com.kunal;
```

* Puts this class in a **package** called `com.kunal`
* Packages help **organize code**
* Must match the folder structure, but you don’t need to stress about it yet

---

```java
public class PrettyPrinting {
```

* Declares a **public class** named `PrettyPrinting`
* **File name must match class name** → `PrettyPrinting.java`
* One public class per file

---

```java
public static void main(String[] args) {
```

* **Entry point** of the program
* JVM starts running code from here
* Without this, program won’t execute

---

```java
float a = 453.1234f;
```

* `float` = decimal number type (32-bit)
* **`f` is mandatory** because Java treats all decimals as `double` by default
* `a` stores the number `453.1234`

---

```java
System.out.printf("Formatted number is %.2f", a);
```

* `System` → built-in class
* `out` → reference variable (PrintStream) that points to the console
* `printf()` → prints formatted text

`"%.2f"` → formatting specifier:

* `%` → format placeholder
* `.2` → **2 digits after decimal**
* `f` → floating-point number

**So output will be:**

```
Formatted number is 453.12
```

> `printf` does **not automatically go to a new line** (unlike `println`)

---

```java
}
```

* Closes `main()` method

```java
}
```

* Closes class

---

### 🔒 Key things to remember

1. File name = public class name
2. `main()` is **entry point**
3. `float` literals need `f` (`double` by default)
4. `printf()` formats output
5. `%.2f` → **2 digits after decimal**

---

