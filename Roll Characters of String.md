## 01. Roll Characters of String

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/roll-the-characters-of-a-string2127/1)

### Problem Description

**Task:** Given a string s consisting of lowercase English letters and an integer array roll[], perform a sequence of roll operations on the string. For each value roll[i], increment each of the first roll[i] characters of the string by 1 in the English alphabet. After 'z', the character wraps around to 'a'.Return the final string after applying all roll operations.Note: A roll operation affects the current state of the string, including all previous modifications.Examples:Input: s = "bca", roll[] = [1, 2, 3]

#### Examples

##### Example 1

- **Output:**
```text
debbExplanation: Initially, s = "zcza". Roll first 1 character: "zcza" - > "acza" Roll first 1 character again: "acza" - > "bcza" Roll first 3 characters: "bcza" - > "cdaa" Roll first 4 characters: "cdaa" - > "debb" Therefore, the final string is "debb".
```
- **Explanation:** Initially, s = "bca" roll[0] = 1: Roll the first 1 character. "bca" - > "cca" roll[1] = 2: Roll the first 2 characters. "cca"- > "dda" roll[2] = 3: Roll the first 3 characters. "dda" - > "eeb" After applying all the roll operations, the final string is "eeb".Input: s = "zcza", roll[] = [1, 1, 3, 4]

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-10-14 23:49:10
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def findRollOut(self, s, roll):
        # code her
        n = len(s)
        m = len(roll)
        diff = [0]*(n+1)
        for i in range(m):
            diff[0]+=1
            if roll[i]<n:
                diff[roll[i]] -= 1
        for i in range(1,n):
            diff[i] += diff[i-1]
        s = list(s)
        for i in range(n):
            shift = diff[i]%26
            s[i] = chr(ord('a')+(ord(s[i])-ord('a')+shift)%26)
        return ''.join(s)
```

*Generated on: 14/10/2026, 23:49:19*