# EASY
367

The saying is correct the more questions and solutions we do the more complexity increases.
I was thinking of approaches like:
1. Checking for some similarity in binary
2. Revising all the formulas in mind
3. Thinking about LCM

But the solution simply lied in doing the sqrt of the number i.e A**0.5 and the raising it to power 2
Since this should bring A if the number is a perfect sqrt. So yeah here is the solution:

# CODE:
```PYTHON
class Solution(object):
    def isPerfectSquare(self, num):
        """
        :type num: int
        :rtype: bool
        """
        return int(num**0.5) ** 2 == num if num >= 0 else False
```

#### TOC  : 0ms (100%)
---

# THINGS I LEARNT
1. Always try for the easiest approach first because we don't know wether we can optimize it or not
