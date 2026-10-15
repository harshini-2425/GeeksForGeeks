## 01. Maximum Without 3 Consecutive Set Bits

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/geek-hates-too-many-1s--170647/1)

### Problem Description

**Task:** Given a non-negative integer n, you can only change a set bit (1) to an unset bit (0). Find the maximum possible value of n such that its binary representation does not contain three consecutive set bits (111) after performing zero or more allowed operations.Examples:Input: n = 2

#### Examples

##### Example 1

- **Output:**
```text
6
```
- **Explanation:** The binary representation of 7 is 111, which contains three consecutive set bits. Changing the rightmost set bit to 0 gives: 111 - > 110. Thus, the maximum possible value is 6.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(1)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-15 23:15:37
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def maxValue(self, n: int) -> int:
        """code here"""
        self.bits = [0]*31
        self.dp = [[0]*3 for _ in range(31)]
        self.vis = [[False]*3 for _ in range(31)]
        for i in range(31):
            self.bits[i] = (n>>i)&1
        return self.solve(30,0)
    def solve(self,pos,ones):
        if pos < 0:
            return 0
        if self.vis[pos][ones]:
            return self.dp[pos][ones]
        self.vis[pos][ones] = True
        res = self.solve(pos-1,0)
        if self.bits[pos] == 1 and ones < 2:
            res = max(res,(1<<pos)+self.solve(pos-1,ones+1))
        self.dp[pos][ones] = res
        return res
```

*Generated on: 15/10/2026, 23:15:42*