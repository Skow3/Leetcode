# EASY
1925

```python
class Solution(object):
    def countTriples(self, n):
        """
        :type n: int
        :rtype: int
        """
        squares = {i * i for i in range(1, n + 1)}
        count = 0
        for a in range(1, n + 1):
            for b in range(1, n + 1):
                s = a * a + b * b
                if s in squares:
                    count += 1
                    
        return count
```
