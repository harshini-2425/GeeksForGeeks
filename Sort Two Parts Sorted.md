## 01. Sort Two Parts Sorted

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/sort-the-half-sorted2157/1)

### Problem Description

**Task:** Given an integer array arr[] where the two parts around a break point are individually sorted, merge them into a single sorted array. The break point can be anywhere in the array, including at the beginning or end.Examples:Input: arr[] = [2, 3, 8, -1, 7, 10]

#### Examples

##### Example 1

- **Output:**
```text
[10, 20, 30]
```
- **Explanation:** One part is empty and the other part is whole array which is already sorted.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-11 22:34:56
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def mergeTwoParts(self, arr):
        # code here
        n = len(arr)
        index = 0
        temp = [0]*n
        for i in range(n-1):
            if arr[i] > arr[i+1]:
                index = i+1
                break
        if index == 0:
            return
        i,j,k = 0,index,0
        while i < index and j < n:
            if arr[i] < arr[j]:
                temp[k] = arr[i]
                i += 1
            else:
                temp[k] = arr[j]
                j += 1
            k += 1
        while i < index:
            temp[k] = arr[i]
            i += 1
            k += 1
        while j < n:
            temp[k] = arr[j]
            j += 1
            k += 1
        for i in range(n):
            arr[i] = temp[i]
```

*Generated on: 11/10/2026, 22:35:09*