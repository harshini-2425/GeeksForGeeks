## 01. Distinct Pairs with Diff K

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/count-distinct-pairs-with-difference-k1233/1)

### Problem Description

**Task:** Given an integer array of size n and a non-negative integer k, count all distinct pairs with a difference equal to k, i.e., arr[ i ] - arr[ j ] = k.

#### Examples

##### Example 1

- **Input:**
```text
arr = [1, 5, 4, 1, 2], k = 0
```
- **Output:**
```text
1
```
- **Explanation:** There is only one pair (1, 1) whose difference equal to 0.

##### Example 2

- **Input:**
```text
arr = [1, 5, 3], k = 2
```
- **Output:**
```text
2
```
- **Explanation:** There are two pairs (5, 3) and (1, 3) whose difference equal to 2.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-11-12 11:40:04
- **Status:** Correct
- **Marks:** 4

```python
from typing import List
class Solution:
    def countPairs(self, arr: List[int], k: int) -> int:
        # Code here
        freq = {}
        cnt = 0
        for i in range(len(arr)):
            freq[arr[i]] = freq.get(arr[i],0)+1
        for num in freq:
            if k == 0:
                if freq[num] >= 2:
                    cnt += 1
            else:
                if num+k in freq:
                    cnt += 1
        return cnt
```

*Generated on: 12/11/2026, 18:09:02*