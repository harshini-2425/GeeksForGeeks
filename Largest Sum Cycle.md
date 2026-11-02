## 01. Largest Sum Cycle

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/largest-sum-cycle--170645/1)

### Problem Description

**Task:** Given an array edge[] of size n, there are n cells numbered from 0 to n - 1. Each cell has at most one outgoing edge.For every cell i:edge[i] is the cell reached from i in one step.edge[i] = -1 means that cell i has no outgoing edge.A cycle is a sequence of cells where, by following the outgoing edges, we eventually return to the starting cell. The sum of a cycle is the sum of the indices of all cells in that cycle.Return the maximum cycle sum. If there is no cycle, return -1.Examples:Input: edge[] = [1, 2, 0, -1]Output: 3Explanation: There is only one cycle in the graph i.e. 0 - > 1 - > 2 - > 0. Sum of the cell index in that cycle = 0 + 1 + 2 = 3.Input: edge[] = [2, 0, -1, 2]Output: -1Explanation: There is no cycle in the graph. The edges are 1 - > 0 - > 2 < - 3. Hence, 2 has no outgoing edge, so no cycle exists.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-11-02 21:24:30
- **Status:** Correct
- **Marks:** 8

```python
from collections import deque
class Solution:
    def largestSumCycle(self, edge):
        # code here
        n = len(edge)
        indegree = [0]*n
        for i in range(n):
            if edge[i] != -1:
                indegree[edge[i]] += 1
        q = deque()
        for i in range(n):
            if indegree[i] == 0:
                q.append(i)
        while q:
            node = q.popleft()
            next_node = edge[node]
            if next_node != -1:
                indegree[next_node] -= 1
                if indegree[next_node] == 0:
                    q.append(next_node)
        ans = -1
        visited = [0]*n
        for i in range(n):
            if indegree[i] > 0 and visited[i] == 0:
                total = 0
                node = i
                while visited[node] == 0:
                    visited[node] = 1
                    total += node
                    node = edge[node]
                ans = max(ans,total)
        return ans
```

*Generated on: 02/11/2026, 21:24:35*