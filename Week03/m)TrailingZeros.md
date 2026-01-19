
### **Problem:**
Find how many zeros are at the **end** of \( N! \) (factorial of \( N \)).

- \( N! \) is the product of all numbers from 1 to \( N \).
- Trailing zeros are created by multiplying **2** and **5** (since \( 2 \times 5 = 10 \)).
- In \( N! \), there are **always more 2s than 5s**, so we only need to count the number of **5s**.

---

### **Solution:**
To count the trailing zeros:
1. Count how many multiples of **5** are in \( N! \).
2. Count how many multiples of **25** (since \( 25 = 5 \times 5 \)) are in \( N! \).
3. Count how many multiples of **125** (since \( 125 = 5 \times 5 \times 5 \)) are in \( N! \).
4. Keep going for higher powers of 5 (e.g., 625, 3125, etc.) until the power exceeds \( N \).

Finally, add up all these counts to get the total number of trailing zeros.

---

### **Example:**
Let’s say \( N = 100 \):
1. Count multiples of **5**: \( 100 / 5 = 20 \).
2. Count multiples of **25**: \( 100 / 25 = 4 \).
3. Count multiples of **125**: \( 100 / 125 = 0 \) (since 125 > 100).

Total trailing zeros = \( 20 + 4 + 0 = 24 \).

So, \( 100! \) has **24 trailing zeros**.

---

### **Program:**
Here’s the Java program to do this:

```java
class Solution {
    public int trailingZeroes(int N) {
        int count = 0; // Initialize the count of trailing zeros

        // Count factors of 5, 25, 125, ...
        for (int i = 5; i <= N; i *= 5) {
            count += N / i; // Add the number of multiples of i (current power of 5)
        }

        return count; // Return the total trailing zeros
    }
}
```

---

### **How It Works:**
1. Start with \( i = 5 \) (the smallest power of 5).
2. Divide \( N \) by \( i \) to count how many multiples of \( i \) are in \( N! \).
3. Multiply \( i \) by 5 to check the next power of 5 (e.g., 25, 125, etc.).
4. Repeat until \( i \) exceeds \( N \).
5. Add up all the counts to get the total trailing zeros.

---

### **Key Points:**
1. Trailing zeros come from **factors of 10** (\( 2 \times 5 \)).
2. There are always more **2s** than **5s**, so we only count **5s**.
3. The formula is:  
   \( \text{Trailing zeros} = N/5 + N/25 + N/125 + \dots \)

---

### **Example Table for \( N = 100 \):**

| **Power of 5** | **Calculation** | **Count Added** | **Total Trailing Zeros** |
|----------------|-----------------|-----------------|--------------------------|
| \( 5 \)        | \( 100 / 5 = 20 \) | 20              | 20                       |
| \( 25 \)       | \( 100 / 25 = 4 \) | 4               | 24                       |
| \( 125 \)      | \( 100 / 125 = 0 \) | 0               | 24                       |

**Final Answer:** \( 100! \) has **24 trailing zeros**.

---

### **Time Complexity:**
The loop runs for each power of 5, so it’s very efficient: \( O(\log_5 N) \).

---

### **Summary:**
- Count the number of **5s** in \( N! \) by dividing \( N \) by powers of 5.
- Add them up to get the total trailing zeros.
- The program does this quickly and efficiently!
