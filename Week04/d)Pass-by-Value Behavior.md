
If you use an **array instead of a String**, then yes — it **will change!** 🪄

Let’s see it clearly 👇

---

### 💥 String case (no change)

```java
public class Demo {
    public static void main(String[] args) {
        String name = "subha";
        change(name);
        System.out.println(name); // 👉 prints "subha"
    }

    static void change(String naam) {
        naam = "pradha"; // creates NEW string, doesn’t touch old one
    }
}
```

➡️ Output:

```
subha
```

Because `String` is **immutable**, and `naam = "pradha"` just makes `naam` point to a *different* string.
The original `"subha"` stays untouched.

---

### 💫 Array case (changes!)

```java
public class Demo {
    public static void main(String[] args) {
        String[] name = {"subha"};
        change(name);
        System.out.println(name[0]); // 👉 prints "pradha"
    }

    static void change(String[] naam) {
        naam[0] = "pradha"; // changes the element inside the same array box
    }
}
```

➡️ Output:

```
pradha
```

Because arrays are **mutable**, so when you change an element (`naam[0]`),
you are **modifying the same memory box** that both `name` and `naam` share.

---

### 🌈 In short:

| Type   | Mutable? | Inside method can modify original? |
| ------ | -------- | ---------------------------------- |
| String | ❌ No     | ❌ Cannot change original           |
| Array  | ✅ Yes    | ✅ Can change original              |

---

