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


