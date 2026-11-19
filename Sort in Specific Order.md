## 01. Sort in Specific Order

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/sort-in-specific-order2422/1)

### Problem Description

**Task:** Given an array arr[] of non-negative integers. Your need to sort them so that The first part of the array contains odd numbers sorted in descending order.The rest of the portion contains even numbers sorted in ascending order.Examples:Input: arr[] = [1, 2, 3, 5, 4, 7, 10]

#### Examples

##### Example 1

- **Output:**
```text
[7, 5, 3, 1, 0, 2, 4]Explanation: 7, 5, 3, 1 are odd numbers in descending order and 0, 2, 4 are even numbers in ascending order.
```
- **Explanation:** 7, 5, 3, 1 are odd numbers in descending order and 2, 4, 10 are even numbers in ascending order.Input: arr[] = [0, 4, 5, 3, 7, 2, 1]

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (Python)

- **Submitted:** 2026-11-19 23:16:16
- **Status:** Correct
- **Marks:** 0

```python
from functools import cmp_to_key
class Solution:
    def sortIt(self, arr):
        # code here
        def compare(a,b):
            if a%2 == 0 and b%2 ==0:
                return a-b
            if a%2 != 0 and b%2 != 0:
                return b-a
            return -1 if a%2 != 0 else 1
        arr.sort(key=cmp_to_key(compare))
```

#### Solution 2 (Python)

- **Submitted:** 2026-06-08 14:30:36
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def sortIt(self, arr):
        # code here
        odd = []
        even = []
        for num in arr:
            if num%2 != 0:
                odd.append(num)
            else:
                even.append(num)
        odd.sort(reverse=True)
        even.sort()
        i = 0
        while i < len(odd):
            arr[i] = odd[i]
            i += 1
        j = 0
        while j < len(even) and i < len(arr):
            arr[i] = even[j]
            j += 1
            i += 1
        return arr
```

*Generated on: 19/11/2026, 23:16:47*