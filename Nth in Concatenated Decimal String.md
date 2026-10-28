## 01. Nth in Concatenated Decimal String

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/nth-character-in-concatenated-decimal-string0245/1)

### Problem Description

**Task:** Consider a string s formed by concatenating the decimal representations of all positive integers in order:s = "12345678910111213141516171819202122232425262728293031..."Given an integer n, find the nth character (1-based indexing) in the string s.Examples:Input: n = 10

#### Examples

##### Example 1

- **Output:**
```text
'0'
```
- **Explanation:** The 11th character in "12345678910.." is '0'.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(log n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-28 22:34:08
- **Status:** Correct
- **Marks:** 4

```python
class Solution:

    def nthCharacter(self, n):
        # code here
        len = 1
        count = 9
        start = 1
        while n > len*count:
            n -= len*count
            len += 1
            count *= 10
            start *= 10
        number = start + (n-1)//len
        digitIndex = (n-1)%len
        divisor = 1
        for i in range(len-digitIndex-1):
            divisor *= 10
        digit = (number//divisor)%10
        return chr(ord('0')+digit)
```

*Generated on: 28/10/2026, 22:34:08*