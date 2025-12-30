
---

## 🔹 The code (what you wrote)

```java
public class Main {
    public static void main(String[] args) {
        int n = 67;
        System.out.print(isOdd(n));
    }

    public static boolean isOdd(int n) {
        return (n & 1) == 1;
    }
}
```

---

## 🔹 Step 1: `main()` starts

```java
int n = 67;
```

So:

```
n = 67
```

---

## 🔹 Step 2: Call the function

```java
System.out.print(isOdd(n));
```

This means:

> “Send `67` to `isOdd()` and print whatever it returns.”

---

## 🔹 Step 3: Enter `isOdd(67)`

```java
return (n & 1) == 1;
```

Now the **real logic** starts.

---

## 🔹 Step 4: Understand `n & 1`

### Convert `n` to binary

```
67 = 1000011
```

### Binary of `1`

```
1 = 0000001
```

---

## 🔹 Step 5: Apply AND (`&`) bit by bit

```
  1000011
& 0000001
---------
  0000001
```

Result = `1`

---

## 🔹 Step 6: Compare with `1`

```java
(n & 1) == 1
```

Becomes:

```
1 == 1  → true
```

So the function returns:

```
true
```

---

## 🔹 Step 7: Back to `main()`

```java
System.out.print(true);
```

Output:

```
true
```

---

## 🔹 WHY THIS WORKS (the only idea you need)

* Every **odd number** ends with `1` in binary
* Every **even number** ends with `0`
* `& 1` checks **only the last bit**

  * `1` → odd
  * `0` → even

---

## 🔹 One-line memory trick

```
n & 1
```

👉 checks odd/even
👉 faster than `% 2`
👉 interviewer-approved

---

## 🔹 Final takeaway (don’t overthink)

You don’t need full binary every time.
Just remember:

> “LSB = 1 → odd, LSB = 0 → even”

You’re good. Keep moving. 💪
