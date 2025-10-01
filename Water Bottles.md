# EASY 
1518

# FIRST SOLUTION :
```python
class Solution(object):
    def numWaterBottles(self, numBottles, numExchange):
        """
        :type numBottles: int
        :type numExchange: int
        :rtype: int
        """
        ans = numBottles
        while numBottles>1:
            numBottles = numBottles/numExchange
            ans+= numBottles
        return int(ans)
```

I tried running and submitting this in leetcode [Python] but it was giving wrong output for (15,4) --> 18 in leetcode but for VSCODE It was giving 19

So after checking again and again i got to know that it is because of the version compatiblity and not the code 

The code which i wrote above was compatible for Python3 so what to do for Python?

# Python Solution:
```python
class solution(object):
    def numWaterBottles(self, numBottles, numExchange):
        """
        :type numBottles: int
        :type numExchange: int
        :rtype: int
        """
        ans = numBottles
        while numBottles >= numExchange:
            newBottles = numBottles // numExchange
            ans += newBottles
            numBottles = newBottles + (numBottles % numExchange)
        return ans
```

SO using // and modulus will solve that

# Difference between / and // in older versions?
### #
Python 2:

* If both operands are integers → does integer division (truncates result).
* If at least one operand is float → does true division (float result).

Python 3:

* / always means true division (returns a float).

