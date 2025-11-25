AMAZON INTERVIEW QUES

---


```java
public class infiniteArray{ 
    public static void main(String[] args) {
        int[] arr = { 3, 5, 7, 9, 10, 90, 100, 130, 140, 160, 170 };
        int target = 10;
        System.out.println(ans(arr, target));   // print found index (or -1)
    }

    static int ans(int[] arr, int target) {
        int start = 0;            // window start index
        int end = 1;              // window end index (initial box [0..1])

        // EXPANSION PHASE: grow the window until arr[end] >= target
        while (target > arr[end]) {          // while target is to the right of current box
            int newStart = end + 1;          // next window will begin after current end
            end = end + (end - start + 1) * 2; // enlarge box: end = end + boxSize*2
            start = newStart;               // shift start to newStart
        }

        // BINARY SEARCH PHASE: search only inside [start..end]
        return BS(arr, target, start, end);
    }

    static int BS(int[] arr, int target, int start, int end) {
        while (start <= end) {
            int mid = start + (end - start) / 2; // safe mid index
            if (target < arr[mid])               // target left of mid
                end = mid - 1;
            else if (target > arr[mid])          // target right of mid
                start = mid + 1;
            else {                               // found
                return mid;
            }
        }
        return -1; // not found
    }
}
```

---

## 2) What each important line does (one-liner mapping)

* `int start = 0, end = 1;` — begin with a tiny search box covering indexes `0` and `1`.
* `while (target > arr[end])` — if the value at `end` is still smaller than target, the target is not inside the current box → expand.
* `int newStart = end + 1;` — next box will start at the element right after current `end`.
* `end = end + (end - start + 1) * 2;` — double-ish expansion: increase `end` by `boxSize * 2`. (`boxSize = end-start+1`)
* `start = newStart;` — move `start` to the new box start.
* `BS(...)` — perform a normal binary search inside the discovered window `[start..end]`.
* `mid = start + (end - start)/2` — correct mid calculation.
* `if/else` — standard binary search comparisons and pointer updates; `return mid` when found.

---

## 3) Full dry run (example values)

**Input**

```
arr = [3, 5, 7, 9, 10, 90, 100, 130, 140, 160, 170]
target = 10
```

### Expansion phase (loop `while (target > arr[end])`)

Start: `start = 0`, `end = 1`
`arr[1] = 5`, target `10` → `10 > 5` true → expand

* **Iteration E1**

  * `newStart = end + 1 = 2`
  * `boxSize = end - start + 1 = 1 - 0 + 1 = 2`
  * `end = end + boxSize * 2 = 1 + 2*2 = 5`
  * `start = newStart = 2`
  * Now window = `[2 .. 5]` (values: `7, 9, 10, 90`)
  * Check loop condition: `arr[end] = arr[5] = 90`, `target = 10`, `10 > 90`? **No** → stop expanding.

**Result of expansion:** `start = 2`, `end = 5`. We are guaranteed (in this run) that `target <= arr[end]` so target, if present, must be inside indexes `2..5`.

---

### Binary search phase (`BS(arr, 10, 2, 5)`)

Initial: `start = 2`, `end = 5`

| Step | start | end | mid = start + (end-start)/2 |  arr[mid] | Comparison | Action              |
| ---- | ----- | --- | --------------------------: | --------: | ---------- | ------------------- |
| 1    | 2     | 5   |       mid = 2 + (5-2)/2 = 3 |  arr[3]=9 | 10 > 9     | start = mid + 1 = 4 |
| 2    | 4     | 5   |       mid = 4 + (5-4)/2 = 4 | arr[4]=10 | 10 == 10   | return 4 (found)    |

Binary search returns index `4`. That is printed by `main`.

**Final output:** `4` — matches the example.

---

## 4) Quick numeric intuition for expansion formula

* `boxSize = end - start + 1` = number of elements currently in the box.
* `end = end + boxSize * 2` roughly *triples* the covered range length (depending on start shift), which yields very fast exponential growth of the search window. That’s why this finds the approximate region in `O(log i)` steps where `i` is the index of the target.

---

## 5) Important caveat (practical Java)

* Your code assumes `arr[end]` is always safe to access. That is true for the **infinite-array model** used in the theoretical problem.
* If you run this on a **real finite Java array** and the target is larger than all elements, the expansion can push `end` beyond `arr.length - 1` and cause `ArrayIndexOutOfBoundsException`. In production Java you either:

  * Add a guard `while (end < arr.length && target > arr[end])` and clamp `end` after expansion, or
  * Use try/catch around `arr[end]` accesses if simulating a true infinite interface that throws on out-of-range access.

You’ve asked not to add extras — so your current version assumes the infinite-array behavior. For the sample input it runs fine and returns `4`.

---

## TL;DR — one-line summary

1. Expand a small window exponentially until the target fits inside the window.
2. Run binary search in that window.
3. For your `arr` and `target=10` the steps are: expand `[0..1]` → `[2..5]`, then binary search in `[2..5]` → find target at index `4`.


* Show the exact console output of each iteration (printing `start,end,mid`), or
* Convert this into a step-by-step trace that prints the variables as the code runs. Which of those would you prefer?
