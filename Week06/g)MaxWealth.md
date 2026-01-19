
```java
public class MAXWEALTH {
  
  public static void main(String[] args){
    // your 2D array of customers + their bank balances
    int accounts[][] = { {1,2,3}, {3,2,1} };

    // print the richest customer's wealth
    System.out.print(maximumWealth(accounts));
  }

  public static int maximumWealth(int[][] accounts) {

    int ans = 0;  
    // ans = tracks the maximum wealth found so far

    // loop through each customer (each row)
    for(int r = 0; r < accounts.length; r++){

      int sum = 0;
      // sum = total wealth of ONE customer (one row)

      // loop through each bank account of that customer
      for(int c = 0; c < accounts[r].length; c++){
        sum += accounts[r][c];  
        // keep adding their balances: 1+2+3 or 3+2+1
      }

      // after finishing the row, check if this customer is richer
      if(sum > ans){
        ans = sum;  
        // update the richest wealth
      }
    }

    return ans;  
    // final richest wealth
  }
}
```

---

## Quick example so your brain doesn’t glitch

### For accounts = `[[1,2,3],[3,2,1]]`

### r = 0 → Customer 1

```
sum = 1 + 2 + 3 = 6
ans = 6
```

### r = 1 → Customer 2

```
sum = 3 + 2 + 1 = 6
ans stays 6
```

### return → **6**

