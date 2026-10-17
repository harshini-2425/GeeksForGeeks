## 01. Convert One String to Another with Constraints

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/check-if-it-is-possible-to-convert-one-string-into-another-with-given-constraints4116/1)

### Problem Description

**Task:** Given two strings s1 and s2, consisting only of the characters 'A', 'B', and '#'. Determine whether s1 can be transformed into s2 by performing the following operations on s1:'A' can move only towards the left. 'B' can move only towards the right.Neither 'A' nor 'B' can cross each other.'#' represents an empty position through which 'A' and 'B' can move.Moving the character at index i one step to the left means swapping it with the character at index i - 1, provided i - 1 >= 0. Similarly, moving it one step to the right means swapping it with the character at index i + 1, provided i + 1 < s1.length().Return true if s1 can be transformed into s2; otherwise, return false.Examples:Input: s1 = #A#B#B#, s2 = A###B#B

#### Examples

##### Example 1

- **Output:**
```text
false
```
- **Explanation:** The character 'A' in s1 is at index 1, whereas the corresponding 'A' in s2 is at index 3. Since 'A' can move only towards the left, it cannot reach a position to the right of its current position. Therefore, s1 cannot be transformed into s2, and hence, the answer is false.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n + m)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-17 23:34:01
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def isItPossible(self, s1: str, s2: str) -> bool:
        # code here
        m,n = len(s1),len(s2)
        if m!=n:
            return False
        i,j = 0,0
        while i < m or j < n:
            while i < m and s1[i] == '#':
                i += 1
            while j < n and s2[j] == '#':
                j += 1
            if i>= m and j >= n:
                break
            if i >= m or j >= n:
                return False
            if s1[i] != s2[j]:
                return False
            if s1[i] == 'A' and i< j:
                return False
            if s1[i] == 'B' and i >j:
                return False
            i += 1
            j += 1
        return True
```

*Generated on: 17/10/2026, 23:34:12*