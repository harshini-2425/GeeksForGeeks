## 01. Count Pairs Violating BST Property

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/pairs-violating-bst-property--212515/1)

### Problem Description

**Task:** Given root of a binary tree in which all node values are distinct, count pairs of nodes that violate any of the following Binary Search Tree (BST) properties. All values in the left subtree are strictly smaller.All values in the right subtree are strictly greater.Examples:Input: root[] = [10, 50, 40, N, N, 20, 30]Output: 5

#### Examples

##### Example 1

- **Explanation:** There are total 10 pairs (80, 30), (80, 60), (80, 50), (30, 60), (40, 70), (40, 30), (40, 50), (70, 30), (70, 60), (70, 50) which violate the BST properties.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-23 23:09:42
- **Status:** Correct
- **Marks:** 4

```python
# BST Node Structure
class Node:
    def __init__(self, val):
        self.data = val
        self.left = None
        self.right = None


class Solution:
    def pairsViolatingBST(self, root):
        # code here
        arr = []
        self.inorder(root,arr)
        _,count = self.mergeSort(arr)
        return count
    def mergeSort(self,arr):
        if len(arr) <= 1:
            return arr,0
        mid = len(arr)//2
        left,countLeft = self.mergeSort(arr[:mid])
        right,countRight = self.mergeSort(arr[mid:])
        merged = []
        i=j=0
        count= countLeft+countRight
        while i < len(left) and j < len(right):
            if left[i] <= right[j]:
                merged.append(left[i])
                i += 1
            else:
                count += len(left)-i
                merged.append(right[j])
                j += 1
        merged.extend(left[i:])
        merged.extend(right[j:])
        return merged,count
    def inorder(self,root,arr):
        if root is None:
            return
        self.inorder(root.left,arr)
        arr.append(root.data)
        self.inorder(root.right,arr)
```

*Generated on: 23/10/2026, 23:09:48*