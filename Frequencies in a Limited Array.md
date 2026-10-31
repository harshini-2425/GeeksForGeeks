## 01. Frequencies in a Limited Array

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/frequency-of-array-elements-1587115620/1)

### Problem Description

**Task:** Given an array arr[] containing positive integers. The elements in the array arr[] range from 1 to n (where n is the size of the array), and some numbers may be repeated or absent. Your have to count the frequency of all numbers in the range 1 to n and return an array of size n such that result[i] represents the frequency of the number i (1-based indexing).Examples:Input: arr[] = [2, 3, 2, 3, 5]

#### Examples

##### Example 1

- **Output:**
```text
[1]
```
- **Explanation:** We have: 1 occurring 1 time, and there are no other numbers between 1 and the size of the array.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (3)

#### Solution 1 (Python)

- **Submitted:** 2026-10-31 17:09:35
- **Status:** Correct
- **Marks:** 0

```python
class Solution:
    def frequencyCount(self, arr):
        #  code here
        n = len(arr)
        res = [0]*n
        for num in arr:
            res[num-1] += 1
        return res
```

#### Solution 2 (Python)

- **Submitted:** 2025-12-02 00:12:18
- **Status:** Correct
- **Marks:** 0

```python
class Solution:
    def frequencyCount(self, arr):
        #  code here
        n = len(arr)
        result = [0]*n
        for num in arr:
            result[num-1] += 1
        return result
```

#### Solution 3 (Python)

- **Submitted:** 2025-12-02 00:08:34
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def frequencyCount(self, arr):
        #  code here
        arr.sort()
        n = len(arr)
        result = [0]*n
        for num in arr:
            result[num-1] += 1
        return result
```

*Generated on: 31/10/2026, 17:09:37*