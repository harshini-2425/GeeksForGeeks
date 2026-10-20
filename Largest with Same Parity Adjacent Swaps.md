## 01. Largest with Same Parity Adjacent Swaps

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/even-swap/1)

### Problem Description

**Task:** Given an array arr[], you are allowed to swap two adjacent elements, arr[i] and arr[i + 1] only if their sum is even. Find the lexicographically largest array that can be obtained by performing this operation any number of times, including zero times. Note: An array X is lexicographically larger than another array Y if, at the first position where they differ, X has the larger element.Examples:Input: arr[] = [1, 3, 5]Output: [5, 3, 1]

#### Examples

##### Example 1

- **Output:**
```text
[3, 1, 4, 2]Explanation: [1, 3, 4, 2], [1, 3, 2, 4], [3, 1, 2, 4] and [3, 1, 4, 2] are all possible, among which the last one is lexicographically largest one.
```
- **Explanation:** We can swap any adjacent pair as all have even sum. All possible obtainable arrays are [1, 3, 5], [1, 5, 3], [3, 1, 5], [3, 5, 1], [5, 1, 3] and [5, 3, 1] The array [5, 3, 1] is lexicographically largest.Input: arr[] = [1, 3, 4, 2]

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-20 22:47:25
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def lexicographicallyLargest(self, arr: list[int]) -> list[int]:
        # code here
        n = len(arr)
        i = 0
        while i < n:
            j = i+1
            while j < n and arr[j]%2 == arr[j-1]%2:
                j += 1
            arr[i:j] = sorted(arr[i:j],reverse=True)
            i = j
        return arr
```

*Generated on: 20/10/2026, 22:48:08*