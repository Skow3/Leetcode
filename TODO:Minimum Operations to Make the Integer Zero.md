# MEDIUM
2749

# WILL DO ON SUNDAY
```python
class Solution:
    def makeTheIntegerZero(self, num1, num2):
        for t in range(1, 37):  # looping from 1 to 36 inclusive
            val = num1 - t * num2

            if val < 0:
                return -1
            if bin(val).count("1") <= t and t <= val:
                return t

        return -1
```
