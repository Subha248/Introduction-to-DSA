

1️⃣ **All modulo properties you MUST know**
2️⃣ **Fermat’s theorem explained like a human**
3️⃣ **Fast exponentiation (binary exponentiation)**


# ✅ 1. BASIC MODULO PROPERTIES (ONLY WHAT YOU NEED)

## **1️⃣ Addition**

```
(A + B) % M
```

That’s it.

---

## **2️⃣ Subtraction (IMPORTANT)**

```
(A - B + M) % M
```

That `+M` avoids negative results.

---

## **3️⃣ Multiplication**

```
(A * B) % M
```

---

## **4️⃣ Division (CAN’T DO DIRECTLY)**

Wrong:

```
(A / B) % M ❌
```

Correct:

```
(A * inverse(B)) % M ✔
```

---

# 🔥 2. MODULAR INVERSE (WHAT YOU NEED TO KNOW)

You only need ONE line of understanding:

> In modulo arithmetic, we “undo” division by multiplying with inverse(B).

And inverse(B) only exists when:

```
gcd(B, M) = 1
```

(co-prime)

---

# 🔥 3. FERMAT’S LITTLE THEOREM (THE ACTUAL USEFUL PART)

You don’t need the full theory.
You ONLY need this:

If **M is prime** (like 1e9+7):

```
B^(M-1) ≡ 1 (mod M)
```

Which implies:

```
B^(M-2) ≡ B⁻¹ (mod M)
```

SO:

### ⭐ Final usable formula:

```
inverse(B) = B^(M-2) % M
```

That’s literally the whole point of Fermat for DSA.
You don’t need more.

---

# 🔥 4. FAST EXPONENTIATION (YOU WILL USE THIS 100 TIMES)

You MUST know how to compute:

```
A^X % M
```

in **O(log X)** time using binary exponentiation.

Without this, you can’t compute inverse using Fermat.

### Concept (super simple):

* If X is even:

  ```
  A^X = (A^(X/2))^2
  ```
* If X is odd:

  ```
  A^X = A * A^(X-1)
  ```

This reduces time drastically.

---

# 🎯 THE ULTIMATE DSA CHEAT SHEET

Here is the final set of things you **MUST** memorize/understand:

```
(1) (A + B) % M
(2) (A - B + M) % M
(3) (A * B) % M
(4) division -> A * inverse(B) % M
(5) inverse(B) = B^(M-2) % M   // only when M is prime
(6) fast exponentiation O(log N)
```

---

