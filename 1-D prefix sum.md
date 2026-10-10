## 01. 1-D prefix sum

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/1-d-prefix-sum/1)

### Problem Description

**Task:** Given an array arr[], the goal is to compute its prefix sum array. The prefix sum array, prefixSum[], should be of the same length as arr[], where each element prefixSum[i] represents the sum of all elements from the start of the array up to index i, i.e., prefixSum[i] = arr[0] + arr[1] + .... + arr[i].

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [10, 20, 10, 5, 15]Output: [10, 30, 40, 45, 60]Explanation: For each index i, add all the elements from 0 to i:prefixSum[0] = 10, prefixSum[1] = 10 + 20 = 30, prefixSum[2] = 10 + 20 + 10 = 40 and so on.
```

##### Example 2

- **Input:**
```text
arr[] = [30, 10, 10, 5, 50]Output: [30, 40, 50, 55, 105]Explanation: For each index i, add all the elements from 0 to i:prefixSum[0] = 30, prefixSum[1] = 30 + 10 = 40, prefixSum[2] = 30 + 10 + 10 = 50 and so on.
```

#### Constraints

- **1.** `1 ≤ arr.size() ≤ 10⁵^1 ≤ arr[i] ≤ 10⁴^`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (2)

#### Solution 1 (Python)

- **Submitted:** 2026-10-10 15:55:18
- **Status:** Correct
- **Marks:** 0

```python
class Solution:
    def prefSum(self, arr):
        # code here
        pre = [0]*len(arr)
        pre[0] = arr[0]
        for i in range(1,len(arr)):
            pre[i] += pre[i-1]+arr[i]
        return pre
```

#### Solution 2 (Python)

- **Submitted:** 2026-10-10 15:48:17
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def prefSum(self, arr):
        # code here
        pre = [0]*len(arr)
        pre[0] = arr[0]
        for i in range(1,len(arr)):
            pre[i] += pre[i-1]+arr[i]
        return pre
```

*Generated on: 10/10/2026, 16:29:55*