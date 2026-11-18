## 01. XOR of Number Range

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/find-xor-of-numbers-from-l-to-r/1)

### Problem Description

**Task:** Given two integers l and r, find the bitwise XOR of all integers in the range [l, r] (both inclusive).Examples:Input: l = 4, r = 8

#### Examples

##### Example 1

- **Output:**
```text
5
```
- **Explanation:** The XOR of all integers from 5 to 9 is (5 xor 6 xor 7 xor 8 xor 9) = 5.Constraints:1 ≤ l ≤ r ≤ 10⁹

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(1)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-11-18 23:15:14
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def findXOR(self, l: int, r: int) -> int:
        # code here
        xor_r = self.computeXOR(r)
        xor_l_minus_1 = self.computeXOR(l-1)
        return xor_r^xor_l_minus_1
    def computeXOR(self,n:int) -> int:
        rem = n%4
        if rem == 0:
            return n
        if rem == 1:
            return 1
        if rem == 2:
            return n+1
        return 0
```

*Generated on: 18/11/2026, 23:15:23*