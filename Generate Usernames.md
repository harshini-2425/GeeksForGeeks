## 01. Generate Usernames

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/new-registration-system--150419/1)

### Problem Description

**Task:** Given an array of strings arr[]. The array represents first names of users, generate a unique username for each entry in the order it appears.Initially, consider all usernames present in the input array as reserved.If a username has not already been assigned to any previous user, keep it unchanged.Otherwise, append the smallest positive integer suffix that produces a username that has not been reserved or assigned to any previous user.Return the array of generated usernames.Examples:Input: arr[] = ["aba", "ab", "aba", "aba", "ab"]Output: ["aba", "ab", "aba1", "aba2", "ab1"]Explanation: The first occurrences of "aba" and "ab" are new, so they remain unchanged. The next "aba" is already used, so "aba1" is assigned. When "aba" appears again, "aba1" is already used, so "aba2" is assigned. Similarly, the second occurrence of "ab" becomes "ab1".Input: arr[] = ["a", "a", "a1", "a"]

#### Examples

##### Example 1

- **Output:**
```text
["aba1", "aba", "aba2"]
```
- **Explanation:** Initially, "aba1" and "aba" are reserved. The first occurrence of each retains its original name. For the second occurrence of "aba", "aba1" is already reserved, so "aba2" is assigned.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n * m)
- **Expected Auxiliary Space Complexity:** O(n * m)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-11-07 22:18:12
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def generateUsernames(self, arr: list[str]) -> list[str]:
        # code here
        res = []
        used = set(arr)
        nextSuffix = {}
        processed = set()
        for s in arr:
            if s not in processed:
                processed.add(s)
                res.append(s)
                nextSuffix[s] =1
            else:
                suffix = nextSuffix[s]
                name = s+str(suffix)
                while name in used:
                    suffix += 1
                    name = s+str(suffix)
                used.add(name)
                res.append(name)
                nextSuffix[s] = suffix+1
        return res
```

*Generated on: 07/11/2026, 22:18:02*