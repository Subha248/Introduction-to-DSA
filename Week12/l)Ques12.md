
---

## 🔥 Question 12: “Check if a number is a power of 2”

### First: kill the fear

This question is NOT about loops.
It’s NOT about math.
It’s about **binary patterns**.

---

## Step 1️⃣: What does “power of 2” REALLY mean?

Powers of 2:

```
1   → 2⁰
2   → 2¹
4   → 2²
8   → 2³
16  → 2⁴
```

Now binary:

```
1   → 0001
2   → 0010
4   → 0100
8   → 1000
16  → 10000
```

🚨 OBSERVATION (this is everything):
👉 **Exactly ONE `1` bit**

That’s the definition in binary.

---

## Step 2️⃣: What does `n - 1` do in binary?

Take one example.

### n = 8

```
n     = 1000
n - 1 = 0111
```

What happened?

* the **only `1`** became `0`
* everything to the right became `1`

This ALWAYS happens for powers of 2.

---

## Step 3️⃣: Now the AND trick (this is the “aha” moment)

AND rule:

```
1 & 1 = 1
anything else = 0
```

Now:

```
1000
&0111
-----
0000
```

Result = **0**

👉 Meaning:
There was **no position** where both numbers had `1`
👉 So there was **only one `1` originally**

---

## Step 4️⃣: Try a non-power (so your brain trusts it)

### n = 10

```
10 = 1010
9  = 1001
```

AND:

```
1010
&1001
-----
1000  ❌ not zero
```

More than one `1` → **NOT power of 2**

---

## Step 5️⃣: How YOUR brain should think before coding

Say this mentally:

> “If a number has only one set bit,
> then AND-ing it with (n − 1) removes that bit
> and gives zero.”

That’s the logic. Period.

---

## Step 6️⃣: Java code (exam-ready)

```java
public class Main {
    public static void main(String[] args) {
        int n = 16;

        if (n > 0 && (n & (n - 1)) == 0) {
            System.out.println("Power of 2");
        } else {
            System.out.println("Not a power of 2");
        }
    }
}
```

⚠️ `n > 0` is IMPORTANT
Because `0 & -1 = 0` (Java being sneaky)

---

## One-line memory hook 🧠

> **Power of 2 → only one `1`
> `n & (n - 1)` deletes that `1`
> result zero → valid**

---

