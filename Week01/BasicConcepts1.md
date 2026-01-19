
### Problem 1

Write a program that takes an integer, then a string, then a char from the user and prints them in the screen.

``` plaintext
Input:  2 Name y

Expected Output:

2

Name

y
```


``` java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);

       
        int num = scan.nextInt();
        scan.nextLine(); // Consume leftover newline character

       
        String a = scan.nextLine();

       
        char y = scan.next().charAt(0);

        
        System.out.println(num);
        System.out.println(a);
        System.out.println(y);
    }
}

```

1. **Import Scanner**: Allows user input.

2. **Create Scanner Object**:
   ```java
   Scanner scan = new Scanner(System.in);
   ```

3. **Input Reading**:
   - `scan.nextInt()` → Reads an integer and stores in `num`.
   - `scan.nextLine()` → Clears leftover newline from `nextInt()`.
   - `scan.nextLine()` → Reads a full line of text into `a`.
   - `scan.next().charAt(0)` → Reads a single character into `y`.

4. **Output**:
   Prints `num`, `a`, and `y`.

---

### Example:

#### Input:
```
5
Hello
T
```

#### Output:
```
5
Hello
T
```

### Prob 2: Write a program to check whether a triangle can be formed with the given values for the angles.
``` plaintext
If sum of angles is equal to 180, then triangle can be formed, else it can't be formed.

Input: 45 45 45

Expected Output: 

Triangle cannot be formed

Explanation -> We are getting 3 inputs, that is three angles of triangle, but here the sum of three angles that is 45+45+45 is not equal to 180 so Triangle cannot be formed is the output
```

Here’s the program to check whether a triangle can be formed based on the given angles:

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int angle1 = scan.nextInt();
        int angle2 = scan.nextInt();
        int angle3 = scan.nextInt();

        if (angle1 + angle2 + angle3 == 180) {
            System.out.println("Triangle can be formed");
        } else {
            System.out.println("Triangle cannot be formed");
        }
    }
}
```

---

### Explanation:

1. **Input**:
   - The program takes three integers as input (angles of a triangle).

2. **Condition**:
   - It checks whether the sum of the three angles is equal to `180`.

3. **Output**:
   - If the sum is `180`, the program prints `"Triangle can be formed"`.
   - Otherwise, it prints `"Triangle cannot be formed"`.

---

### Input/Output Example:

#### Input:
```
45 45 45
```

#### Output:
```
Triangle cannot be formed
```

---

#### Input:
```
60 60 60
```

#### Output:
```
Triangle can be formed
```
### Prob 3: 
```plainnext
Given mark of student, Print the Grade

Grade A if mark is greater than or equal to 90

Grade B if mark is greater than or equal to 80

Grade C if mark if greater than or equal to 60

Grade D if mark if greaer than or equal to 35

Fail if mark is lesser than 35

Input: 95

Expected Output:

Grade A

Explanation: Here 95 is greater than or equal to 90 so its Grade A

```
Here’s the program to calculate and print the grade based on the student’s mark:

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int mark = scan.nextInt();

        if (mark >= 90) {
            System.out.println("Grade A");
        } else if (mark >= 80) {
            System.out.println("Grade B");
        } else if (mark >= 60) {
            System.out.println("Grade C");
        } else if (mark >= 35) {
            System.out.println("Grade D");
        } else {
            System.out.println("Fail");
        }
    }
}
```

---

### Explanation:

1. **Input**:
   - The program takes an integer input (`mark`) from the user.

2. **Conditions**:
   - Checks the range of the mark and assigns a grade based on the specified criteria:
     - `mark >= 90` → Grade A
     - `mark >= 80` → Grade B
     - `mark >= 60` → Grade C
     - `mark >= 35` → Grade D
     - `mark < 35` → Fail

3. **Output**:
   - Prints the corresponding grade.

---

### Input/Output Examples:

#### Input:
```
95
```

#### Output:
```
Grade A
```

---

#### Input:
```
75
```

#### Output:
```
Grade C
```

---

#### Input:
```
30
```

#### Output:
```
Fail
```

### Prob 4 
```plaintext
Prob 4: Write a program using switch case which takes a value and prints the respective Size.
If size is 29 then its small

If size is 30 then its Medium

If size is 38 then its Large

If size is 42 then its XLarge

If size is not any of the above then Invalid.



Input: 29

Expected Output: 

Small
```
Here’s the program using `switch-case` to print the respective size:

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int size = scan.nextInt();

        switch (size) {
            case 29:
                System.out.println("Small");
                break;
            case 30:
                System.out.println("Medium");
                break;
            case 38:
                System.out.println("Large");
                break;
            case 42:
                System.out.println("XLarge");
                break;
            default:
                System.out.println("Invalid");
                break;
        }
    }
}
```

---

### Explanation:

1. **Input**:
   - The program takes an integer input (`size`).

2. **Switch-Case**:
   - Matches the input `size` with predefined cases:
     - `29` → Small
     - `30` → Medium
     - `38` → Large
     - `42` → XLarge
   - If no match is found, the `default` case is executed, printing `"Invalid"`.

3. **Output**:
   - Prints the corresponding size based on the input.

---

### Input/Output Examples:

#### Input:
```
29
```

#### Output:
```
Small
```

---

#### Input:
```
42
```

#### Output:
```
XLarge
```

---

#### Input:
```
35
```

#### Output:
```
Invalid
```

