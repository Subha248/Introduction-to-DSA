

---

## 🔹 PROGRAM 1 (FAST, GOOD)

```java
for(int i = 0; i < 26; i++){
    char ch = (char)('a' + i);
    System.out.println(ch);
}
```

### Step-by-step

1️⃣ `i = 0`

* `'a'` → 97
* `97 + 0 = 97`
* `(char)97 → 'a'`
* Prints `a`

2️⃣ `i = 1`

* `(char)('a' + 1)` → `b`

3️⃣ Continues till:

* `i = 25` → `z`

### Output

```
a
b
c
...
z
```

### Why this is FAST

* No string creation
* Only `char` printing
* No extra objects
* Minimal memory usage

---

## 🔹 PROGRAM 2 (SLOW, BAD PRACTICE)

```java
String series = "";
for(int i = 0; i < 26; i++){
    char ch = (char)('a' + i);
    series = series + ch;
}
System.out.println(series);
```

### Step-by-step (THIS IS IMPORTANT)

#### Initial:

```
series = ""
```

---

### Iteration 1:

```java
series = "" + 'a'
```

* Creates NEW string `"a"`

---

### Iteration 2:

```java
series = "a" + 'b'
```

* Creates NEW string `"ab"`

---

### Iteration 3:

```java
series = "ab" + 'c'
```

* Creates NEW string `"abc"`

---

### 🔥 What’s really happening

* **Strings are immutable**
* Every `+` creates a **NEW String object**
* Old strings become garbage

For 26 characters →
👉 **26 string objects created**

For 10,000 loops →
👉 **10,000 string objects** 💀

---

## 🔥 INTERVIEW RULE (VERY IMPORTANT)

> **Never use `String +` inside loops**

Because:

* Creates many objects
* Slow
* Wastes memory
* Garbage Collector gets overloaded

---

## ✅ Correct Way (INTERVIEW ANSWER)

```java
StringBuilder sb = new StringBuilder();

for(int i = 0; i < 26; i++){
    char ch = (char)('a' + i);
    sb.append(ch);
}

System.out.println(sb.toString());
```

### Why this is FAST

* `StringBuilder` is **mutable**
* No new objects per iteration
* Same memory reused
* Best performance

---

## 🔒 FINAL BRAIN LOCK (MEMORIZE)

* Strings are **immutable**
* `String +` in loop = **BAD**
* Creates **new object every time**
* Use **StringBuilder** for performance
* Interviewers LOVE this answer

---

### One killer interview line 😎

> “Using `String` concatenation in loops is inefficient due to immutability; `StringBuilder` should be used instead.”

