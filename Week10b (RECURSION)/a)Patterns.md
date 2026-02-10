
---

# Q1: Triangle 1 (Inverted Triangle using Recursion)

## 🔑 MAIN APPROACH (THIS IS THE KEY)

**Convert nested loops → recursion by treating parameters as loop variables.**

That’s the approach. Period.

If you remember only ONE line for life, remember this 👇
👉 **“In recursion, function parameters act like loop counters.”**

* `r` → row loop
* `c` → column loop

---

## 🧠 First, think of the LOOP version (important)

Interviewers love this thinking.

```java
for (int r = n; r > 0; r--) {
    for (int c = 0; c < r; c++) {
        System.out.print("*");
    }
    System.out.println();
}
```

Now we **remove loops** and **replace them with recursion**.

---

## 🔁 How we convert loops → recursion

| Loop Concept     | Recursive Version    |
| ---------------- | -------------------- |
| outer loop (`r`) | parameter `r`        |
| inner loop (`c`) | parameter `c`        |
| increment `c++`  | `triangle(r, c + 1)` |
| move to next row | `triangle(r - 1, 0)` |
| loop end         | base case (`r == 0`) |

---

## ✅ FULL CODE (WITH `main` FUNCTION)

```java
public class Main {
    public static void main(String[] args) {
        int n = 4;
        triangle(n, 0);
    }

    static void triangle(int r, int c) {
        // Base case: no rows left
        if (r == 0) {
            return;
        }

        // Inner loop work (printing stars)
        if (c < r) {
            System.out.print("*");
            triangle(r, c + 1);   // move to next column
        } 
        // Outer loop work (move to next row)
        else {
            System.out.println(); // move to next line
            triangle(r - 1, 0);   // move to next row
        }
    }
}
```

---

## 🧩 LINE-BY-LINE EXPLANATION (SIMPLE + INTERVIEW SAFE)

```java
if (r == 0) {
    return;
}
```

🛑 **Base Case**
No rows left → stop recursion
(Same as loop condition failing)

---

```java
if (c < r) {
```

👉 Means:
“I am still inside the current row”

Equivalent to:

```java
for (c = 0; c < r; c++)
```

---

```java
System.out.print("*");
```

⭐ Print one star
(Work of the inner loop)

---

```java
triangle(r, c + 1);
```

➡️ Move **horizontally** to next column

---

```java
else {
    System.out.println();
    triangle(r - 1, 0);
}
```

Row finished ✅

* Print new line
* Move **vertically** to next row
* Reset column back to `0`

---

# 🔁 FULL DRY RUN (NO SKIPPING, REAL EXECUTION)

### Initial call

```java
triangle(4, 0)
```

---

## 🔹 Row 1 (`r = 4`)

```
triangle(4,0) → c < r → print *
triangle(4,1) → c < r → print *
triangle(4,2) → c < r → print *
triangle(4,3) → c < r → print *
triangle(4,4) → c == r
```

Output so far:

```
****
```

Now:

```
newline
triangle(3,0)
```

---

## 🔹 Row 2 (`r = 3`)

```
triangle(3,0) → print *
triangle(3,1) → print *
triangle(3,2) → print *
triangle(3,3) → c == r
```

Output:

```
****
***
```

Call:

```
triangle(2,0)
```

---

## 🔹 Row 3 (`r = 2`)

```
triangle(2,0) → print *
triangle(2,1) → print *
triangle(2,2) → c == r
```

Output:

```
****
***
**
```

Call:

```
triangle(1,0)
```

---

## 🔹 Row 4 (`r = 1`)

```
triangle(1,0) → print *
triangle(1,1) → c == r
```

Output:

```
****
***
**
*
```

Call:

```
triangle(0,0)
```

---

## 🔹 Base Case Hit

```
triangle(0,0) → r == 0 → return
```

Recursion ends 🛑

---

## 🎯 FINAL OUTPUT

```
****
***
**
*
```

---

## 🧠 HOW TO THINK WHILE DRY RUNNING

* Finish **one full row** first (horizontal)
* Then move to **next row** (vertical)
* Reduce `r`
* Stop when `r == 0`

Exactly like nested loops.

---

## 🔥 WHY THIS APPROACH IS IMPORTANT (INTERVIEW POV)

Say this confidently 👇

> “I convert nested loops into recursion by treating parameters as loop variables.
> One parameter controls rows, the other controls columns.
> The base case replaces loop termination.”

That’s an **instant green flag** answer 🟢

---

## 🧠 BIG TAKEAWAYS (SAVE THIS)

* Recursion ≠ scary
* It’s just **loops rewritten**
* Parameters = loop counters
* Base case = loop exit
* Same logic works for:

  * Patterns
  * Bubble Sort
  * Selection Sort
  * Grid / matrix problems

---

