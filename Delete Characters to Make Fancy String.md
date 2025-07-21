# EASY 

# FINAL SOLUTION:
```python
class Solution:
    def makeFancyString(self, s: str) -> str:
        his = s[0]
        c= 0
        for i in s:
                if i == his:
                    c+=1
                else:
                    c=1
                his = i
                if c < 3:
                    ans +=i
        return ans
```


---
