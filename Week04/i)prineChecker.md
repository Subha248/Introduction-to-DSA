
---

### ✅ **Final Correct Code**

```java
import java.util.*;

public class prime {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int n = sc.nextInt();
    boolean ans = isPrime(n);
    System.out.print(ans);
    sc.close();
  }

  static boolean isPrime(int n) {
    if (n <= 1) {
      return false;
    }
    for (int i = 2; i * i <= n; i++) {
      if (n % i == 0)
        return false;
    }
    return true;
  }
}
```

---

### 💡 How it works (example: `n = 17`)

1. You enter `17`
2. Program calls `isPrime(17)`
3. It checks `if (17 <= 1)` → ❌ false → continue
4. The loop runs:

   * `i = 2` → check `2 * 2 <= 17` → ✅ true
     → check `17 % 2 == 0` → ❌ false
   * `i = 3` → `3 * 3 <= 17` → ✅
     → `17 % 3 == 0` → ❌ false
   * `i = 4` → `4 * 4 <= 17` → ✅
     → `17 % 4 == 0` → ❌ false
   * `i = 5` → `5 * 5 <= 17` → ❌ (25 > 17) → stop loop
5. No divisors found → return `true`
6. Output → `true` ✅ (means 17 is prime)

---

### 💬 If you enter `n = 15`

* `i = 2` → `15 % 2 != 0`
* `i = 3` → `15 % 3 == 0` ✅ → immediately returns `false`
* Output → `false` (15 is not prime)

---

