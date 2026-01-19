
---

## **Check if a Number is a Palindrome**

### **Problem Statement**
Write a program to check if a given number is a palindrome. A number is considered a palindrome if it reads the same backward as forward.

---

### **Program**

```java
public class Main {
    public static void main(String[] args) {
        int n = 1221; // Input number
        int original = n; // Store the original number for comparison
        int sum = 0; // Variable to store the reversed number

        // Reverse the number
        while (n > 0) {
            int ld = n % 10; // Extract the last digit
            sum = sum * 10 + ld; // Build the reversed number
            n = n / 10; // Remove the last digit
        }

        // Compare the reversed number with the original number
        if (sum == original) {
            System.out.println("palindrome"); // Print palindrome if the number matches its reverse
        } else {
            System.out.println("not palindrome"); // Print not palindrome otherwise
        }
    }
}
```

---

### **Explanation**

1. **Initialization**:
   - `n`: Input number to be checked.
   - `original`: Stores the original value of `n` for comparison after reversing.
   - `sum`: Will store the reversed number.

2. **Reverse the Number**:
   - Use a `while` loop to reverse the number.
   - Extract the last digit of `n` using `n % 10`.
   - Add the extracted digit to `sum` by shifting the digits (`sum * 10 + ld`).
   - Remove the last digit of `n` using integer division (`n = n / 10`).

3. **Comparison**:
   - After reversing the number, compare `sum` with `original`.
   - If they are equal, the number is a palindrome.
   - Otherwise, it is not a palindrome.

---

### **Test Cases**

| **Input** | **Original Number** | **Reversed Number** | **Output**        |
|-----------|---------------------|---------------------|-------------------|
| 1221      | 1221                | 1221                | palindrome        |
| 1234      | 1234                | 4321                | not palindrome    |
| 101       | 101                 | 101                 | palindrome        |
| 123       | 123                 | 321                 | not palindrome    |

---

### **Output**

#### Example 1:
**Input**:
```
n = 1221
```

**Output**:
```
palindrome
```

#### Example 2:
**Input**:
```
n = 1234
```

**Output**:
```
not palindrome
```

---

### **Time Complexity**
- **Reversing the Number**: \( O(\log_{10}n) \), where \( n \) is the input number.
- **Comparison**: \( O(1) \).

**Overall Time Complexity**: \( O(\log_{10}n) \).

### **Space Complexity**
- **Space Used**: \( O(1) \).

---

