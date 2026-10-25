## 01. Sum of Beauty of All Substrings

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/sum-of-beauty-of-all-substrings-1662962118/1)

### Problem Description

**Task:** Given a string s, return the sum of the beauty of all substrings of s. The beauty of a substring is defined as the difference between the maximum and minimum frequencies of the characters present in that substring.Examples:Input: s = "aaac"Output: 3Explanation: The substrings with non-zero beauty are "aaac" and "aac". For "aaac", the frequencies are a = 3 and c = 1. Its beauty is 3 − 1 = 2. For "aac", the frequencies are a = 2 and c = 1. Its beauty is 2 − 1 = 1. The remaining substrings have a beauty of 0. Therefore, the sum of the beauties of all substrings is 2 + 1 = 3.Input: s = "aabc"Output: 2Explanation: The substrings with non-zero beauty are "aab" and "aabc". For "aab", the frequencies are a = 2 and b = 1. Its beauty is 2 − 1 = 1. For "aabc", the frequencies are a = 2, b = 1, and c = 1. Its beauty is 2 − 1 = 1. Therefore, the sum of the beauties of all substrings is 1 + 1 = 2.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(|s| * |s|)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-25 23:06:16
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def beautySum(self, s: str) -> int:
        # code here
        ans = 0
        for i in range(len(s)):
            cnt = [0]*26
            max_f = 0
            for j in range(i,len(s)):
                idx = ord(s[j])-97
                cnt[idx] += 1
                max_f = max(max_f,cnt[idx])
                min_f = len(s)+1
                for freq in cnt:
                    if freq > 0:
                        min_f = min(min_f,freq)
                ans += max_f-min_f
        return ans
```

*Generated on: 25/10/2026, 23:06:40*