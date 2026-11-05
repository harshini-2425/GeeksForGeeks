## 01. Minimum Days

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/minimum-days--170646/1)

### Problem Description

**Task:** Given a string s of length n containing only lowercase English letters, and a permutation array p[] of length n containing integers from 0 to n - 1. On the (i + 1)th day, the character at index p[i] in the string is replaced with '?'. For example:On day 1, replace s[p[0]] with '?'.On day 2, replace s[p[1]] with '?'.On day 3, replace s[p[2]] with '?'.And so on.Find the minimum number of days required so that no two adjacent characters in s are equal, unless at least one of them is '?'.Formally, for every index i (0 <= i < n - 1), the string must satisfy: If s[i] ! = '?' and s[i+1] ! = '?', then s[i] ! = s[i+1].Examples:Input: s = "aabb", p = [2, 1, 3, 0]

#### Examples

##### Example 1

- **Output:**
```text
0 The initial string "abca" already satisfies the condition without replacing any characters.
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n) [Note: For CPP - O(1)]

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-11-05 23:20:28
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def getMinimumDays(self, s: str, p: list[int]) -> int:
        # code here
        n = len(s)
        t = 0
        chars = list(s)
        for i in range(n-1):
            if chars[i] == chars[i+1]:
                t += 1
        if t== 0:
            return 0
        for i in range(n):
            in_pos=p[i]
            
            if in_pos-1 >= 0 and chars[in_pos-1] == chars[in_pos]:
                t -= 1
            if in_pos+1 < n and chars[in_pos] == chars[in_pos+1]:
                t -= 1
            chars[in_pos] = '?'
            if t == 0:
                return i+1
        return n
```

*Generated on: 05/11/2026, 23:20:21*