# EASY 
3136

# FINAL SOLUTION
```python
class Solution(object):
    def isValid(self, word):
        """
        :type word: str
        :rtype: bool
        """
        word  = word.lower()
        if len(word)<3:
            return False
        if word.isalnum() is False:
            return False
        vowels = {'a','e','i','o','u'}
        vt = 0
        ct = 0
        for i in word:
            if i in vowels:
                vt+=1
            else:
                if i.isnumeric() is False:
                    ct+=1
        return (bool(ct) & bool(vt))
```


Will do the cpp code + explanation on friday/tomorrow 

---
