
---

# Example C – NumbersExampleRecursion.java

```java
package com.kunal;

public class NumbersExampleRecursion {
    public static void main(String[] args) {
        // print first 5 numbers: 1 2 3 4 5
        print(1);
    }

    static void print(int n) {
        // base condition
        if (n == 5) {
            System.out.println(5);
            return;
        }

        System.out.println(n);

        // recursive call
        print(n + 1);
    }
}
```

---

## What is happening in this code

This is **recursion** because the function `print()` is **calling itself** using:

```java
print(n + 1);
```

---

## Base Condition in Recursion

The **base condition** is where the function **stops making new calls**.

Here, the base condition is:

```java
if (n == 5) {
    System.out.println(5);
    return;
}
```

* This is a **simple if condition**
* It tells the recursion **when to stop**

---

## Function Calls and Memory

Every time `print()` is called:

* A **new function call** is created
* It takes **separate memory**
* A new **stack frame** is added to the stack

Example calls:

```
print(1)
print(2)
print(3)
print(4)
print(5)
```

Each of these takes **its own memory** in the stack.

---

## Stack Diagram (During Execution)

When `print(5)` is reached:

```
| print(5) |
| print(4) |
| print(3) |
| print(2) |
| print(1) |
| main()   |
```

---

## What Happens at `n == 5`

* Base condition becomes true
* `print(5)` prints `5`
* `return` executes
* Function **finishes execution**
* It is **removed from the stack**
* Program flow is restored to where it was called

Then:

* `print(4)` finishes
* `print(3)` finishes
* `print(2)` finishes
* `print(1)` finishes

Stack becomes empty and program ends.

---

## What If There Was NO Base Condition

If there was no base condition:

* `print(n + 1)` keeps calling again and again
* Stack keeps filling
* Every function call takes memory
* Memory exceeds
* **StackOverflowError occurs**

---

## Tail Recursion

This line:

```java
print(n + 1);
```

* Is the **last statement** in the function
* So this is **tail recursion**

---

## Function Body Change at `print(5)`

* For `n = 1` to `4`, function prints and calls itself
* At `n = 5`, function **does not call itself**
* Function behavior changes
* Stack starts clearing

---

## Why We Use Recursion (From This Example)

Without recursion, we would have to:

* Write multiple functions like `print1()`, `print2()`, `print3()`…
* Manually copy-paste code many times
* Which is not practical for large numbers like 100 or 1000

Recursion avoids this by:

* Using the **same function**
* Repeating execution
* Controlled by a base condition

---

