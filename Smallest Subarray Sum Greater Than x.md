## 01. Smallest Subarray Sum Greater Than x

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/smallest-subarray-with-sum-greater-than-x5651/1)

### Problem Description

**Task:** Given an integer x and an array of integers, arr[]. Find the length of the smallest subarray whose sum is strictly greater than x. If no such subarray exists, return 0.Examples:Input: x = 51, arr[] = [1, 4, 45, 6, 0, 19]

#### Examples

##### Example 1

- **Output:**
```text
0
```
- **Explanation:** No subarray has a sum greater than 100. Hence, the answer is 0.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (Python)

- **Submitted:** 2026-11-21 23:30:34
- **Status:** Correct
- **Marks:** 0

```python
class Solution:
    def smallestSubWithSum(self, arr, x):
        # code here
        n = len(arr)
        prefix = [0]*(n+1)
        for i in range(n):
            prefix[i+1] = prefix[i]+arr[i]
        dq = []
        left = 0
        ans = float('inf')
        for i in range(n+1):
            while left<len(dq) and prefix[i]-prefix[dq[left]] > x:
                ans = min(ans,i-dq[left])
                left += 1
            while left<len(dq) and prefix[i] <= prefix[dq[-1]]:
                dq.pop()
            dq.append(i)
        return 0 if ans == float('inf') else ans
```

#### Solution 2 (Python)

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

*Generated on: 21/11/2026, 23:30:48*