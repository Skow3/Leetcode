# EASY
1304

```PYTHON
class Solution:
    def sumZero(self, n):
        result = [0] * n
        start = 1
        i = 0
        while i + 1 < n:
            result[i] = start
            result[i+1] = -start
            i += 2
            start += 1
        return result
```
