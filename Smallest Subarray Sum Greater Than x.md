## 01. Smallest Subarray Sum Greater Than x

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/smallest-subarray-with-sum-greater-than-x5651/1)

### Problem Description

**Task:** Given a number x and an array of integers arr, find the smallest subarray with sum strictly greater than the given value. If such a subarray do not exist return 0 in that case.

#### Examples

##### Example 1

- **Input:**
```text
x = 51, arr[] = [1, 4, 45, 6, 0, 19]
```
- **Output:**
```text
3
```
- **Explanation:** Minimum length subarray is [4, 45, 6]

##### Example 2

- **Input:**
```text
x = 100, arr[] = [1, 10, 5, 2, 7]
```
- **Output:**
```text
0
```
- **Explanation:** No subarray exist

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-20 18:34:28
- **Status:** Correct
- **Marks:** 2

```python
from collections import deque
class Solution:
    def smallestSubWithSum(self, x, arr):
        # code here 
        n = len(arr)
        prefix = [0]*(n+1)
        for i in range(n):
            prefix[i+1] = prefix[i]+arr[i]
        dq = deque()
        ans = n+1
        for i in range(n+1):
            while dq and prefix[i]-prefix[dq[0]] > x:
                ans = min(ans,i-dq.popleft())
            while dq and prefix[i] <= prefix[dq[-1]]:
                dq.pop()
            dq.append(i)
        return ans if ans <= n else 0
```

*Generated on: 20/10/2026, 18:34:45*