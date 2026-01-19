### Prob 1:
```plaintext
Write a program which takes two values x and y. Prints x for y number of times.

Input:

2 

3

Expected Output

2

2

2

Explanation - 2 is x and 3 is y in the input. So 2 is printed 3 times on the output.
```

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int x = scan.nextInt();
        int y = scan.nextInt();

        for (int i = 0; i < y; i++) {
            System.out.println(x);
        }
    }
}
```

---

### Explanation:

1. **Input**:
   - The program takes two integers as input:
     - `x`: The value to be printed.
     - `y`: The number of times `x` should be printed.

2. **For Loop**:
   - The loop runs from `i = 0` to `i < y` (a total of `y` iterations).
   - During each iteration, it prints the value of `x`.

3. **Output**:
   - Prints `x` on a new line for each iteration.

---

### Input/Output Example:

#### Input:
```
2
3
```

#### Output:
```
2
2
2
```

#### Input:
```
5
4
```

#### Output:
```
5
5
5
5
```
### Prob 2:

Write a program to take x and print multiples of x till 1000.

Input:

100

Expected Output:

100

200

300

400

500

600

700

800

900

1000

Explanation - Input is 100, multiples of 100 is 100*1, 100*2, 100*3 and so on till 1000.
Here’s the program to solve **Prob 2**:

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int x = scan.nextInt();

        for (int i = 1; i * x <= 1000; i++) {
            System.out.println(i * x);
        }
    }
}
```

---

### Explanation:

1. **Input**:
   - The program takes an integer `x` as input (e.g., `100`).

2. **For Loop**:
   - The loop starts with `i = 1`.
   - The condition `i * x <= 1000` ensures the loop runs as long as the multiples of `x` are less than or equal to 1000.
   - Each iteration prints `i * x`.

3. **Output**:
   - Prints all multiples of `x` from `x` to `1000`.

---

### Input/Output Example:

#### Input:
```
100
```

#### Output:
```
100
200
300
400
500
600
700
800
900
1000
```

---

#### Input:
```
250
```

#### Output:
```
250
500
750
1000
```
###Prob 3:

Write a program to get firstName and lastName and n as input and print fullName that is firstName+lastName for n times.

Input

Nandy

Raja

5

Expected output:

NandyRaja

NandyRaja

NandyRaja

NandyRaja

NandyRaja

Explanation - Nandy is the firstName, Raja is the lastName and n is 5, so the expected output has NandyRaja printed 5 times.

Here’s the program to solve **Prob 3**:

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        String firstName = scan.nextLine();
        String lastName = scan.nextLine();
        int n = scan.nextInt();

        for (int i = 0; i < n; i++) {
            System.out.println(firstName + lastName);
        }
    }
}
```

---

### Explanation:

1. **Input**:
   - The program takes three inputs:
     - `firstName`: A string (e.g., "Nandy").
     - `lastName`: A string (e.g., "Raja").
     - `n`: An integer indicating how many times to print the full name.

2. **For Loop**:
   - The loop runs `n` times.
   - Each iteration concatenates `firstName` and `lastName` and prints the result.

3. **Output**:
   - Prints `firstName + lastName` on a new line for each iteration.

---

### Input/Output Example:

#### Input:
```
Nandy
Raja
5
```

#### Output:
```
NandyRaja
NandyRaja
NandyRaja
NandyRaja
NandyRaja
```

