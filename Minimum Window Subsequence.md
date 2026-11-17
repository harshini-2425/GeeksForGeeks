## 01. Minimum Window Subsequence

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/minimum-window-subsequence/1)

### Problem Description

**Task:** You are given two strings, s1 and s2. Your task is to find the smallest substring in s1 such that s2 appears as a subsequence within that substring.The characters of s2 must appear in the same sequence within the substring of s1.If there are multiple valid substrings of the same minimum length, return the one that appears first in s1.If no such substring exists, return an empty string.Note: Both the strings contain only lowercase english letters.Examples:Input: s1 = "geeksforgeeks", s2 = "eksrg"

#### Examples

##### Example 1

- **Output:**
```text
"eksforg"
```
- **Explanation:** "eksforg" satisfies all required conditions. s2 is its subsequence and it is smallest and leftmost among all possible valid substrings of s1.

##### Example 2

- **Input:**
```text
s1 = "abcdebdde", s2 = "bde" Output: "bcde"Explanation: "bcde" and "bdde" are two substring of s1 where s2 occurs as subsequence but "bcde" occur first so we return that.Input: s1 = "ad", s2 = "b" Output: ""Explanation: There is no substring exists.
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n * m)
- **Expected Auxiliary Space Complexity:** O(n * m)

### Accepted Solutions (2)

#### Solution 1 (Python)

- **Submitted:** 2026-11-17 12:03:18
- **Status:** Correct
- **Marks:** 0

```python
class Solution:
    def minWindow(self, s1, s2):
        # Code here
        n = len(s1)
        m = len(s2)
        ans =""
        minLen = float('inf')
        for i in range(len(s1)):
            if s1[i] == s2[0]:
                p1,p2 = i,0
                while p1 < n and p2<m:
                    if s1[p1] == s2[p2]:
                        p2 += 1
                    p1+=1
                if p2 == m:
                    end = p1-1
                    p2 = m-1
                    
                    while end > i:
                        if s1[end] == s2[p2]:
                            p2 -= 1
                        if p2 < 0:
                            break
                        end -= 1
                    start = end
                    length = p1-end
                    if length < minLen:
                        minLen = length
                        ans = s1[start:start+length]
        return ans
```

#### Solution 2 (Python)

- **Submitted:** 2026-01-31 23:14:26
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def minWindow(self, s1, s2):
        # Code here
        n = len(s1)
        m = len(s2)
        ans =""
        minLen = float('inf')
        for i in range(len(s1)):
            if s1[i] == s2[0]:
                p1,p2 = i,0
                while p1 < n and p2<m:
                    if s1[p1] == s2[p2]:
                        p2 += 1
                    p1+=1
                if p2 == m:
                    end = p1-1
                    p2 = m-1
                    
                    while end > i:
                        if s1[end] == s2[p2]:
                            p2 -= 1
                        if p2 < 0:
                            break
                        end -= 1
                    start = end
                    length = p1-end
                    if length < minLen:
                        minLen = length
                        ans = s1[start:start+length]
        return ans
```

*Generated on: 17/11/2026, 12:03:22*