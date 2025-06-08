# MEDIUM

MY APPROACH BRUTE FORCE 

```python
class Solution(object):
    def lexicalOrder(self, n):
        """
        :type n: int
        :rtype: List[int]
        """
        s = []
        for i in range(n):
            s.append(i+1)

        for i in range(n):
            s[i] = str(s[i])
        
        s = sorted(s)
        for i in range(n):
            s[i] = int(s[i])
        
        return s
```

APP. TIME COMPLEXITY = O(Nlog^2N)


---
Will do this with another approach on 11th June 
