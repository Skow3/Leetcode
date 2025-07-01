# Easy 
The question went in one strike

```python
class Solution(object):
    def possibleStringCount(self, word):
        """
        :type word: str
        :rtype: int
        """
        his = word[0]
        count=0
        for i in word:
            if i == his:
                count+=1
            his =i
        return count
```

TOC : 45%
O(n)

---
