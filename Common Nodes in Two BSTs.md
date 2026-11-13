## 01. Common Nodes in Two BSTs

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/print-common-nodes-in-bst/1)

### Problem Description

**Task:** Given the roots r1 and r2 of two Binary Search Trees (BST), find all nodes that are present in both trees i.e. the intersection nodes of the two BSTs.Return the common node values in sorted order.Examples:Input: r1 = [5, 1, 10, 0, 4, 7, N, N, N, N, N, N, 9], r2 = [10, 7, 20, 4, 9, N, N] Output: [4, 7, 9, 10]Explanation: The values present in both BSTs are 4, 7, 9, and 10. Hence, the answer is [4, 7, 9, 10].Input: r1 = [10, 2, 11, 1, 3, N, N], r2 = [2, 1, 3]Output: [1, 2, 3]Explanation: The values 1, 2, and 3 are present in both BSTs. Hence, the answer is [1, 2, 3].

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n1 + n2), where n1 and n2 are the number of nodes in r1 and r2 respectively.
- **Expected Auxiliary Space Complexity:** O(h1 + h2), where h1 and h2 are the heights of r1 and r2 respectively.

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-11-13 23:06:36
- **Status:** Correct
- **Marks:** 4

```python
#Structure of a Binary Search Tree node
class Node:
    def __init__(self, val):
        self.data = val
        self.left = None
        self.right = None
    def insert(self,root:'Node',key:int)->'Node':
        if not root:
            return Node(key)
        if key < root.data:
            root.left = self.insert(root.left,key)
        else:
            root.right = self.insert(root.right,key)
        return root

class Solution:
    def findCommon(self, r1: 'Node', r2: 'Node') -> list[int]:
        # code here
        s1 = []
        s2 = []
        res = []
        while True:
            while r1:
                s1.append(r1)
                r1 = r1.left
            while r2:
                s2.append(r2)
                r2 = r2.left
            if len(s1) == 0 or len(s2) == 0:
                break
            curr1 = s1[-1]
            curr2 = s2[-1]
            if curr1.data == curr2.data:
                res.append(curr1.data)
                s1.pop()
                s2.pop()
                r1 = curr1.right
                r2 = curr2.right
            elif curr1.data < curr2.data:
                s1.pop()
                r1 = curr1.right
                r2 = None
            else:
                s2.pop()
                r2 = curr2.right
                r1 = None
        return res
```

*Generated on: 13/11/2026, 23:06:45*