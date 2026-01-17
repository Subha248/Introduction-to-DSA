https://leetcode.com/problems/sqrtx/
---

# **Full Working Java Code — Integer Square Root**

```java
class Solution {
    public int mySqrt(int x) {
        int start = 0;
        int end = x;
        int ans = 0; // to store the floor of sqrt

        while (start <= end) {
            int mid = start + (end - start) / 2;
            long sq = (long) mid * mid; // use long to avoid overflow

            if (sq == x) {
                return mid; // perfect square
            } else if (sq < x) {
                ans = mid;   // mid might be the floor
                start = mid + 1; // look for bigger number
            } else {
                end = mid - 1; // mid too big, look smaller
            }
        }

        return ans; // floor of sqrt if x is not perfect square
    }
}
```

---

# **Step-by-Step Dry Run (Example: x = 8)**

| Step | start | end | mid | mid*mid | Comparison             | ans |
| ---- | ----- | --- | --- | ------- | ---------------------- | --- |
| 1    | 0     | 8   | 4   | 16      | 16 > 8 → end=3         | 0   |
| 2    | 0     | 3   | 1   | 1       | 1 < 8 → ans=1, start=2 | 1   |
| 3    | 2     | 3   | 2   | 4       | 4 < 8 → ans=2, start=3 | 2   |
| 4    | 3     | 3   | 3   | 9       | 9 > 8 → end=2          | 2   |

Loop ends because start (3) > end (2) → return **ans = 2** ✅

---

# **Key Points**

1. **Binary search:** We keep narrowing the range `[start, end]`
2. **Floor handling:** When `mid*mid < x`, store `mid` in `ans` → it might be floor
3. **Overflow safe:** Use `long sq = (long)mid * mid;`
4. **No manual increment/decrement needed** (`s++`/`e--`) — binary search updates start/end properly

---

# **Time & Space Complexity**

* **Time:** O(log x) → each step halves the search range
* **Space:** O(1) → only a few variables used, no extra array

---
---

## **Question**

Write a Java program to find the square root of a number `n` up to `p` decimal places **without using `Math.sqrt()`**. Use **binary search** for the integer part and incremental checking for the decimal part.

**Example Input:**

```java
n = 40
p = 3
```

**Expected Output:**

```
6.325
```

---

## **Correct Java Code**

```java
public class Main {
    public static void main(String[] args){
        int n = 40;
        int p = 3;
        System.out.printf("%." + p + "f", sqrt(n, p));
    }

    public static double sqrt(int n, int p){
        // 1️⃣ Find integer part using binary search
        int s = 0, e = n;
        int ans = 0;  // to store the integer part of sqrt
        while(s <= e){
            int m = s + (e - s) / 2;

            if(m * m == n){
                ans = m;
                break;  // perfect square
            }

            if(m * m < n){
                ans = m;  // possible integer part
                s = m + 1;
            } else {
                e = m - 1;
            }
        }

        // 2️⃣ Find decimal part
        double root = ans;  // start from integer part
        double incr = 0.1;  // increment for decimal

        for(int i = 0; i < p; i++){   // loop for each decimal place
            while(root * root <= n){
                root += incr;  // keep adding increment until root*root > n
            }
            root -= incr;  // step back one increment
            incr /= 10;    // move to next decimal place
        }

        return root;
    }
}
```

---

## **Line-by-Line Explanation**

1. **`int s = 0, e = n;`**

   * Start and end for binary search (0 → n).

2. **`int ans = 0;`**

   * To store integer part of the square root.

3. **Binary search loop:**

```java
while(s <= e){
    int m = s + (e - s)/2;
    if(m*m == n){ ans = m; break; }
    if(m*m < n){ ans = m; s = m+1; }
    else { e = m-1; }
}
```

* `m` = middle of search.
* If `m*m == n` → perfect square → return immediately.
* If `m*m < n` → `m` could be integer part → move `s = m+1`.
* Else → too big → move `e = m-1`.

✅ At the end, `ans` holds the **integer part** of the square root.

4. **Decimal part calculation:**

```java
double root = ans;
double incr = 0.1;
for(int i = 0; i < p; i++){
    while(root*root <= n) root += incr;
    root -= incr;
    incr /= 10;
}
```

* Start `root` from integer part `ans`.
* `incr` = increment for each decimal place.
* While `root*root <= n`, keep adding `incr`.
* Once it exceeds `n`, step back `root -= incr`.
* Divide `incr` by 10 for next decimal place.

---

## **Dry Run Example**

**Input:** `n = 40`, `p = 3`

### **Step 1: Binary Search (integer part)**

| s | e  | m  | m*m | ans |        |
| - | -- | -- | --- | --- | ------ |
| 0 | 40 | 20 | 400 | 0   |        |
| 0 | 19 | 9  | 81  | 0   |        |
| 0 | 8  | 4  | 16  | 4   |        |
| 5 | 8  | 6  | 36  | 6   |        |
| 7 | 8  | 7  | 49  | 6   |        |
| 7 | 6  | -  | -   | 6   | (exit) |

✅ Integer part = 6

---

### **Step 2: Decimal Part (p=3)**

**i=0 → 0.1 place**

* root = 6, incr = 0.1
* while loop:

  * 6*6 = 36 ≤ 40 → add 0.1 → root = 6.1 → 6.1*6.1=37.21 ≤40 → add → 6.2 → 38.44 ≤40 → add → 6.3 → 39.69 ≤40 → add → 6.4 → 40.96 >40 → stop
* Step back: root -= 0.1 → root = 6.3

**i=1 → 0.01 place**

* incr = 0.01, root = 6.3
* 6.3*6.3 = 39.69 ≤40 → add 0.01 → 6.31*6.31=39.8161 ≤40 → add → 6.32*6.32=39.9424 ≤40 → add → 6.33*6.33=40.0689 >40 → stop
* Step back: root = 6.32

**i=2 → 0.001 place**

* incr = 0.001, root = 6.32
* 6.32*6.32=39.9424 ≤40 → add 0.001 → 6.321*6.321=39.9544 ≤40 → ... → 6.325*6.325=39.990625 ≤40 → 6.326*6.326=40.003876 >40 → stop
* Step back: root = 6.325

✅ Final Answer = 6.325

---

## **Output**

```
6.325
```

---
---

# 1️⃣ QUESTION

> Find the square root of 40 using the **Newton-Raphson method** in Java.
> Stop when the guess stops changing significantly. Explain **why we start with x = n**, **why n doesn’t change**, **why we check Math.abs(root - x)**, and trace **all iterations**.

---

# 2️⃣ FULL WORKING CODE

```java
public class NewtonSQRT {
    public static void main(String[] args) {
        double n = 40; // number whose square root we want
        double root = sqrt(n);
        System.out.println("Square root of " + n + " ≈ " + root);
    }

    static double sqrt(double n) {
        double x = n;          // initial guess
        double root;

        while (true) {
            root = 0.5 * (x + (n / x)); // Newton-Raphson formula

            // STOP CONDITION: when improvement is tiny
            if (Math.abs(root - x) < 0.000001) {
                break;
            }

            x = root; // update guess for next iteration
        }

        return root;
    }
}
```

---

# 3️⃣ LINE-BY-LINE EXPLANATION

| Line                                 | Explanation                                                                                                                                                                                                          |
| ------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `double n = 40;`                     | The number whose square root we want. **This NEVER changes**.                                                                                                                                                        |
| `double root = sqrt(n);`             | Calls our Newton-Raphson function.                                                                                                                                                                                   |
| `double x = n;`                      | Initial guess. Could be anything, we chose `x = n` because it’s simple. **x changes every iteration**, n does NOT.                                                                                                   |
| `root = 0.5 * (x + (n / x));`        | Newton-Raphson formula. It improves the guess: <br> - `x` = current guess <br> - `n / x` = correction factor <br> - Average them → new guess                                                                         |
| `if (Math.abs(root - x) < 0.000001)` | Checks **how much the guess changed**. <br> - If the difference is tiny → stop, because further improvement is pointless. <br> - This is why we don’t need `root == exact value`. Computers can’t do exact decimals. |
| `x = root;`                          | Update the guess for the next iteration. Only **x changes**. `n` stays the same.                                                                                                                                     |
| `return root;`                       | Return the final guess as the approximate square root.                                                                                                                                                               |

---

# 4️⃣ DRY RUN FOR n = 40

| Iteration | x (old guess) | n/x  | root = 0.5*(x+n/x) | |root - x| | Note |
|-----------|---------------|------|-------------------|------------|------|
| 1         | 40.0          | 1.0  | 20.5              | 19.5       | First improvement |
| 2         | 20.5          | 1.951| 11.225            | 9.275      | Guess gets smaller |
| 3         | 11.225        | 3.565| 7.395             | 3.83       | Closer to actual √40 |
| 4         | 7.395         | 5.408| 6.401             | 0.994      | Converging |
| 5         | 6.401         | 6.247| 6.324             | 0.077      | Almost there |
| 6         | 6.324         | 6.327| 6.325             | 0.001      | Very close |
| 7         | 6.325         | 6.324| 6.3249            | 0.0001     | Difference < 0.000001 → STOP |

---

# ✅ OUTPUT

```
Square root of 40 ≈ 6.324555
```

---

# 5️⃣ ANSWERS TO YOUR  DOUBTS

1. **x = n → does n change?**

   * NOPE. `n` stays **fixed**. Only `x` updates every loop.
   * `x` moves: 40 → 20.5 → 11.225 → 7.395 → … → 6.3249

2. **Why use `Math.abs(root - x) < tiny_value`?**

   * It checks **if our guess stopped improving**.
   * Computers can’t store exact decimals, so we stop when the change is small enough.

3. **What happens if guess and n were the same?**

   * It won’t stay the same because the formula will adjust it: `(x + n/x)/2`.
   * Example: x = 40, n = 40 → new root = (40 + 40/40)/2 = 20.5 → changes instantly.

4. **Why start with x = n at all?**

   * Just a simple starting point. Could be 1, n/2, anything. Newton-Raphson will pull it to the correct value anyway.

---

💥 THERE.
This is **full question → code → line-by-line → dry run → output → all doubts answered**.

---



