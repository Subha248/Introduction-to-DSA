
---

## ARRAYS (mutable)

```java
int[] arr = {2, 3, 5, 4, 19};
```

* `arr` → reference variable (stack)
* Actual array → object in heap

If you do:

```java
arr[0] = 99;
```

* Same array object changes
* Anyone pointing to it sees the change

**Conclusion:**
👉 Arrays are **mutable**
👉 Change = object itself changes

---

## STRINGS (immutable)

```java
String name = "suba";
```

* `String` → class
* `name` → reference variable (stack)
* `"suba"` → object (heap → **String Pool**)

```java
System.out.println(name); // suba
```

Normal output.

---

## STRING POOL (important)

* String Pool = special memory **inside heap**
* Stores **string literals**
* Same value is **not created again**

---

## MAIN QUESTION (this is the core)

```java
String a = "suba";
String b = "suba";
```

What happens?

* Only **ONE `"suba"` object** is created
* Stored in **String Pool**
* `a` and `b` both point to **the SAME object**

So correct understanding is:
👉 **a and b (stack) → one "suba" (heap)**

NOT two objects.

---

## WHY Java does this?

1. **Memory saving** (String Pool)
2. **Security** (immutability)

If strings were mutable:

* Changing `a` would change `b`
* Passwords, usernames = 💀

So Java said:
👉 “No editing strings. New object only.”

---

## WHEN YOU “CHANGE” A STRING

```java
a = "kumar";
```

What really happens:

* `"suba"` is NOT changed
* New `"kumar"` object is created
* `a` now points to `"kumar"`
* `"suba"` stays untouched

---

## FINAL BRAIN LOCK 🔒 (remember this)

* Arrays → **mutable**
* Strings → **immutable**
* Same string literal → **same object (String Pool)**
* String change → **new object, reference changes**
* Array change → **same object changes**

