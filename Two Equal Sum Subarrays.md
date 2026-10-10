## 01. Two Equal Sum Subarrays

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/split-an-array-into-two-equal-sum-subarrays/1)

### Problem Description

**Task:** Given an array of integers arr[], return true if it is possible to split it in two subarrays (without reordering the elements), such that the sum of the two subarrays are equal. If it is not possible then return false.

#### Examples

##### Example 1

- **Input:**
```text
arr[] = [1, 2, 3, 4, 5, 5]Output: trueExplanation: We can divide the array into [1, 2, 3, 4] and [5, 5]. The sum of both the subarrays are 10.
```

##### Example 2

- **Input:**
```text
arr[] = [4, 3, 2, 1]Output: falseExplanation: We cannot divide the array into two subarrays with equal sum.
```

#### Constraints

- **1.** `1 ≤ arr.size() ≤ 10⁵ 1 ≤ arr[i] ≤ 10⁶`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (Python)

- **Submitted:** 2026-10-10 17:13:46
- **Status:** Correct
- **Marks:** 0

```python
class Solution:
    def canSplit(self, arr):
        #code here
        total = sum(arr)
        leftsum = 0
        for num in arr:
            leftsum += num
            rightsum = total-leftsum
            if leftsum == rightsum:
                return True
        return False
```

#### Solution 2 (Python)

- **Submitted:** 2026-04-23 16:08:30
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def canSplit(self, arr):
        #code here
        total = sum(arr)
        left = 0
        for num in arr:
            left += num
            if left == total-left:
                return True
        return False
```

*Generated on: 10/10/2026, 17:14:24*