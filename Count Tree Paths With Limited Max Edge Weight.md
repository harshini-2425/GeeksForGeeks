## 01. Count Tree Paths With Limited Max Edge Weight

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/possible-paths--141628/1)

### Problem Description

**Task:** Given a weighted tree with n nodes, numbered from 1 to n and n - 1 edges, where each edge is represented as [u, v, w] indicating an edge between nodes u and v with weight w.You are also given an array queries[], where each queries[i] represents a maximum allowed edge weight.For each query x, find the number of distinct paths in the tree such that the maximum edge weight along the path is less than or equal to x.Return an array containing the number of valid paths for each query.Note: A path from node u to node v and the path from node v to node u are considered the same path. A path must contain at least one edge. A path from a node to itself is not considered.Examples:Input: n = 3, edges[][] = [[1, 2, 1], [2, 3, 4]], queries[] = [3]

#### Examples

##### Example 1

- **Output:**
```text
[1, 3, 4]
```
- **Explanation:** For x = 1, only the edge [2, 3, 1] satisfies the condition. Therefore, the only valid path is 2 - > 3, giving an answer of 1. For x = 3, the edges [2, 3, 1] and [1, 2, 3] can be used. They form three valid paths: 1 - > 2, 2 - > 3, and 1 - > 3. For x = 5, the edges with weights 1, 3, and 4 can be used. They form four valid paths: 1 - > 2, 2 - > 3, 1 - > 3, and 5 - > 7.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(nlogn + qlogn)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-11-03 22:43:12
- **Status:** Correct
- **Marks:** 8

```python
from bisect import bisect_right
class Solution:
    def root(self,x,parent):
        while parent[x] != x:
            parent[x] = parent[parent[x]]
            x = parent[x]
        return x
    def union(self,a,b,parent,sz,ans):
        ra = self.root(a,parent)
        rb = self.root(b,parent)
        if ra == rb:
            return ans
        if sz[ra] < sz[rb]:
            ra,rb = rb,ra
        ans += sz[ra]*sz[rb]
        parent[rb] = ra
        sz[ra] += sz[rb]
        return ans
    def maximumWeight(self, n, edges, queries):
        # code here
        ans = 0
        parent = list(range(n+1))
        sz = [1]*(n+1)
        wt = []
        for e in edges:
            wt.append((e[2],e[0],e[1]))
        wt.sort()
        mp = {}
        i = 0
        while i < len(wt):
            weight = wt[i][0]
            while i < len(wt) and wt[i][0] == weight:
                u = wt[i][1]
                v = wt[i][2]
                ans = self.union(u,v,parent,sz,ans)
                i += 1
            mp[weight] = ans
        weights = sorted(mp.keys())
        res = []
        for x in queries:
            pos = bisect_right(weights,x)
            if pos == 0:
                res.append(0)
            else:
                res.append(mp[weights[pos-1]])
        return res
```

*Generated on: 03/11/2026, 22:43:12*