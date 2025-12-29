### See notes
---

## **1️⃣ Space Complexity Basics**

* **Space Complexity = total memory used**

  * **Input Space** → memory for input itself
  * **Auxiliary Space** → extra memory your algorithm uses

* **Interview Tip:** Usually they mean **Auxiliary Space**

* **Common Cases:**

  * **O(1)** → constant space (few variables, like `start`, `end`, `mid`)
  * **O(n)** → new array / data structure proportional to input

🧠 Memory:

> **O(1) = tiny memory, O(n) = grows with input**

---

## **2️⃣ Sorting Algorithms & Space**

* **In-place sorts:** Bubble, Selection, Insertion → **O(1)** space
* **Time complexity:** worst-case = **O(n²)**

🧠 Memory: In-place = no extra array

---

## **3️⃣ Recursion & Space**

* Every function call → goes into **stack memory**
* **Space complexity = height of recursion tree**
* At any time → only **current path** in the stack matters

  * E.g., Fibonacci recursion tree height = `n` → **O(n)** space

🧠 Analogy: recursion tree = tall narrow staircase → you only occupy the steps you’re on

---

## **4️⃣ Types of Recurrence Relations**

1. **Linear recurrence:** reduce problem by constant

   * e.g., Fibonacci: `f(n) = f(n-1) + f(n-2)`
2. **Divide-and-conquer recurrence:** reduce by factor

   * e.g., Binary Search: `T(n) = T(n/2) + c`

---

## **5️⃣ Divide-and-Conquer Recurrence Example**

* General form: `T(n) = aT(n/b) + f(n)`

  * `a` = # of subproblems
  * `n/b` = size of each subproblem
  * `f(n)` = extra work

* **Examples:**

  * Binary Search → `T(n) = T(n/2) + O(1)` → **O(log n)**
  * Merge Sort → `T(n) = 2T(n/2) + O(n)` → **O(n log n)**

---

## **6️⃣ Akra-Bazzi Theorem**

* More powerful than Master Theorem
* Solves almost any divide-and-conquer recurrence
* Formula:

  ```
  T(x) = Θ(x^p * (1 + ∫[1,x] g(u)/u^(p+1) du))
  ```
* Solve `∑ a_i * b_i^p = 1` to find `p`

🧠 Memory: Basically a “magical tool” for hard recurrences

---

## **7️⃣ Solving Linear Recurrence (Fibonacci)**

1. **Assume:** `f(n) = α^n`
2. **Plug in → characteristic eq:**

   ```
   α^2 - α - 1 = 0
   ```
3. **Solve roots:**

   ```
   α1 = (1+√5)/2, α2 = (1-√5)/2
   ```
4. **General solution:**

   ```
   f(n) = c1*α1^n + c2*α2^n
   ```
5. **Find constants** using `f(0)=0`, `f(1)=1` → `c1 = 1/√5`, `c2 = -1/√5`

---

## **8️⃣ Fibonacci Using Golden Ratio**

* Direct formula:

  ```
  f(n) = (1/√5) * [ ((1+√5)/2)^n - ((1-√5)/2)^n ]
  ```
* **Golden Ratio φ ≈ 1.618**
* Second term → small, can ignore for **approximation**
* **Time complexity:** O(1.618^n) for recursion, O(1) if using formula

🧠 Memory: Formula = **fast AF**, recursion = slow

---

### ✅ **Quick Analogy for Recursion Space**

> Recursion tree = tall narrow staircase → only the current path matters, not all floors at once

---

### **Interview/Exam Shortcut**

* Space complexity = **extra memory used + recursion stack**
* Linear recursion → **height of tree**
* Divide-and-conquer → solve recurrence (Master / Akra-Bazzi)

---
