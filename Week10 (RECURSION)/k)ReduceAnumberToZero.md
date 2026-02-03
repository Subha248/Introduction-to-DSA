https://leetcode.com/problems/number-of-steps-to-reduce-a-number-to-zero/

This is a **recursion problem** called:

## 🧠 **Question: Number of Steps to Reduce a Number to Zero**

You are given a number `num`.

You must keep doing this until it becomes **0**:

* If the number is **even** → divide it by 2
* If the number is **odd** → subtract 1

Return **how many steps** it took.

---

### ✨ Example

Input: `num = 14`

Steps:

| Step | Number | Operation         |
| ---- | ------ | ----------------- |
| 1    | 14     | even → 14 / 2 = 7 |
| 2    | 7      | odd → 7 - 1 = 6   |
| 3    | 6      | even → 6 / 2 = 3  |
| 4    | 3      | odd → 3 - 1 = 2   |
| 5    | 2      | even → 2 / 2 = 1  |
| 6    | 1      | odd → 1 - 1 = 0   |

✅ Output = **6 steps**

---

## 🧩 What Your Code is Trying to Do

You're using **recursion** and passing the step count along each time.

But Java does **NOT** allow named parameters like
`helper(num: num/2, steps: steps+1)` ❌

Also you forgot an `else` and have two returns inside one block.

Let’s fix it.

---

## ✅ Correct Code

```java
public int numberOfSteps(int num) {
    return helper(num, 0);
}

private int helper(int num, int steps) {
    // Base case: when number becomes 0, return total steps
    if (num == 0) {
        return steps;
    }

    // If number is even
    if (num % 2 == 0) {
        return helper(num / 2, steps + 1);
    } 
    // If number is odd
    else {
        return helper(num - 1, steps + 1);
    }
}
```

---

## 🔄 How Recursion is Working (Flow)

Let’s trace for **num = 14**

```
helper(14, 0)  → even → helper(7, 1)
helper(7, 1)   → odd  → helper(6, 2)
helper(6, 2)   → even → helper(3, 3)
helper(3, 3)   → odd  → helper(2, 4)
helper(2, 4)   → even → helper(1, 5)
helper(1, 5)   → odd  → helper(0, 6)
helper(0, 6)   → base case → return 6
```

Each function call waits for the next one to finish.
When `num` becomes 0, recursion stops and returns **6** back through all calls.

---

## 🎯 Key Concepts You Should Remember

✔ **Base Case** → Stops recursion (`num == 0`)
✔ **State Passing** → `steps` keeps count
✔ **Even Check** → `num % 2 == 0`
✔ **Odd Case** → subtract 1

---

## ⏱ Time Complexity

Each step reduces the number quickly (especially when dividing).
So complexity is about **O(log n)**.

---

If you want, I can also show **how the call stack looks visually** (like boxes).
