# MEDIUM
837
Google ..

# CONCEPT OF PROBABLITY 
```python
class Solution(object):
    def new21Game(self, n, k, maxPts):
        """
        :type n: int
        :type k: int
        :type maxPts: int
        :rtype: float
        """
        P = [0.0] * (n + 1)  # P[i] = probability of getting score = i
        P[0] = 1.0  # already at score 0 with probability 1
        
        currProbabSum = 1.0 if k > 0 else 0.0
        
        for i in range(1, n + 1):
            P[i] = currProbabSum / maxPts
            
            if i < k:
                currProbabSum += P[i]
            
            if i - maxPts >= 0 and i - maxPts < k:
                currProbabSum -= P[i - maxPts]
        
        return sum(P[k:])

```

> WILL EXPLAIN TOMORRROW
