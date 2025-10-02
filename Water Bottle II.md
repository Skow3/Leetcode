# MEDIUM
3100

# FIRST SOLUTION:
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
