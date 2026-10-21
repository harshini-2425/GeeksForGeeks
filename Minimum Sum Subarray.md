## 01. Minimum Sum Subarray

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/smallest-sum-contiguous-subarray/1)

### Problem Description

**Task:** Given an array arr[], find the minimum sum of a subarray containing atleast one element in the given array.Examples:Input: arr[] = [3, -4, 2, -3, -1, 7, -5]

#### Examples

##### Example 1

- **Output:**
```text
1
```
- **Explanation:** The subarray [1] has the minimum sum, which is 1.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-21 22:20:10
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def minSubarraySum(self, arr: list[int]) -> int:
        # code here
        curMin = float('inf')
        ans = float('inf')
        for num in arr:
            if curMin > 0:
                curMin = num
            else:
                curMin += num
            ans = min(ans,curMin)
        return ans
```

*Generated on: 21/10/2026, 22:20:18*