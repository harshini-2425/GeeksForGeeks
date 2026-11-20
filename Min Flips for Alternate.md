## 01. Min Flips for Alternate

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/min-number-of-flips3210/1)

### Problem Description

**Task:** Given a binary string s, we can flip any bit (change 0 to 1 or 1 to 0) to make the string alternating. A string is called alternating if no two adjacent characters are the same. Find the minimum number of bit flips required to make the string alternating.Examples:Input: s = "001"

#### Examples

##### Example 1

- **Output:**
```text
1
```
- **Explanation:** Flip the bit at index 0 from 0 to 1 to obtain "101", which is an alternating binary string. Hence, the minimum number of flips required is 1.

##### Example 2

- **Input:**
```text
s = "0001010111"
```
- **Output:**
```text
2
```
- **Explanation:** Flip the bit at indices 1 and 8 to obtain "0101010101", which is an alternating binary string. Hence, the minimum number of flips required is 2.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-11-20 23:03:34
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def minFlips(self, s):
        # Code here
        n = len(s)
        x = 0
        for i in range(n):
            expected = '0' if i%2 == 0 else '1'
            if s[i] != expected:
                x += 1
        return min(x,n-x)
```

*Generated on: 20/11/2026, 23:03:42*