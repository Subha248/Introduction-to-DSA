
---

## 🔹 The code (what it does overall)

This code finds the **one number that appears only once**.
All others appear **twice**.

Array:

```
{1, 2, 3, 4, 3, 2, 1}
```

Only **4** is unique.

---

## 🔹 Step 1: `main()` starts

```java
int[] arr = {1,2,3,4,3,2,1};
System.out.print(Numbers(arr));
```

So:

* `arr` is passed to `Numbers()`

---

## 🔹 Step 2: Enter `Numbers(int[] n)`

```java
int unique = 0;
```

Computer memory now:

```
unique = 0
```

---

## 🔹 Step 3: Loop starts (FOR EACH)

We go **one number at a time**.

### 🔁 Iteration 1

```
num = 1
unique = 0 ^ 1 = 1
```

Now:

```
unique = 1
```

---

### 🔁 Iteration 2

```
num = 2
unique = 1 ^ 2 = 3
```

(binary: 01 ^ 10 = 11)

Now:

```
unique = 3
```

---

### 🔁 Iteration 3

```
num = 3
unique = 3 ^ 3 = 0
```

💥 Duplicate killed itself

Now:

```
unique = 0
```

---

### 🔁 Iteration 4

```
num = 4
unique = 0 ^ 4 = 4
```

Now:

```
unique = 4
```

---

### 🔁 Iteration 5

```
num = 3
unique = 4 ^ 3 = 7
```

(binary: 100 ^ 011 = 111)

Now:

```
unique = 7
```

---

### 🔁 Iteration 6

```
num = 2
unique = 7 ^ 2 = 5
```

(binary: 111 ^ 010 = 101)

Now:

```
unique = 5
```

---

### 🔁 Iteration 7

```
num = 1
unique = 5 ^ 1 = 4
```

(binary: 101 ^ 001 = 100)

Now:

```
unique = 4
```

---

## 🔹 Step 4: Loop ends

```java
return unique;
```

Returns:

```
4
```

---

## 🔹 Step 5: Back to `main()`

```java
System.out.print(4);
```

### ✅ Output

```
4
```

---

## 🔹 WHY THIS WORKS (this is the ONLY idea you need)

XOR rules:

```
a ^ a = 0
a ^ 0 = a
```

So:

* 1 cancels 1
* 2 cancels 2
* 3 cancels 3
* only **4** never gets cancelled

Order ❌ doesn’t matter
Steps ❌ don’t matter
Result ✅ always correct

---

## 🔹 One-line exam/interview explanation

> “XOR cancels duplicate elements because a^a = 0. Since XOR is commutative, all repeated numbers cancel out, leaving the unique number.”

Say that. Move on. Win life.

---

