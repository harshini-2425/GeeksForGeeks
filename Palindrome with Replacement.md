## 01. Palindrome with Replacement

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/palindrome-with-minimum-sum--170648/1)

### Problem Description

**Task:** Given a string s consisting of lowercase English letters and the character '?',
Replace every '?' with a lowercase English letter such that the resulting string is a palindrome.
If it is possible to form a palindrome, return the minimum possible sum of the absolute ASCII differences between every pair of adjacent characters in the resulting string.
If it is not possible to form a palindrome, return -1.

#### Examples

##### Example 1

- **Input:**
```text
s = a???c??c????
```
- **Output:**
```text
4
```
- **Explanation:** One optimal palindrome is "abbbccccbbba". The sum of the absolute ASCII differences between adjacent characters is 1 + 0 + 0 + 1 + 0 + 0 + 0 + 1 + 0 + 0 + 1 = 4, which is the minimum possible.

##### Example 2

- **Input:**
```text
s = a???c??c???c
```
- **Output:**
```text
-1
```
- **Explanation:** It is not possible to replace the '?' characters to make the string a palindrome because the first and last characters are different and cannot be changed.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-22 21:51:14
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def minimumSum(self, s: str) -> int:
        # code here
        if not self.isPossible(s):
            return -1
        n = len(s)
        s = list(s)
        for i in range(n//2):
            if s[i] == '?' and s[n-i-1] != '?':
                s[i] = s[n-i-1]
            elif s[i] != '?' and s[n-i-1] =='?':
                s[n-i-1] = s[i]
        st = []
        i = 0
        while i < n:
            if s[i] != '?':
                st.append(s[i])
                i += 1
            else:
                if st:
                    while i<n and s[i] == '?':
                        s[i] = st[-1]
                        i += 1
                else:
                    i += 1
        st.clear()
        i = n-1
        while i>=0:
            if s[i] != '?':
                st.append(s[i])
                i -= 1
            else:
                if st:
                    while i>=0 and s[i] == '?':
                        s[i] = st[-1]
                        i -= 1
                    st.pop()
                else:
                    i -= 1
        for i in range(n):
            if s[i] == '?':
                s[i] = 'a'
        res = 0
        for i in range(n-1):
            res += abs(ord(s[i]) - ord('a')-(ord(s[i+1]) - ord('a')))
        return res
    def isPossible(self,s):
        n = len(s)
        for i in range(n//2):
            if s[i] != '?' and s[n-i-1] != '?' and s[i] != s[n-i-1]:
                return False
        return True
```

*Generated on: 22/10/2026, 21:53:24*