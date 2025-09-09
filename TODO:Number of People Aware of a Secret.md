# MEDIUM
2327

will do all the approaches later on after this hackathon
```python
class Solution:
    MOD = 10**9 + 7

    def peopleAwareOfSecret(self, n, delay, forget):
        t = [0] * (n + 1)  

        t[1] = 1
        count = 0

        for day in range(2, n + 1):
            if day - delay > 0:
                count = (count + t[day - delay]) % self.MOD
            if day - forget > 0:
                count = (count - t[day - forget] + self.MOD) % self.MOD
            t[day] = count 

        result = 0
        for day in range(n - forget + 1, n + 1):
            if day > 0:
                result = (result + t[day]) % self.MOD

        return result

```
