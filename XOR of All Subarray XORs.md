## 01. XOR of All Subarray XORs

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/game-of-xor1541/1)

### Problem Description

**Task:** Given an integer array arr[], find the XOR of the XOR values of all possible non-empty subarrays of the array.Examples:Input: arr[] = [1, 2, 3]

#### Examples

##### Example 1

- **Output:**
```text
2 xor[1] = 1 xor[1, 2] = 3 xor[2, 3] = 1 xor[1, 2, 3] = 0 xor[2] = 2 xor[3] = 3 Result: 1 ^ 3 ^ 1 ^ 0 ^ 2 ^ 3 = 2
```

##### Example 2

- **Input:**
```text
arr[] = [1, 2]
```
- **Output:**
```text
0 xor[1] = 1 xor[1, 2] = 3 xor[2] = 2 Result: 1 ^ 3 ^ 2 = 0
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-11-04 23:13:35
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def subarrayXor(self, arr):
        # code here 
        result = 0
        n = len(arr)
        for i in range(n):
            if (i+1)%2 != 0 and (n-i)%2 != 0:
                result ^= arr[i]
        return result
```

*Generated on: 04/11/2026, 23:14:00*