
---

```java
// 🌸 Java Program: Function with Parameter and Return Type (String Function)
// Demonstrates how to pass a parameter to a method and return a String value.

import java.util.*;

public class Demo {

    public static void main(String[] args) {
        // Calling the method and storing the returned value
        String msg = greet("Subha");
        
        // Printing the returned message
        System.out.print(msg);
    }

    // Method with parameter and return type
    // Takes a String parameter 'name' and returns it
    public static String greet(String name) {
        String r = name; // store the input in variable r
        return r;        // return the value of r
    }
}
```

---


---

```java
import java.util.Scanner;

public class Demo {

    public static void main(String[] args) {
        // Create Scanner object for user input
        Scanner scan = new Scanner(System.in);

        // Take name as input from the user
        System.out.print("Enter your name: ");
        String name = scan.next();

        // Call the greet() method and store the returned value
        String msg = greet(name);

        // Display the returned message
        System.out.print(msg);
    }

    // Method Definition
    // Takes a String parameter 'name' and returns a greeting message
    public static String greet(String name) {
        String r = "Yoo " + name + "!";
        return r;
    }
}

/*
🧠 Sample Output:
-----------------
Enter your name: Subha
Yoo Subha!
*/
```

---


