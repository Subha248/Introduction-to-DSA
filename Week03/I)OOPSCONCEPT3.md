### **3:**

### **Do All Methods Need a `return`?**
No, not all methods in Java need a `return` statement. It depends on the method's **return type**.

---

### **1. Methods That Must Have `return`**
- If a method has a **non-void return type** (e.g., `int`, `boolean`, `String`), it **must return a value** of that type.

#### Example:
```java
int add(int a, int b) {
    return a + b;  // Returns an integer
}

boolean isAdult(int age) {
    return age >= 18;  // Returns a boolean
}
```

---

### **2. Methods That Don’t Need `return`**
- Methods with a **void return type** don’t need a `return` statement. They are used for actions like printing or updating.

#### Example:
```java
void greet(String name) {
    System.out.println("Hello, " + name);  // No return needed
}
```

- **Optional Early Exit**:
  - A `void` method can use `return;` to exit early.
  ```java
  void checkAge(int age) {
      if (age < 18) {
          System.out.println("Too young.");
          return;  // Exits early
      }
      System.out.println("Welcome!");
  }
  ```

---

### **Key Rule**
- **Void Methods**: Don’t require `return`.
- **Non-Void Methods**: Must have a `return` statement with a value matching the return type.
  ---
  
### *** EXAMPLE PROGRAM***
Got it! Here's the explanation with **separate programs** for non-void and void methods, just as you provided.

---

### **Non-Void Method Example**
```java
class Human {
    // Non-void method: returns a value
    String baby(String name) {
        return name; // Returns the input name
    }

    public static void main(String[] args) {
        // Create an object of the Human class
        Human subha = new Human();

        String s = "chan";               // Input for the non-void method
        String sub = subha.baby(s);      // Call the non-void method and store the result
        System.out.println(sub);         // Prints the returned value
    }
}
```

---

### **Void Method Example**
```java
class Human {
    // Void method: does not return anything
    void baby(String name) {
        System.out.println(name); // Prints the input name
    }

    public static void main(String[] args) {
        // Create an object of the Human class
        Human subha = new Human();

        subha.baby("chuba"); // Call the void method (directly prints the name)
    }
}
```

---


---

### **Key Rule**
1. **Void Methods**:
   - Do not require a `return` statement.
   - Typically used for actions like printing or updating values.

2. **Non-Void Methods**:
   - Must have a `return` statement with a value that matches their return type.

---

### **Example Program Explanation**

#### **1. Class `Human` Attributes**
```java
int age;
String nickname;
```
- `age`: Stores the age of the person.
- `nickname`: Stores the nickname of the person.

---

#### **2. Non-Void Method: `hasMobile(boolean a, int b)`**
```java
boolean hasMobile(boolean a, int b) {
    System.out.println(b);  // Prints the integer value `b`
    return a;               // Returns the boolean value `a`
}
```
- **Return Type**: `boolean`
- **Key Rule Applied**: This method must have a `return` statement that returns a `boolean` value. In this case, it returns `a`.

---

#### **3. Void Method: `futureAge(int sub)`**
```java
void futureAge(int sub) {
    System.out.println(sub);  // Prints the value of `sub`
}
```
- **Return Type**: `void`
- **Key Rule Applied**: This method does not return anything, so there is no `return` statement. Instead, it prints the value of `sub`.

---

#### **4. Main Method**
```java
public static void main(String[] args) {
    // Create an object
    Human subha = new Human();
    subha.age = 15;
    subha.nickname = "pradha";

    // Print attributes
    System.out.println(subha.age);       // Prints: 15
    System.out.println(subha.nickname);  // Prints: pradha

    // Call non-void method
    boolean m = subha.hasMobile(true, 19);  // Prints: 19 and returns: true
    System.out.println(m);                  // Prints: true

    // Call void method
    subha.futureAge(subha.age + 5);         // Prints: 20
}
```

---

### **Output**
When you run this program, the output will be:
```
15
pradha
19
true
20
```

---

### **How This Example Matches the Key Rule**
1. **Non-Void Method**:
   - `hasMobile` has a `boolean` return type and must return a `boolean` value. It follows the rule by returning `a`.

2. **Void Method**:
   - `futureAge` has a `void` return type, so it doesn't return anything. It follows the rule by printing a value instead.



This program is an excellent example for understanding the difference between `void` and non-`void` methods.
---
---
### **4:**
### **Program: Demonstrating Static Method Usage in Java**

---

### **Program: Using Static Method in Java**

```java
class Human {
    // Static method: can be called without creating an object
    static String baby(String chan) {
        return chan;  // Returns the string passed as an argument
    }

    public static void main(String[] args) {
        // Call the static method directly using the class name
        String s = Human.baby("baby chan");
        System.out.println(s);  // Prints the returned string
    }
}
```

---

### **Explanation**

1. **Static Method `baby`**:
   - The method `baby` is declared as `static`:
     ```java
     static String baby(String chan)
     ```
   - This means it belongs to the class and can be called directly without creating an object of the `Human` class.
   - The method takes a `String` parameter (`chan`) and returns it.

2. **Main Method**:
   - The `main` method is the entry point of the program:
     ```java
     public static void main(String[] args)
     ```
   - Inside the `main` method:
     - The static method `baby` is called directly using the class name `Human`:
       ```java
       String s = Human.baby("baby chan");
       ```
     - The value `"baby chan"` is passed to the `baby` method.
     - The method returns `"baby chan"`, which is stored in the variable `s`.

3. **Output**:
   - The `System.out.println(s);` line prints the value of `s`:
     ```
     baby chan
     ```

---

### **Key Points**
- **Static Method**: 
  - Declared using the `static` keyword.
  - Can be called directly using the class name without creating an object.
- **Method Arguments**: 
  - The string `"baby chan"` is passed as an argument to the `baby` method.
  - The method returns the same string, which is then printed.

---

### **Output**
When you run the program, the output will be:
```
baby chan
```

---

### **Why This Code Is Useful**
- Demonstrates how to use **static methods** in Java.
- Shows how to pass arguments to a method and return a value.

### **EXAMPLE PROGRAM**
``` java
public class Human{
  int age;
  String nickname;
  //method
  boolean ran(boolean input,int a){
   System.out.println(a);
  return input;
  }
  //another method
  int future(int dd){
    return dd;
  }
  // void method
  void vovo(String kaka){
    System.out.println(kaka); // no return
  }
  
  // static method
  
  static String saran(String cha){
    return cha;// return
  }
  
  public static void main (String[] args){
    
    /*static method dont use Object, it uses class to
    call static method*/
    String ff=Human.saran("whats up");
    System.out.println(ff);
    // Object
    Human subha =new Human();
    subha.age=20;
    subha.nickname="ss";
   
    System.out.println(subha.age);
      System.out.println(subha.nickname);
      
         //call method  
         boolean y=subha.ran(true,77);
         //call another method
         int v=subha.future(subha.age+5);
         //call void mehtod
         subha.vovo("soso");

            System.out.println(y);
             System.out.println(v);
      
     
  }
}
```
``` 
### OUTPUT:
whats up
20
ss
77
soso
true
25
```
--- 
