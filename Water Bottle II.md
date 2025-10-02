# MEDIUM
3100

# FIRST SOLUTION:
```python
class Solution(object):
    def maxBottlesDrunk(self, numBottles, numExchange):
        """
        :type numBottles: int
        :type numExchange: int
        :rtype: int
        """
        ans=numBottles
        numfill = 0
        while True:
            if numExchange <= numBottles:
                numBottles = numBottles - numExchange
                numfill+=1
                numExchange+=1       
            else:
                if numfill>0:
                    numBottles+=1
                    numfill-=1
                    ans+=1
                else:
                    break
        return ans
```



# SECOND SOLUTION:
```python
class Solution:
    def maxBottlesDrunk(self, numBottles: int, numExchange: int) -> int:
        numdrunk = numBottles
        numempty = numBottles
        
        while numempty >= numExchange:
            numempty -= numExchange
            numExchange += 1
            numdrunk += 1
            numempty += 1
            
        return numdrunk
```
