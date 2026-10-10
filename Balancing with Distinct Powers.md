## 01. Balancing with Distinct Powers

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/balancing-pan5038/1)

### Problem Description

**Task:** Given a simple weighing scale with two pans, a target weight b, and a set of weights where each weight is a distinct power of a, find if the scale can be balanced such that: b + (some powers of a) = (some other powers of a)Note: Exactly one weight is available for each power of a, so each power can be used at most once.Examples:Input: a = 4, b = 11

#### Examples

##### Example 1

- **Output:**
```text
true
```
- **Explanation:** 5 + 3 + 1 = 9. So, target = 5 can be balanced using powers of 3.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(log b)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-10 22:17:34
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def balancePan(self, a, b):
        # code here
        while b > 0:
            rem = b%a
            if rem == 0 or rem == 1:
                b //= a
            elif rem == a-1:
                b = b//a+1
            else:
                return False
        return True
```

*Generated on: 10/10/2026, 22:17:44*