## 01. Two Pairs with Same Sum

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/satisfy-the-equation5847/1)

### Problem Description

**Task:** Given an array arr[] of positive integers, find four indices a, b, c, and d such that arr[a] + arr[b] = arr[c] + arr[d], where a, b, c, d are all distinct indices.If multiple such quadruplets exist, return the one that is lexicographically smallest when the indices are considered in the order a, b, c, d. If no such quadruplet exists, return {-1, -1, -1, -1}. Ensure a < b and c < d, and the pair (a, b) is lexicographically smaller than the pair (c, d).Examples:Input: arr[] = [3, 4, 7, 1, 2, 9, 8]

#### Examples

##### Example 1

- **Output:**
```text
[-1, -1, -1, -1]
```
- **Explanation:** No two distinct pairs of indices produce the same sum.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n^2)
- **Expected Auxiliary Space Complexity:** O(n^2)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-11-24 23:39:17
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def findPairs(self, arr: list[int]) -> list[int]:
        # code here
        n = len(arr)
        mp = {}
        res = None
        for i in range(n):
            for j in range(i+1,n):
                total = arr[i]+arr[j]
                if total not in mp:
                    mp[total] = (i,j)
                    continue
                a,b = mp[total]
                if a == i or a==j or b==i or b==j:
                    continue
                cur = [a,b,i,j]
                if res is None or cur < res:
                    res = cur
        if res is None:
            return [-1,-1,-1,-1]
        return res
```

*Generated on: 24/11/2026, 23:39:37*