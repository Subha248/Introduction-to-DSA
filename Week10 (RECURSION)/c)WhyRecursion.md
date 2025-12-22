
---

## Use of Recursion and Visualisation Using Recursion Trees

### 1. Use of Recursion (Why Recursion?)

Recursion is considered the **base of all other sections** in Data Structures and Algorithms. It plays a crucial role in solving problems that are otherwise difficult to handle using simple loops.

#### Why we use recursion:

* **Solving complex problems in a simpler way**
  Recursion allows us to solve **large and complex problems** by breaking them into **smaller, manageable sub-problems**. Problems such as **Tower of Hanoi**, **tree traversal**, **graph traversal**, and **heap operations** are naturally recursive.

* **Foundation for advanced topics**
  Without a strong understanding of recursion, it becomes extremely difficult to understand:

  * Dynamic Programming (DP)
  * Binary Search Trees
  * Linked Lists
  * Graph algorithms
    Recursion is the core idea behind all these topics.

* **Breaking down problems**
  Recursion works by dividing a problem into **smaller versions of the same problem**.
  Example:

  * Fibonacci → broken into `fibo(n-1)` and `fibo(n-2)`
  * Binary Search → search space divided into half repeatedly

* **Bridge between recursion and iteration**
  A common strategy is:

  1. Solve the problem **using recursion first** (easy to think)
  2. Convert the recursive solution into **iteration (loops)** for better optimisation
     Any recursive solution **can be converted into iteration**, and vice versa.

---

### 2. Visualising Recursion (Recursion Tree)

Understanding recursion without visualisation is difficult. Hence, **drawing recursion trees is essential**.

#### What is a Recursion Tree?

A **recursion tree** is a **visual representation** of how a recursive function makes multiple calls to itself.
Each node represents a function call, and each branch represents a new recursive call.

---

### Example: Simple Call Chain (print1 to print5)

```
print1
  |
print2
  |
print3
  |
print4
  |
print5
```

Even though this is not self-calling recursion, it helps understand **call flow and stack behaviour**.
When converted to recursion, **the same function calls itself**, forming a recursion tree.

---

### Example: Fibonacci (Core Recursion Example)

Problem: **Find the nth Fibonacci number**

Known facts (Base Condition):

* Fibonacci(0) = 0
* Fibonacci(1) = 1

#### Recurrence Relation:

```
F(n) = F(n - 1) + F(n - 2)
```

This formula is called a **recurrence relation**.

---

### Fibonacci Recursion Tree (Example: fibo(4))

```
                fibo(4)
              /          \
         fibo(3)         fibo(2)
         /     \         /     \
    fibo(2)  fibo(1)  fibo(1)  fibo(0)
     /   \
fibo(1) fibo(0)
```

---

### Understanding Execution Using the Tree

* The **entire left subtree** must finish execution before the right subtree starts.
* Base conditions (`fibo(0)` and `fibo(1)`) are the **leaf nodes**.
* Values return **bottom-up**, combining results until the final answer reaches `main()`.

This clearly shows:

* How the **stack is filled**
* How the **stack is cleared**
* How return values propagate

---

### Importance of Drawing Recursion Trees

* Helps visualise **function call order**
* Helps track **stack memory usage**
* Helps understand **why recursion is slow in some cases** (repeated calls)
* Makes it easier to convert recursion into **dynamic programming**

As stated:

> No one can truly understand recursion unless they **draw the recursion tree manually**.

---

### Analogy: Recursion Tree

Think of a recursion tree like a **company hierarchy**:

* CEO → `main()`
* Manager → `fibo(n)`
* Supervisors → `fibo(n-1)` and `fibo(n-2)`
* Workers → base conditions (`fibo(0)`, `fibo(1)`)

The CEO only gets the final report after **all workers finish and pass results upward**.

---

### Final Summary

* Recursion is essential for solving recurrent problems.
* Recurrence relations define how problems break into sub-problems.
* Base conditions stop infinite recursion.
* Recursion trees help visualise execution and stack behaviour.
* Fibonacci is a classic example of recursion using recurrence relations.
* Understanding recursion is mandatory before learning DP, trees, or graphs.

