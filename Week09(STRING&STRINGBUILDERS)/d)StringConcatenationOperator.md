
---

## Rule #1 🔥

### `+` behaves DIFFERENTLY based on operand types

Java checks **left to right**.

---

## 1️⃣ Primitive + Primitive → **math**

```java
System.out.println('a' + 'b');
```

What happens:

* `'a'` → 97
* `'b'` → 98
* 97 + 98 = **195**

Output:

```
195
```

👉 **chars are numbers internally**

---

## 2️⃣ String + String → **concatenation**

```java
System.out.println("a" + "b");
```

Output:

```
ab
```

👉 String + anything = joining

---

## 3️⃣ char arithmetic + cast

```java
System.out.println((char)('a' + 3));
```

* `'a'` → 97
* 97 + 3 = 100
* `(char)100` → `'d'`

Output:

```
d
```

👉 Cast converts number → character

---

## 4️⃣ String + int

```java
System.out.println("a" + 1);
```

What happens:

* `1` → converted to `"1"`
* `"a" + "1"` → `"a1"`

Output:

```
a1
```

👉 **If ONE operand is String → everything becomes String**

---

## 5️⃣ String + Object

```java
System.out.println("Kunal" + new ArrayList<>());
```

* `ArrayList.toString()` → `"[]"`
* `"Kunal" + "[]"`

Output:

```
Kunal[]
```

👉 Objects are converted using `toString()`

---

## 6️⃣ String + Wrapper object

```java
System.out.println("Kunal" + new Integer(56));
```

* `Integer.toString()` → `"56"`

Output:

```
Kunal56
```

👉 Same rule: **String present → concat**

---

## 7️⃣ Object + Object ❌ ERROR

```java
System.out.println(new Integer(56) + new ArrayList<>());
```

❌ Compile-time error

Why?

* No `+` defined for **Object + Object**
* Neither side is String
* Java doesn’t know what to do

👉 **`+` is NOT magic**

---

## 8️⃣ Force String to make it work

```java
System.out.println(new Integer(56) + "" + new ArrayList<>());
```

What happens:

* `""` is a String
* Everything becomes String
* `"56" + "[]"`

Output:

```
56[]
```

👉 Empty string trick forces concatenation

---

## 🔒 FINAL BRAIN LOCK 

### Remember ONLY this 👇

1. `+` works for **numbers → addition**
2. `+` works for **String → concatenation**
3. If **ANY operand is String → everything becomes String**
4. Objects use `toString()` automatically
5. Object + Object ❌ unless String is involved
6. Empty string `""` can **force concatenation**

---

###  summary 

> **Java’s `+` is dumb but predictable.
> Math if numbers.
> Join if String.
> Error if confused.**

---

## What are **primitives**?

👉 **Primitive types are basic data types that store actual values, not objects.**

They are **NOT classes**.
They don’t have methods.
They just hold data.

---

## Java has **8 primitive types** (memorize this list)

### 🔢 Numbers

* `byte`
* `short`
* `int`
* `long`

### 🔢 Decimals

* `float`
* `double`

### 🔤 Character

* `char`

### ✅ True / False

* `boolean`

That’s it. Only **8**.

---

## Example

```java
int a = 10;
float b = 3.5f;
char c = 'a';
boolean ok = true;
```

These variables store the **actual value directly**.

---

## Primitive vs Object (important difference)

### Primitive

```java
int x = 5;
```

* Stores `5`
* No methods
* Faster
* No `toString()`

### Object

```java
Integer y = 5;
```

* Stores a **reference**
* Has methods
* Uses heap memory
* Can be `null`

---

## Why this matters for `+` operator

* **Primitive + Primitive** → **math**
* `char` is primitive → behaves like a number
* Object + Object ❌
* String involved → concatenation

---

## One-line brain lock 🔒

> **Primitives are basic value types. Objects are references to data.**


