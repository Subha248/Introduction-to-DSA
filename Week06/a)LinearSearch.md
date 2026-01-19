
```java
import java.util.*;

public class sample {
    public static void main(String[] args) {

        int target = 12; // element to search for
        int arr[] = { 12, 34, 23, 435, 53, 22, 45, 34 }; // array of elements

        System.out.println(Arrays.toString(arr)); // print array
        int ans = Linear(arr, target); // call linear search
        System.out.println("Thus the target element is at index: " + ans); // print result
    }

    // Linear search method
    public static int Linear(int arr[], int target) {
        if (arr.length == 0) {
            return -1; // empty array, return -1
        }
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == target) {
                return i; // target found, return index
            }
        }
        return -1; // target not found
    }
}
```

If you want, I can also make it **even cleaner** by shortening variable names and comments so it’s super easy to read at a glance. Do you want me to do that?
