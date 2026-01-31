
Your code:

```java
public static void fun(int n){
    if(n==0) return;
    fun(n-1);
    System.out.println(n);
}
```

You call:

```java
fun(5);
```

---

# 🧠 Big Idea First

There are **two phases in recursion**:

| Phase         | What happens                               |
| ------------- | ------------------------------------------ |
| ⬇️ Going DOWN | Function keeps calling smaller values      |
| ⬆️ Coming UP  | Calls finish and lines after recursion run |

👉 Your `System.out.println(n);` is **after** the recursive call
So printing happens **while coming back up the stack**, not while going down.

---

# ⬇️ PHASE 1 — STACK BUILDING (Going Down)

We haven’t printed anything yet.

### Call 1

`fun(5)`
Stack:

```
fun(5)
```

Calls `fun(4)`

---

### Call 2

`fun(4)`
Stack:

```
fun(4)
fun(5)
```

Calls `fun(3)`

---

### Call 3

`fun(3)`
Stack:

```
fun(3)
fun(4)
fun(5)
```

Calls `fun(2)`

---

### Call 4

`fun(2)`
Stack:

```
fun(2)
fun(3)
fun(4)
fun(5)
```

Calls `fun(1)`

---

### Call 5

`fun(1)`
Stack:

```
fun(1)
fun(2)
fun(3)
fun(4)
fun(5)
```

Calls `fun(0)`

---

### Call 6 — BASE CASE 🛑

`fun(0)`
Stack:

```
fun(0)
fun(1)
fun(2)
fun(3)
fun(4)
fun(5)
```

Now:

```java
if(n==0) return;
```

So **fun(0) ends immediately**.
Now stack starts **unwinding**.

---

# ⬆️ PHASE 2 — STACK UNWINDING (Coming Up)

Now each function resumes **after** its `fun(n-1)` call.

---

### Returning to `fun(1)`

Stack becomes:

```
fun(1)
fun(2)
fun(3)
fun(4)
fun(5)
```

Now it runs:

```java
System.out.println(1);
```

🖨 Prints **1**

Then `fun(1)` ends.

---

### Returning to `fun(2)`

Stack:

```
fun(2)
fun(3)
fun(4)
fun(5)
```

Prints **2**
Ends.

---

### Returning to `fun(3)`

Stack:

```
fun(3)
fun(4)
fun(5)
```

Prints **3**
Ends.

---

### Returning to `fun(4)`

Stack:

```
fun(4)
fun(5)
```

Prints **4**
Ends.

---

### Returning to `fun(5)`

Stack:

```
fun(5)
```

Prints **5**
Ends.

---

# ✅ Final Output

```
1
2
3
4
5
```

---

# 🔥 Why order changed?

Because:

```java
fun(n-1);   // go deeper first
print(n);   // print while coming back
```

So printing happens **after all smaller numbers finish**.

---

# 🧩 Visual Trick to Remember

Think of recursion like going down stairs and coming back up:

```
fun(5) → fun(4) → fun(3) → fun(2) → fun(1) → fun(0) 🛑
                                            ⬆️ print 1
                                  ⬆️ print 2
                        ⬆️ print 3
              ⬆️ print 4
    ⬆️ print 5
```

Down = calls
Up = prints

---

# 💡 Rule You Just Learned

| Code Position         | When it runs     |
| --------------------- | ---------------- |
| Before recursive call | While going DOWN |
| After recursive call  | While coming UP  |


----------
This prints numbers **while going down** *and* **while coming back up** the stack.

Your code:

```java
public static void funst(int n){
    if(n==0) return;

    System.out.println(n);  // (1) BEFORE recursion
    funst(n-1);             // (2) recursive call
    System.out.println(n);  // (3) AFTER recursion
}
```

You call:

```java
funst(5);
```

---

# 🧠 Two Print Zones

| Line                | When it runs          | Phase         |
| ------------------- | --------------------- | ------------- |
| First `println(n)`  | Before recursive call | ⬇️ Going DOWN |
| Second `println(n)` | After recursive call  | ⬆️ Coming UP  |

So every number prints **twice**:

* Once on the way down
* Once on the way up

---

# ⬇️ GOING DOWN (Stack Building)

| Call     | Prints |
| -------- | ------ |
| funst(5) | 5      |
| funst(4) | 4      |
| funst(3) | 3      |
| funst(2) | 2      |
| funst(1) | 1      |
| funst(0) | stops  |

So far output is:

```
5
4
3
2
1
```

No second prints yet — they are waiting.

---

# ⬆️ COMING BACK UP (Stack Unwinding)

Now each paused function resumes **after** the recursive call.

| Returning To | Prints |
| ------------ | ------ |
| funst(1)     | 1      |
| funst(2)     | 2      |
| funst(3)     | 3      |
| funst(4)     | 4      |
| funst(5)     | 5      |

---

# 🖨 FINAL OUTPUT

```
5
4
3
2
1
1
2
3
4
5
```

---

# 🎯 Visual Staircase

Think of it like shouting numbers while going down stairs and again while climbing back up:

```
Going down:   5 4 3 2 1
Coming up:    1 2 3 4 5
```

---

# 🔥 Golden Recursion Insight

If a statement is:

* **Before** recursive call → runs while going DOWN
* **After** recursive call → runs while coming UP

You just unlocked one of the most important recursion patterns used in:
✔ Tree traversals
✔ Backtracking
✔ Divide & conquer


