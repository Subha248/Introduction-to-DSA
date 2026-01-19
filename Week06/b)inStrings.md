
---

### 💻 Full Code:

```java
package com.kunal;

public class SearchInStrings {
    public static void main(String[] args) {
        String name = "Kunal";
        char target = 'u';
        System.out.println(search2(name, target));
    }

    static boolean search2(String str, char target) {
        // if the string is empty, there’s nothing to search
        if (str.length() == 0) {
            return false;
        }

        // for-each loop goes through every character in the string
        for (char ch : str.toCharArray()) {
            if (ch == target) {
                // if the target matches current character, return true
                return true;
            }
        }

        // if loop finishes without finding target, return false
        return false;
    }
}
```

---

### 🧠 Step-by-step Explanation:

#### 1️⃣ `String name = "Kunal";`

You’re creating a string named `"Kunal"`.

#### 2️⃣ `char target = 'u';`

You’re setting the target character to `'u'`, which we’ll try to find inside `"Kunal"`.

#### 3️⃣ `System.out.println(search2(name, target));`

This calls the `search2` method and prints the result (`true` or `false`).

---

### 🔍 Inside the `search2` method:

#### `if (str.length() == 0)`

Checks if the string is empty.
If yes → returns `false` because there’s nothing to search.

---

#### `for (char ch : str.toCharArray())`

This is a **for-each loop**.
It means:

> “For every character `ch` in the string, do the following…”

Example:

```
String = "Kunal"
str.toCharArray() → ['K', 'u', 'n', 'a', 'l']
```

So the loop runs like this:

```
1st → ch = 'K'
2nd → ch = 'u'
3rd → ch = 'n'
4th → ch = 'a'
5th → ch = 'l'
```

---

#### `if (ch == target)`

Each time, it compares the current character `ch` with the `target`.

If match → return `true` immediately.
Because once you’ve found it, no need to continue searching.

---

#### `return false`

If the loop finishes and never found the target, this line executes, meaning:

> “Target not found in the string.”

---

### ⚡ Output:

```
true
```

Because the character `'u'` **is** in `"Kunal"`.

---

