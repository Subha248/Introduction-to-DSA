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


Do you want me to do that?
