## 01. Minimize Max Min Diff with Subarray Removal

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/minimize-the-difference/1)

### Problem Description

**Task:** You are given an array arr[] of size n. You need to remove a subarray of size k , such that the difference between the maximum and minimum values of the remaining array is minimized. Find the minimum value obtained after performing the operation of the removal of the subarray.Examples:Input: arr = [1, 2, 3, 4, 5], k = 3 Output: 1Explanation: We remove first subarray of length 3, the remaining array is [4,5] and the difference of maximum and minimum element is 1 i.e 5 - 4 = 1Input: arr = [2, 3, 1, 4, 6, 7], k = 3Output: 2Explanation: If we remove the subarray [2,3,1] then remaining array is [4,6,7] and the difference = 7-4 = 3If we remove the subarray [3,1,4] then remaining array is [2,6,7] and the difference = 7-2 = 5If we remove the subarray [1,4,6] then remaining array is [2,3,7] and the difference = 7-2 = 5If we remove the subarray [4,6,7] then remaining array is [2,3,1] and the difference = 3-1 = 2So the answer is min(3,5,5,2) = 2

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-26 23:37:46
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def minDiff(self, k: int, arr: list[int]) -> int:
        # code here
        n = len(arr)
        suffixMax = [0]*n
        suffixMin = [0]*n
        suffixMin[n-1] = [0]*n
        suffixMax[n-1] = arr[n-1]
        suffixMin[n-1] = arr[n-1]
        for i in range(n-2,-1,-1):
            suffixMax[i] = max(arr[i],suffixMax[i+1])
            suffixMin[i] = min(arr[i],suffixMin[i+1])
        res = suffixMax[k] - suffixMin[k]
        prefixMax = arr[0]
        prefixMin = arr[0]
        for i in range(1,n-k):
            currentMax = max(prefixMax,suffixMax[i+k])
            currentMin = min(prefixMin,suffixMin[i+k])
            res = min(res,currentMax-currentMin)
            prefixMax = max(prefixMax,arr[i])
            prefixMin = min(prefixMin,arr[i])
        res = min(res,prefixMax-prefixMin)
        return res
```

*Generated on: 26/10/2026, 23:37:47*