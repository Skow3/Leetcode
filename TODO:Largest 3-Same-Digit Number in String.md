# EASY
2264
```python
class Solution:
    def largestGoodInteger(self, num):
        max_char = ' '  # placeholder for no match yet
        
        for i in range(2, len(num)):
            if num[i] == num[i - 1] == num[i - 2]:
                if max_char == ' ' or num[i] > max_char:
                    max_char = num[i]
        
        return "" if max_char == ' ' else max_char * 3
```
