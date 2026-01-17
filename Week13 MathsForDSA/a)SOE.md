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
### TIME AND SPACE COMPLEXITY

# **Sieve of Eratosthenes — Simpler Explanation**

---

## **1️⃣ What it does**

* It finds **all prime numbers up to N**.
* Idea: start from 2, mark all multiples of 2 as not prime, then 3, 5, 7… skip numbers already marked.

---

## **2️⃣ Time Complexity — O(N log log N)**

Don’t panic at the letters. Here’s the **logic**:

### Step by step:

1. For each **prime number**, we mark its multiples as not prime.

   Example: N = 10

   * Prime 2 → mark 4, 6, 8, 10
   * Prime 3 → mark 6, 9
   * Prime 5 → mark 10

2. How many operations do we do in total?

   * For 2 → about N/2 operations
   * For 3 → about N/3 operations
   * For 5 → N/5 operations
   * …for all primes up to N

3. The sum of 1/2 + 1/3 + 1/5 + … (all primes) grows **really slowly**, roughly like `log(log N)`.

✅ So total operations = N × log(log N) → **much faster than checking each number individually**.

**Simple analogy:**

* If normal method = checking every number with division → takes forever for big N
* Sieve = mark multiples smartly → much faster

---

## **3️⃣ Space Complexity — O(N)**

* We need a **boolean array** of size N+1 (0 to N)
* Each slot tells us if the number is prime (false) or not (true)

**Example:**

```
N = 10
isNotPrime[0..10] = F F F F F F F F F F F
```

* We mark multiples as true
* That’s **all extra memory we need** → size proportional to N → O(N)

---

## **4️⃣ Optimizations that make it fast**

1. **Square root rule**

   * Outer loop only goes up to √N
   * Why? Multiples beyond √N are already marked by smaller numbers.

2. **Start marking from i × 2 (or i × i)**

   * No need to mark 2 × 1, 2 × 2, etc. → already done

---

## **5️⃣ Comparison**

| Method                               | Time Complexity | Space Complexity |
| ------------------------------------ | --------------- | ---------------- |
| Simple prime check (for each number) | O(N × √N)       | O(1)             |
| Sieve of Eratosthenes                | O(N log log N)  | O(N)             |

* ✅ Sieve takes **more memory** but is **much faster**, especially for large N.

---

## **6️⃣ TL;DR **

* Sieve = smart way to find all primes up to N
* Mark multiples of each prime → don’t check everything
* Time = N log log N → super fast
* Space = N → need a boolean array
* Outer loop stops at √N → no need to check after that
* Start marking multiples from 2×prime or prime² → small efficiency gain

---

---

# **O(1) vs O(N) Space — Quick Table**

| Feature                      | O(1) Space                         | O(N) Space                                          |
| ---------------------------- | ---------------------------------- | --------------------------------------------------- |
| **Memory grows with input?** | No                                 | Yes                                                 |
| **Extra memory used**        | A few variables only               | Array / list / map that grows with N                |
| **Example 1**                | Sum of 1…N with a single variable  | Sieve of Eratosthenes storing prime status in array |
| **Example 2**                | Find max in array using 1 variable | Storing all Fibonacci numbers in an array           |
| **Analogy**                  | 1 chair for all students           | A chair for every student                           |

---

# **Why Sieve = O(N) space**

```java
boolean[] isNotPrime = new boolean[n+1];
```

* You need **1 slot for every number from 0 → n** to mark prime/not prime
* Memory grows **directly with N** → O(N)

---

# **Why simple check = O(1) space**

```java
int count = 0;
for(int i=2;i<n;i++){
    if(isPrime(i)) count++;
}
```

* You only use **count and i** → **same memory no matter how big N is** → O(1)

---

# **Gen Z Version**

* **O(1) = tiny backpack** → fits anything, doesn’t get bigger
* **O(N) = locker for everyone** → more students, more lockers

---



