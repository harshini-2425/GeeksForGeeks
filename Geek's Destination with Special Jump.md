## 01. Geek's Destination with Special Jump

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/geek-and-her-destination--145724/1)

### Problem Description

**Task:** Geek starts at position 0 on the positive X-axis and needs to reach or pass position d on the positive X-axis. Geek normally follows a repeating movement pattern:Move forward by a units, taking a seconds.Move backward by b units, taking b seconds.Geek also has a special jump that moves him exactly j units forward in 1 second. He can use it at any time, even in the middle of a forward or backward movement, and the journey ends immediately after the jump.Given five integers a, b, d, l, and r. For every integer j in the range [l, r], find the minimum time required for Geek to reach or pass position d. He may either use the special jump or reach the destination using normal movement alone, whichever takes less time.Return the sum of the minimum times for all jump lengths from l to r. Since, the answer can be large, return modulo 10⁹ + 7. Note: Each jump length is considered independently.Examples:Input: a = 2, b = 1, d = 5, l = 3, r = 4Output: 5Explanation: For j = 3, Geek moves 2 units forward, then takes a jump of 3 units to reach the destination. The minimum time required is 3 seconds.For j = 4, Geek moves 1 unit forward, then takes a jump of 4 units to reach the destination. The minimum time required is 2 seconds.Total sum for the range [l, r] = 3 + 2 = 5.Input: a = 4, b = 2, d = 8, l = 2, r = 4Output: 26Explanation:For j = 2, Geek moves 4 units forward, then 2 units backward. She then moves 4 units forward again and takes a jump of 2 units to reach the destination. The minimum time required is 11 seconds.For j = 3, Geek moves 4 units forward, then 2 units backward. She then moves 3 units forward and takes a jump of 3 units to reach the destination. The minimum time required is 10 seconds.For j = 4, Geek moves 4 units forward, then takes a jump of 4 units to reach the destination. The minimum time required is 5 seconds.Total sum for the range [l, r] = 11 + 10 + 5 = 26.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(1)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-11-25 23:35:18
- **Status:** Correct
- **Marks:** 8

```python
class Solution:
    def solve(self,a,b,c,d):
        remaining = d-c
        if remaining <= 0:
            return 1
        if remaining <= a:
            return remaining+1
        net = a-b
        distance = remaining-a
        cycles = (distance+net-1)//net
        return remaining+2*b*cycles+1
    def summ(self,a,b,t):
        MOD = 1000000007
        first = a+2
        cycleTime = a+b
        if t < first:
            return 0
        count = (t-first)//cycleTime+1
        last = first+(count-1)*cycleTime
        term1 = (b%MOD)*(count%MOD)%MOD
        term1 = term1*((first+last)%MOD)%MOD
        term2 = (count%MOD)*(2*b-1)%MOD
        term2 = term2*(2*b)%MOD
        term2 = term2*((MOD+1)//2)%MOD
        return (term1+term2)%MOD
    def prefix(self,a,b,t):
        MOD = 1000000007
        total = (t%MOD)*((t+1)%MOD)%MOD
        total = total*((MOD+1)//2)%MOD
        return (total-self.summ(a,b,t)+MOD)%MOD
    def minTime(self, a: int, b: int, d: int, l: int, r: int) -> int:
        # code here
        MOD = 1000000007
        t1 = self.solve(a,b,l,d)
        t2 = self.solve(a,b,r+1,d)
        return (self.prefix(a,b,t1)-self.prefix(a,b,t2)+MOD)%MOD
```

*Generated on: 25/11/2026, 23:35:28*