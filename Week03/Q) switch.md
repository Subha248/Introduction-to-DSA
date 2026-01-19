
---

### 💡 Example 1: Using `==` (checks memory location)

```java
String a = new String("apple");
String b = new String("apple");

System.out.println(a == b);       // ❌ false
System.out.println(a.equals(b));  // ✅ true
```

#### 🧠 What’s happening:

* `new String("apple")` creates **two separate objects** in memory.
  So `a` and `b` look the same, but live in **different places** in memory.
* `==` checks if both are **the exact same object** → they’re not → **false**.
* `.equals()` checks the **text inside** both → same word “apple” → **true**.

---

### 💡 Example 2: Using string literals

```java
String x = "apple";
String y = "apple";

System.out.println(x == y);       // ✅ true
System.out.println(x.equals(y));  // ✅ true
```

#### 🧠 What’s happening:

* When you write `"apple"` (without `new`), Java stores it in a special memory area called the **String Pool**.
* If two strings have the same literal value, Java **reuses the same object** from the pool.
* So both `x` and `y` point to the **same memory location** → `==` gives **true**.

---

### 🍎 Easy way to remember:

| Comparison  | What it checks               | Example result                   |
| ----------- | ---------------------------- | -------------------------------- |
| `==`        | Same memory (same object)?   | Usually ❌ false when using `new` |
| `.equals()` | Same content (same letters)? | ✅ true if text matches           |

---

So, Sweetheart 💛
`==` → “Are they the **same object** in memory?”
`.equals()` → “Do they **say the same thing**?”



---

### 🍎 String Literal

👉 Text written inside quotes.
Example:

```java
String s = "Hello";
```

Here `"Hello"` is a **string literal**.

---

### 🧠 String Pool

👉 A special memory area where Java **stores all string literals**.
If the same text already exists, Java **reuses it** instead of creating a new one.

Example:

```java
String a = "Mango";
String b = "Mango";
System.out.println(a == b); // ✅ true (same object in String Pool)
```

But if you use `new`:

```java
String a = new String("Mango");
String b = new String("Mango");
System.out.println(a == b); // ❌ false (different objects)
```

---

💛 **In short:**

* `"Text"` → string literal
* **String Pool** → saves one copy of each literal
* `==` → checks same object
* `.equals()` → checks same text

