
```java
public class range{
  public static void main (String[] args){
    int[] arr={18,12,-7,3,14,28};         // create array

    int ans=Range(arr,3,1,4);              // call Range() to search 3 from index 1 to 4
    System.out.println(ans);               // print the result
  }

  public static int Range(int arr[],int target,int start,int end){
    if(arr.length==0){                      // if array is empty
      return -1;                             // return -1 (not found)
    }

    for(int i=start;i<=end;i++){            // loop from start to end (inclusive)
      if(arr[i]==target){                   // if current element equals target
        return i;                           // return its index
      }
    }

    return -1;                              // target not found in the range
  }
}
```

---

### Quick Notes:

* `arr.length==0` → checks empty array
* `for (i=start; i<=end; i++)` → loops only in the specified range
* `return i` → returns index if target found
* `return -1` → if target isn’t found

---

