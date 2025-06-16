# EASY
338
Got to know some great DP trick doing this problem.

---

#### My approach using the bifs in python

```python
class Solution(object):
    def countBits(self, n):
        """
        :type n: int
        :rtype: List[int]
        """
        ans = []
        for i in range(0,n+1):
            ans.append(bin(i)[2:].count('1'))
        return ans
```

---

This approach used less memory in comparison to the next approach though the TOC here is more than the next logical operator based
approach.

### MAIN APPROACH LEARNT 

* Here we'll calculate the number of 1's in the binary representation using the earlier calculated values i.e

* For example for 2{10} it is [1] but for 5{101} it is Number of ones in 2 + '1'

---

# CODE :
```python
class Solution(object):
    def countBits(self, n):
        """
        :type n: int
        :rtype: List[int]
        """
        ans = [0] * (n + 1)
        for i in range(1, n + 1):
            ans[i] = ans[i >> 1] + (i & 1)
        return ans
```

---
