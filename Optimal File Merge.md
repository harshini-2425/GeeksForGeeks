## 01. Optimal File Merge

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/optimal-file-merge/1)

### Problem Description

**Task:** Given an integer array files[], where files[i] represents the size of the i-th file, merge all the files into a single file with the minimum total computation cost.The cost of merging two files of sizes x and y is x + y. After merging, a new file of size x + y is created, which can be merged further with other files.Return the minimum total cost required to merge all the files.Note: It is guaranteed that the minimum total computation cost fits within a 32-bit signed integer.Examples:Input: files[] = [3, 2, 4]Output: 14

#### Examples

##### Example 1

- **Explanation:** There are different ways to combine these files. Optimal method is given below:

##### Example 2

- **Input:**
```text
files[] = [2, 3, 6, 5, 7, 4]Output: 68Explanation: There are different ways to combine these files. Optimal method is given below:
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-29 22:56:12
- **Status:** Correct
- **Marks:** 4

```python
import heapq
class Solution:
    def minComputation(self, files):
        # code here
        pq = files[:]
        heapq.heapify(pq)
        res = 0
        while len(pq) > 1:
            a = heapq.heappop(pq)
            b = heapq.heappop(pq)
            res += a+b
            heapq.heappush(pq,a+b)
        return res
```

*Generated on: 29/10/2026, 22:56:12*