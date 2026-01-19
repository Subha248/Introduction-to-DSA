
### **What Are Access Specifiers?**
Access specifiers in Java define **who can access a class, method, or variable**. They control the visibility of members (attributes, methods, constructors) in your program.

There are **four main access specifiers** in Java:
1. **public**: Accessible from **anywhere**.
2. **private**: Accessible **only within the same class**.
3. **protected**: Accessible within the **same package** and by **subclasses**.
4. **(default)**: If you don’t specify any access modifier, it is accessible within the **same package** (also called "package-private").

---
```java

// Define the Human class
public class Human {
    // Public instance variable to store the age of a human
    public int age;  
    
    // Public instance variable to store the name of a human
    public String name;

    // Public method to display the age
    public void display() {  
        // Print the age to the console
        System.out.println("Age: " + age);
    }
}

// Define the Main class
class Main {
    // Main method: Entry point of the program
    public static void main(String[] args) {
        // Create an object of the Human class
        Human human = new Human();

        // Assign a value to the 'age' variable of the human object
        human.age = 25; // Setting the age to 25 (Accessing from outside the Human class)

        // Assign a value to the 'name' variable of the human object
        human.name = "Nandhini"; // Setting the name to "Nandhini" (Accessing from outside the Human class)

        // Call the display() method to print the age of the human object
        human.display(); // Calling the method from outside the Human class
                         // Output will be: Age: 25
    }
}
```

Output of the Program:

Age: 25

---

### 2) **Java Encapsulation with Private Variables**
```java
// Define the Human class
class Human {
    // Private variable to store the age of a human
    private int age;

    // Public setter method to set the value of the private age variable
    public void setAge(int a) {
        // Assign the parameter value 'a' to the private variable 'age'
        age = a;
    }

    // Public getter method to get the value of the private age variable
    public int getAge() {
        // Return the value of the private variable 'age'
        return age;
    }
}

// Define the Main class
public class Main {
    public static void main(String[] args) {
        // Create an object of the Human class
        Human human = new Human();

        // Use the setter method to set the age of the human object
        human.setAge(30); // Setting the private variable 'age' to 30

        // Use the getter method to retrieve and print the age of the human object
        System.out.println(human.getAge()); // Output: 30
    }
}
```

### **Explanation of the Code:**
1. **Encapsulation**:
   - The `age` variable is declared as `private` to restrict direct access from outside the `Human` class.
   - Public methods (`setAge` and `getAge`) provide controlled access to the `age` variable.

2. **Setter Method**:
   - The `setAge` method takes a parameter and assigns it to the private variable `age`.
   - It allows external classes to set the value of `age`.

3. **Getter Method**:
   - The `getAge` method returns the value of the private variable `age`.
   - It allows external classes to retrieve the value of `age`.

4. **Main Class**:
   - An object of the `Human` class is created in the `main` method.
   - The private variable `age` is set using the `setAge` method.
   - The value of `age` is retrieved and printed using the `getAge` method.

---


  ### Output:
  ```
  30
  ```
  


### **Beginner-Friendly Summary Table**
| Access Modifier | Same Class | Same Package | Subclass (Different Package) | Other Classes (Different Package) |
|------------------|------------|--------------|-------------------------------|------------------------------------|
| **public**       | ✅         | ✅           | ✅                            | ✅                                 |
| **private**      | ✅         | ❌           | ❌                            | ❌                                 |
| **protected**    | ✅         | ✅           | ✅                            | ❌                                 |
| **default**      | ✅         | ✅           | ❌                            | ❌                                 |

---



