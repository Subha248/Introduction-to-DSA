

```java
public class min {
    public static void main(String[] args) {
        int[] arr = { 18, 12, -1, 3, 14, 28 };   // create an array

        int ans = Min(arr);                      // call Min() method to find minimum
        System.out.print(ans);                   // print the minimum value
    }

    public static int Min(int[] arr) {
        // assume arr.length is not 0
        int ans = arr[0];                        // start by assuming first element is minimum
        for (int i = 0; i < arr.length; i++) {   // loop through each element
            if (arr[i] < ans) {                  // if current element is smaller than ans
                ans = arr[i];                    // update ans with current element
            }
        }
        return ans;                              // return the minimum value
    }
}
```

---

### 🔹 Quick Explanation:

1. `int ans = arr[0];` → assume the first element is the minimum.
2. `for (i=0; i<arr.length; i++)` → check all elements.
3. `if(arr[i] < ans)` → if a smaller element is found, update `ans`.
4. `return ans;` → finally returns the smallest number in the array.

---

Output for your array `{18, 12, -1, 3, 14, 28}` →

```
-1
```

