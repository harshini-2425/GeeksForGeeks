## 01. Number of submatrix have sum X

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/number-of-submatrix-have-sum-k/1)

### Problem Description

**Task:** Given a matrix mat[][] of size n × m and an integer x, find the number of square submatrices whose sum of elements is equal to x.

#### Examples

##### Example 1

- **Input:**
```text
mat[][] = [[2, 4, 7, 8, 10], [3, 1, 1, 1, 1], [9, 11, 1, 2, 1], [12, -17, 1, 1, 1]] , x = 10Output: 3Explanation: The sub-squares whose sum of elements = 10, are colored in the matrix.
```

##### Example 2

- **Input:**
```text
mat[][] = [[3, 3, 5, 3], [2, 2, 2, 6], [11, 2, 2, 4]] ,x = 1Output: 0Explanation: There is no sub-squares whose sum of elements is 1.
```

#### Constraints

- **1.** `1 ≤ n, m ≤ 100-10³ ≤ mat[i] ≤ 10³-10⁹ ≤ x ≤ 10⁹`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n*m*min(n,m))
- **Expected Auxiliary Space Complexity:** O(n*m)

### Accepted Solutions (2)

#### Solution 1 (Python)

- **Submitted:** 2026-10-23 10:35:08
- **Status:** Correct
- **Marks:** 0

```python
class Solution:
    def countSquare(self, mat, x):
        # code here
        n,m = len(mat),len(mat[0])
        prefix = [[0]*(m+1) for _ in range(n+1)]
        for i in range(n):
            for j in range(m):
                prefix[i+1][j+1] = (mat[i][j]+prefix[i][j+1]+prefix[i+1][j]-prefix[i][j])
        ans = 0
        for size in range(1,min(n,m)+1):
            for i in range(n-size+1):
                for j in range(m-size+1):
                    r2,c2 = i+size,j+size
                    total = (prefix[r2][c2]-prefix[i][c2]-prefix[r2][j] + prefix[i][j])
                    if total == x:
                        ans += 1
        return ans
```

#### Solution 2 (Python)

- **Submitted:** 2025-11-20 09:53:43
- **Status:** Correct
- **Marks:** 8

```python
class Solution:
    def countSquare(self, mat, x):
        # code here
        n = len(mat)
        m = len(mat[0])
        pre = [[0]*m for _ in range(n)]
        for i in range(n):
            for j in range(m):
                pre[i][j] = mat[i][j]
                if i>0:
                    pre[i][j] += pre[i-1][j]
                if j>0:
                    pre[i][j] += pre[i][j-1]
                if i>0 and j>0:
                    pre[i][j] -= pre[i-1][j-1]
        
        count = 0
        max_k = min(n,m)
        for k in range(1,max_k+1):
            for i in range(n-k+1):
                for j in range(m-k+1):
                    r1,c1 = i,j
                    r2,c2 = i+k-1,j+k-1
                    
                    total = pre[r2][c2]
                    if r1>0:
                        total -= pre[r1-1][c2]
                    if c1>0:
                        total -= pre[r2][c1-1]
                    if r1>0 and c1>0:
                        total += pre[r1-1][c1-1]
                    if total == x:
                        count += 1
        return count
```

*Generated on: 23/10/2026, 10:35:20*