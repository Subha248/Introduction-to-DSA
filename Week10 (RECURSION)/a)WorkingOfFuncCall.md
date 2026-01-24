
---

## The 2 VERY IMPORTANT POINTS (Core Concept)

### 🔴 Point 1

**When a function has NOT finished executing, it remains in the stack.**
If it calls another function, it stays in the stack in a **waiting state**.

### 🔴 Point 2

**When a function FINISHES executing, it is removed from the stack, and the program flow is restored to the exact line where that function was called.**

Now I’ll explain these **only using Example B**.

---

## Example B Code (same idea, no changes)

```java

import java.util.Scanner;
public class Main{
  public static void main(String[] args){
    int n=5;
      print1(n);
  }
    static void print1(int n) {
    System.out.println(n);
    print2(2);
}

static void print2(int n) {
    System.out.println(n);
    print3(3);
}

static void print3(int n) {
    System.out.println(n);
    print4(4);
}

static void print4(int n) {
    System.out.println(n);
    print5(5);
}

static void print5(int n) {
    System.out.println(n);
}
}
```

`main()` calls `print1(1)`.

---

## FULL EXECUTION (STACK + FLOW)

### Step 1: `main()` calls `print1(1)`

```
| print1(1) |
| main()    |
```

* `print1()` prints `1`
* Calls `print2(2)`
* ❗ `print1()` is **NOT finished**, so it **remains in the stack**

✅ **Point 1 applied**

---

### Step 2: `print2(2)` starts

```
| print2(2) |
| print1(1) |
| main()    |
```

* `print2()` prints `2`
* Calls `print3(3)`
* ❗ `print2()` is also **not finished**, so it stays waiting

---

### Step 3: `print3(3)` starts

```
| print3(3) |
| print2(2) |
| print1(1) |
| main()    |
```

* Prints `3`
* Calls `print4(4)`
* Still **not finished**, stays in stack

---

### Step 4: `print4(4)` starts

```
| print4(4) |
| print3(3) |
| print2(2) |
| print1(1) |
| main()    |
```

* Prints `4`
* Calls `print5(5)`
* Still waiting

---

### Step 5: `print5(5)` starts

```
| print5(5) |
| print4(4) |
| print3(3) |
| print2(2) |
| print1(1) |
| main()    |
```

* Prints `5`
* Does **not call any other function**
* ✅ `print5()` **FINISHES execution**

---

## NOW STACK STARTS CLEARING (Point 2)

### `print5()` finishes → REMOVED

```
| print4(4) |
| print3(3) |
| print2(2) |
| print1(1) |
| main()    |
```

📌 Program flow is restored to:

```java
print5(5);  // this line in print4
```

But there’s **nothing after it**, so `print4()` finishes.

---

### `print4()` finishes → REMOVED

```
| print3(3) |
| print2(2) |
| print1(1) |
| main()    |
```

Flow restored to:

```java
print4(4);  // line in print3
```

Again, nothing left → finishes.

---

### Same thing repeats:

* `print3()` finishes → removed
* `print2()` finishes → removed
* `print1()` finishes → removed

Finally:

```
| main() |
```

Then `main()` ends → program terminates.

---

## FINAL SUMMARY (Say This in Exam / Viva)

* A function **remains in the stack until it finishes execution**.
* If it calls another function, it waits in the stack.
* When a function **finishes execution**, it is **removed from the stack**.
* The **program flow is restored exactly to the line where the function was called**.
* This continues until all functions are removed and `main()` ends.

