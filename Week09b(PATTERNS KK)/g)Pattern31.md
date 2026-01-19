---

## **Pattern31 — Concentric Number Square**

**Output for `n = 4`:**

```
0 0 0 0 0 0 0 0 0 
0 1 1 1 1 1 1 1 0 
0 1 2 2 2 2 2 1 0 
0 1 2 3 3 3 2 1 0 
0 1 2 3 4 3 2 1 0 
0 1 2 3 3 3 2 1 0 
0 1 2 2 2 2 2 1 0 
0 1 1 1 1 1 1 1 0 
0 0 0 0 0 0 0 0 0 
```

---

## **Code**

```java
public class Pattern30 {
    public static void main(String[] args) {
        pattern31(4);
    }

    public static void pattern31(int n) {
        int N = 2 * n;  // grid size
        for (int i = 0; i <= N; i++) {               // row loop
            for (int j = 0; j <= N; j++) {           // column loop
                // find layer by minimum distance from any edge
                int index = Math.min(Math.min(i, j), Math.min(N - i, N - j));
                System.out.print(index + " ");
            }
            System.out.println();
        }
    }
}
```

---

## **Step-by-Step Explanation**

### **1️⃣ Grid and Loops**

```java
int N = 2 * n;
for (int i = 0; i <= N; i++)
for (int j = 0; j <= N; j++)
```

* Creates a **square grid** of `(2*n + 1) × (2*n + 1)`
* Each `(i,j)` is a **cell** in the grid

---

### **2️⃣ Complicated Line: Layer Calculation**

```java
int index = Math.min(Math.min(i, j), Math.min(N - i, N - j));
```

* **i** → distance from **top row**
* **j** → distance from **left column**
* **N - i** → distance from **bottom row**
* **N - j** → distance from **right column**

**Take minimum** → closest edge → determines which **“layer”** the cell belongs to

> Outer cells → layer `0`, next inside → `1`, … center → `n`

---

### **3️⃣ Printing**

```java
System.out.print(index + " ");
```

* Prints **layer number** with space for readability

```java
System.out.println();
```

* Moves to next row after finishing one line

---

### **4️⃣ How the Pattern Forms**

* Each layer number **decreases as you go outward**
* Center of the square is the **largest number = n**
* Outer boundary = **0**

---

### **5️⃣ Dry Run / Layer Example (n = 4, N = 8)**

| i\j | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| --- | - | - | - | - | - | - | - | - | - |
| 0   | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 1   | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 0 |
| 2   | 0 | 1 | 2 | 2 | 2 | 2 | 2 | 1 | 0 |
| 3   | 0 | 1 | 2 | 3 | 3 | 3 | 2 | 1 | 0 |
| 4   | 0 | 1 | 2 | 3 | 4 | 3 | 2 | 1 | 0 |
| 5   | 0 | 1 | 2 | 3 | 3 | 3 | 2 | 1 | 0 |
| 6   | 0 | 1 | 2 | 2 | 2 | 2 | 2 | 1 | 0 |
| 7   | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 0 |
| 8   | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

* Shows **concentric square layers** clearly

---

✅ **Professional Takeaway**

* Uses **single formula** for layers → avoids nested logic
* Works for **any n** → fully scalable
* Outer layer = 0, innermost layer = n
* Perfect for **interview/exam patterns**

---

---

## **QUESTION**

Print a **concentric square number pattern** for a given `n`, where:

* The **outermost layer** has value `n`
* The values **decrease by 1** as we move inward
* The **center** has value `1`

For `n = 4`, the pattern size should be `(2n + 1) × (2n + 1)`.

---

## **OUTPUT (n = 4)**

```
4 4 4 4 4 4 4 4 4 
4 3 3 3 3 3 3 3 4 
4 3 2 2 2 2 2 3 4 
4 3 2 1 1 1 2 3 4 
4 3 2 1 0 1 2 3 4 
4 3 2 1 1 1 2 3 4 
4 3 2 2 2 2 2 3 4 
4 3 3 3 3 3 3 3 4 
4 4 4 4 4 4 4 4 4 
```

🔥 Symmetric. Clean. Interview-gold.

---

## **CODE**

```java
public class Pattern30 {
    public static void main(String[] args){
        pattern31(4);
    }

    public static void pattern31(int n){
        int N = 2 * n;
        int originalN = n;

        for(int i = 0; i <= N; i++){
            for(int j = 0; j <= N; j++){
                int index = originalN
                          - Math.min(Math.min(i, j),
                                     Math.min(N - i, N - j));
                System.out.print(index + " ");
            }
            System.out.println();
        }
    }
}
```

---

## **EXPLANATION (Professional & Simple)**

### **1️⃣ Grid Size Logic**

```java
int N = 2 * n;
```

* Total rows = `2n + 1`
* Total columns = `2n + 1`
* For `n = 4` → **9 × 9 grid**

---

### **2️⃣ Distance From Borders (Key Idea)**

For every cell `(i, j)`, we calculate distance from:

* **Top** → `i`
* **Left** → `j`
* **Bottom** → `N - i`
* **Right** → `N - j`

Closest edge decides the **layer**.

---

### **3️⃣ The “Scary” Line (Explained Like a Human)**

```java
Math.min(Math.min(i, j), Math.min(N - i, N - j))
```

➡ Finds the **minimum distance from any side**

* Outer border → distance `0`
* Next inner layer → `1`
* Keeps increasing as we go inside

---

### **4️⃣ Why We Subtract From `originalN`**

```java
int index = originalN - minDistance;
```

* Outer layer → `n - 0 = n`
* Next layer → `n - 1`
* Center → smallest value

This flips the pattern from:

```
0 → n
```

to

```
n → 0
```

✨ That’s how the big number stays outside.

---

## **DRY RUN (Sample Cells)**

| i | j | min distance | index = 4 - min |
| - | - | ------------ | --------------- |
| 0 | 0 | 0            | 4               |
| 1 | 1 | 1            | 3               |
| 2 | 2 | 2            | 2               |
| 3 | 3 | 3            | 1               |
| 4 | 4 | 4            | 0               |

Boom 💥 perfect symmetry.

---

## **FINAL TAKE**

* ✔ Uses **one formula** for all layers
* ✔ No hardcoding
* ✔ Works for **any n**
* ✔ Classic **concentric square pattern**

