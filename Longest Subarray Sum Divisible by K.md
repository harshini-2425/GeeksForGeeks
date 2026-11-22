## 01. Longest Subarray Sum Divisible by K

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/longest-subarray-with-sum-divisible-by-k1259/1)

### Problem Description

**Task:** Given an array arr[] and a positive integer k, find the length of the longest subarray whose sum is divisible by k.Note: If there is no subarray with sum divisible by k, then return 0.Examples:Input: arr[] = [2, 7, 6, 1, 4, 5], k = 3

#### Examples

##### Example 1

- **Output:**
```text
2
```
- **Explanation:** The subarray is [2, -2] has sum = 0, which is divisible by 2.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(min(n, k))

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-11-22 23:16:37
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def longestSubarrayDivK(self, arr, k):
        # code here
        n = len(arr)
        res = 0
        prefIdx = {}
        sum = 0
        for i in range(n):
            sum = (sum+arr[i])%k
            if sum == 0:
                res = i+1
            elif sum in prefIdx:
                res = max(res,i-prefIdx[sum])
            else:
                prefIdx[sum] = i
        return res
```

*Generated on: 22/11/2026, 23:16:46*