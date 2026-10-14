## 01. Longest Subarray with Sum K

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/longest-sub-array-with-sum-k0809/1)

### Problem Description

**Task:** Given an array arr[] containing integers and an integer k, your task is to find the length of the longest subarray where the sum of its elements is equal to the given value k. If there is no subarray with sum equal to k, return 0.Examples:Input: arr[] = [10, 5, 2, 7, 1, -10], k = 15

#### Examples

##### Example 1

- **Output:**
```text
0
```
- **Explanation:** No subarray with sum = 5 is present in arr[].

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (2)

#### Solution 1 (Python)

- **Submitted:** 2026-10-14 16:06:21
- **Status:** Correct
- **Marks:** 0

```python
class Solution:
    def longestSubarray(self, arr, k):  
        # code here
        mp = {}
        prefix_sum = 0
        res = 0
        for i in range(len(arr)):
            prefix_sum += arr[i]
            if prefix_sum == k:
                res = i+1
            elif (prefix_sum-k) in mp:
                res = max(res,i-mp[prefix_sum-k])
            if prefix_sum not in mp:
                mp[prefix_sum] = i
        return res
```

#### Solution 2 (Python)

- **Submitted:** 2025-01-15 19:22:47
- **Status:** Correct
- **Marks:** 4

```python
# User function Template for python3

class Solution:
    def longestSubarray(self, arr, k):  
        mp={}
        res =0
        prefsum=0
        for i in range(len(arr)):
            prefsum += arr[i]
            if prefsum == k:
                res = i+1
            elif (prefsum-k) in mp:
                res = max(res, i-mp[prefsum-k])
            if prefsum not in mp:
                mp[prefsum] = i 
        return res# code here
```

*Generated on: 14/10/2026, 22:18:57*