
---

## ✅ Full Java Code

```java
public class NextGreatestLetterDemo {

    public static void main(String[] args) {
        char[] letters = {'c', 'd', 'g', 'j'};
        char target = 'd';  // only one target

        char result = nextGreatestLetter(letters, target);
        System.out.println("Next greatest letter after '" + target + "' is: " + result);
    }

    public static char nextGreatestLetter(char[] letters, char target) {
        int start = 0;
        int end = letters.length - 1;

        // Binary search to find next greatest letter
        while (start <= end) {
            int mid = start + (end - start) / 2;

            if (target < letters[mid]) {
                end = mid - 1;  // go left
            } else {
                start = mid + 1; // go right
            }
        }

        // Wrap around if target >= all letters
        return letters[start % letters.length];
    }
}
```

---

## ✅ Step-by-Step Explanation (Target = `'d'`)

```
letters = ['c', 'd', 'g', 'j']
indices = 0    1    2    3
target = 'd'
```

### Iteration 1

* `start = 0, end = 3`
* `mid = 0 + (3-0)/2 = 1`
* `letters[mid] = 'd'`
* Compare: target >= letters[mid] → `start = mid + 1 = 2`

### Iteration 2

* `start = 2, end = 3`
* `mid = 2 + (3-2)/2 = 2`
* `letters[mid] = 'g'`
* Compare: target < letters[mid] → `end = mid - 1 = 1`

### Loop stops

* `start = 2, end = 1` → `start > end` → exit loop

### Result

```
letters[start % letters.length] = letters[2 % 4] = letters[2] = 'g'
```

✅ **Next greatest letter after 'd' is `'g'`**.

---

