## 01. Largest Subarray with 0 Sum

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/largest-subarray-with-0-sum/1)

### Problem Description

**Task:** Given an array arr[] containing both positive and negative integers, the task is to find the length of the longest subarray with a sum equals to 0.Note: A subarray is a contiguous part of an array, formed by selecting one or more consecutive elements while maintaining their original order.Examples:Input: arr[] = [15, -2, 2, -8, 1, 7, 10, 23]

#### Examples

##### Example 1

- **Output:**
```text
5
```
- **Explanation:** The longest subarray with sum equals to 0 is [0, -4, 3, 1, 0]

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (2)

#### Solution 1 (Python)

- **Submitted:** 2026-11-01 16:40:30
- **Status:** Correct
- **Marks:** 0

```python
class Solution:
    def maxLength(self, arr):
        # code here
        mp = {0:-1}
        curSum = 0
        maxlen = 0
        for i in range(len(arr)):
            curSum += arr[i]
            if curSum in mp:
                c = mp[curSum]
                maxlen = max(maxlen,i-c)
            else:
                mp[curSum] = i
        return maxlen
```

#### Solution 2 (Python)

- **Submitted:** 2025-11-18 21:51:39
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def maxLength(self, arr):
        # code here
        firstSeen = {}
        prefixSum = 0
        maxLen = 0
        length = 0
        firstSeen[0] = -1
        for i in range(len(arr)):
            prefixSum += arr[i]
            if prefixSum in firstSeen:
                previndex = firstSeen[prefixSum]
                length = i-previndex
                maxLen = max(maxLen,length)
            else:
                firstSeen[prefixSum] = i
        return maxLen
```

*Generated on: 01/11/2026, 16:42:10*