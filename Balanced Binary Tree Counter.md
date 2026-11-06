## 01. Balanced Binary Tree Counter

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/bbt-counter4914/1)

### Problem Description

**Task:** Given a height h, find the maximum number of distinct balanced binary trees of height exactly h.A binary tree is balanced if, for every node, the heights of its left and right subtrees differ by at most 1. A tree with a single node has height 1. An empty tree has height 0.Note: Since the answer can be very large, return it modulo 10⁹ + 7.Examples:Input: h = 1Output: 1Explanation: Only one tree of height 1 exists i.e. a single node.Input: h = 2

#### Examples

##### Example 1

- **Output:**
```text
3
```
- **Explanation:** 3 distinct balanced trees of height 2 exist.

##### Example 2

- **Input:**
```text
h = 3
```
- **Output:**
```text
15
```
- **Explanation:** 15 distinct balanced trees of height 3 exist.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(h)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-11-06 23:08:26
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def countBT(self, h: int) -> int:
        # code here
        MOD = 1000000007
        if h <= 1:
            return 1
        
        prev2 = 1
        prev1 = 1
        for i in range(2,h+1):
            curr = (prev1*prev1+2*prev1*prev2)%MOD
            prev2 = prev1
            prev1 = curr
        return prev1
```

*Generated on: 06/11/2026, 23:08:23*