
```java
public class Max2D { // Define a class named MIN2D
    public static void main(String[] args) { // Main method, entry point of program
        int[][] arr = { // 2D array declaration and initialization
            {1, 2, 3},      // row 0
            {4, 7, 5, 6},   // row 1
            {8, 9, 13, 23}  // row 2
        };

        int ans = Array2D(arr); // Call Array2D method to find max and store result in ans
        System.out.println(ans); // Print the maximum value found
    }

    public static int Array2D(int[][] arr) { // Method that takes 2D array and returns max value
        int max = Integer.MIN_VALUE; // Start with the smallest possible int value
        for (int row = 0; row < arr.length; row++) { // Loop through each row of 2D array
            for (int col = 0; col < arr[row].length; col++) { // Loop through each element in current row
                if (arr[row][col] > max) { // If current element is greater than max
                    max = arr[row][col];   // Update max with current element
                }
            }
        }
        return max; // Return the maximum value found in the array
    }
}
```

💡 Key points:

* `Integer.MIN_VALUE` ensures any number in the array will be larger initially.
* `arr.length` gives number of rows; `arr[row].length` gives number of columns in that row.
* The nested loop checks **every element**.

This code is perfect for finding the maximum in a jagged 2D array (rows of different lengths).

