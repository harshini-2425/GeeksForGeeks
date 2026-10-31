## 01. First Repeating Element

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/first-repeating-element4018/1)

### Problem Description

**Task:** Given an array arr[], find the first repeating element position. The element should occur more than once and the position (from left) of its first occurrence should be the smallest.Note: The position you return should be according to 1-based indexing. Examples:Input: arr[] = [1, 5, 3, 4, 3, 5, 6]

#### Examples

##### Example 1

- **Output:**
```text
-1
```
- **Explanation:** All elements appear only once so answer is -1.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (2)

#### Solution 1 (Python)

- **Submitted:** 2026-10-31 17:21:40
- **Status:** Correct
- **Marks:** 0

```python
class Solution:
    def firstRepeated(self, arr):
        # code here 
        freq = {}
        minfirst = float('inf')
        for i,num in enumerate(arr):
            if num in freq:
                minfirst = min(minfirst,freq[num])
            else:
                freq[num] = i
        return minfirst+1 if minfirst != float('inf') else -1
```

#### Solution 2 (Python)

- **Submitted:** 2025-12-02 23:13:32
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def firstRepeated(self,arr):
        # code here 
        freq = {}
        minfirst = float('inf')
        for i,val in enumerate(arr):
            if val in freq:
                minfirst = min(minfirst,freq[val])
            else:
                freq[val] = i
        return minfirst+1 if minfirst != float('inf') else -1
```

*Generated on: 31/10/2026, 17:21:41*