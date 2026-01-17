### 📝 LeetCode 204: Count Primes — Problem Statement

Question:

“Given an integer n, return the number of prime numbers strictly less than n.”

Primes = numbers that have no factors except 1 and themselves.
---

# ✅ **FULL CODE**

```java
public class SieveExample {
    public static void main(String[] args) {
        int n = 10;

        // isNotPrime[i] = true means NOT PRIME
        // false means MIGHT be prime
        boolean[] isNotPrime = new boolean[n + 1];

        sieve(n, isNotPrime);
    }

    public static void sieve(int n, boolean[] isNotPrime) {
        for (int number = 2; number * number <= n; number++) {

            // If this number is still prime (false)
            if (!isNotPrime[number]) {

                // Mark all multiples as NOT prime
                for (int multiple = number * 2; multiple <= n; multiple += number) {
                    isNotPrime[multiple] = true;
                }
            }
        }

        // Print prime numbers
        for (int number = 2; number <= n; number++) {
            if (!isNotPrime[number]) {
                System.out.print(number + " ");
            }
        }
    }
}
```

---

# 🔥 DRY RUN (for n = 10)

Initial array (Java fills everything with false):

```
index:  0 1 2 3 4 5 6 7 8 9 10
value:  F F F F F F F F F F F
```

F = false = maybe prime
T = true = not prime

---

# ⭐ Step 1 — number = 2

`2*2 <= 10` ✔️
`isNotPrime[2]` = false ✔️ → still prime

Mark multiples of 2:

```
4 = T
6 = T
8 = T
10 = T
```

Array now:

```
0 F
1 F
2 F  (prime)
3 F  (prime)
4 T
5 F  (prime)
6 T
7 F (prime)
8 T
9 F (prime for now)
10 T
```

---

# ⭐ Step 2 — number = 3

`3*3 <= 10` ✔️
`isNotPrime[3] = false` ✔️ → prime

Mark multiples:

```
6 = already T
9 = T
```

Array now:

```
2 F
3 F
4 T
5 F
6 T
7 F
8 T
9 T
10 T
```

---

# ⭐ Step 3 — number = 4

`4*4 <= 10` ❌
Loop stops.

---

# ⭐ Final Print Loop

Print all numbers where `isNotPrime[number] == false`:

```
2 → prime
3 → prime
5 → prime
7 → prime
```

---

# 🎉 OUTPUT

```
2 3 5 7
```

---

