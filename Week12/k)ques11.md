
---

## 🧠 FIRST QUESTION — THINK LIKE A PROGRAMMER, NOT A MATHEMATICIAN

**Question in simple English:**
👉 “Given `n`, find the sum of numbers in the `n`th row of Pascal’s Triangle.”

That’s it. Nothing else.

---

## Step 1️⃣: Observe like a lazy coder

You don’t want loops.
You don’t want arrays.
You don’t want Pascal’s Triangle at all.

So you **look for a pattern**.

```
n = 0 → sum = 1
n = 1 → sum = 2
n = 2 → sum = 4
n = 3 → sum = 8
n = 4 → sum = 16
```

Now pause.

Ask yourself ONE question:

> “What operation keeps doubling the number?”

Answer: **multiply by 2**

So:

```
sum = 2ⁿ
```

That’s already the whole logic.

---

## Step 2️⃣: Now think in **Java / binary**, not math

Java doesn’t like `2ⁿ`.
Java LOVES **bit shifting**.

### Remember this forever:

```
1 << n   ===   2ⁿ
```

Why?

Because:

* `1` in binary = `0001`
* shifting left adds zeros
* adding zeros = doubling

Example:

```
1 << 0 → 0001 → 1
1 << 1 → 0010 → 2
1 << 2 → 0100 → 4
1 << 3 → 1000 → 8
```

Same numbers. No magic.

---

## Step 3️⃣: How YOUR brain should say it before coding

Say this in your head:

> “I don’t care about Pascal’s Triangle.
> I only care about the row number `n`.
> The sum is just 2 raised to n.
> In Java, 2ⁿ is written as `1 << n`.”

Boom. Done.

---

## Step 4️⃣: Now write the Java code (minimal, clean)

```java
public class Main {
    public static void main(String[] args) {
        int n = 4;          // row number
        int sum = 1 << n;   // sum of nth row
        System.out.println(sum);
    }
}
```

Output:

```
16
```

---

## Step 5️⃣: If examiner asks “explain logic” (easy marks)

Say this 👇 (you can literally memorize):

> “The sum of elements in the nth row of Pascal’s Triangle is 2ⁿ.
> Using bit manipulation, 2ⁿ can be computed as `1 << n`,
> because left shifting 1 by n positions multiplies it by 2ⁿ.”

That’s a full-mark answer. No overthinking.

---

## Final mental shortcut 🔑

* Pascal row sum → **power of 2**
* Power of 2 → **left shift**
* Left shift → **`1 << n`**

