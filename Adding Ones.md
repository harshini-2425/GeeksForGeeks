## 01. Adding Ones

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/adding-ones3628/1)

### Problem Description

**Task:** Consider an array arr[] of size n, initially containing all zeros. You are also given an array updates[] of k positive integers.For each value j in updates[], add 1 to every element arr[i] whose index satisfies i ≥ j.The indices in updates[] are 1-based.Perform all the updates and modify arr[] accordingly.Examples: Input: n = 3, updates[] = [1, 1, 2, 3]

#### Examples

##### Example 1

- **Output:**
```text
[3, 3]
```
- **Explanation:** Initially the array is [0, 0]. After the first 1, it becomes [1, 1]. After the second 1 it becomes [2, 2]. After the third 1, it becomes [3, 3].

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n + k)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-13 22:06:43
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def update(self, n: int, updates: list[int]) -> list[int]:
        # code here
        arr = [0]*n
        for j in updates:
            arr[j-1] += 1
        count = 0
        for i in range(n):
            count += arr[i]
            arr[i] = count
        return arr
```

*Generated on: 13/10/2026, 22:06:51*