# EASY 
326

As always an i'm able to move an easy question easily but since now i have a lot vast knowledge rather than going for a soft try and touch i just go for some unique out
of the world approach.

# FINAL CODE 
```python
class Solution(object):
    def isPowerOfThreenew(self, n):
        """
        :type n: int
        :rtype: bool
        """
        if n==0:
            return False
        while n%3 ==0:
            n=n/3
        if int(n)==1:
            return True
        return False
```

I was trying to submit but was stuck with the TLE .
Then saw that i forgot to handle the 0 as a test case.

# GOOD APPROACH
```python
class Solution(object):
    def isPowerOfThree(self, n):
        """
        :type n: int
        :rtype: bool
        """
        if n<=0:
            return False
        # eliminating the looping and just stating one modulo 
        # Here i'm using 3^19 because we know that our constraints is n< 2^31 -1 and the last power of 3 which is less than 2^31 is 19
        if 1162261467%n ==0:
            return True
        return False
```
* Eliminating the looping and just stating one modulo 
* Here i'm using 3<sup>19</sup> because we know that our constraints is n< 2<sup>31</sup> -1 and the last power of 3 which is less than 2<sup>31</sup> is 19

> 1162261467
