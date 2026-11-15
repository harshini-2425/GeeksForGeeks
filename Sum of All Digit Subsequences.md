## 01. Sum of All Digit Subsequences

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/sum-of-all-sub-sequences-of-a-number3437/1)

### Problem Description

**Task:** Given a string s which consists of digits, find sum of all digits across all non-empty subsequences of s.Note: Since the answer can be very large, return it modulo 10⁹ + 7.Examples:Input: s = "123"

#### Examples

##### Example 1

- **Output:**
```text
24
```
- **Explanation:** The non-empty subsequences are: [1], [2], [3], [1, 2], [1, 3], [2, 3], [1, 2, 3]. The sum of all digits in these subsequences is: 1 + 2 + 3 + (1 + 2) + (1 + 3) + (2 + 3) + (1 + 2 + 3) = 24.

##### Example 2

- **Input:**
```text
s = "405"
```
- **Output:**
```text
36
```
- **Explanation:** The non-empty subsequences are: [4], [0], [5], [4, 0], [4, 5], [0, 5], [4, 0, 5]. The sum of all digits in these subsequences is 36.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(|s|)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-11-15 23:58:20
- **Status:** Correct
- **Marks:** 2

```python
class Solution:

    def subsequenceSum(self, s):
        """code here"""
        MOD = 10**9+7
        dsum = 0
        n = len(s)
        for ch in s:
            dsum = (dsum+int(ch))%MOD
        dfreq = 1
        for i in range(1,n):
            dfreq = (dfreq*2)%MOD
        return (dsum*dfreq)%MOD
```

*Generated on: 15/11/2026, 23:58:53*