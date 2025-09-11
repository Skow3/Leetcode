# MEDIUM
2785

WILL EXPLAIN IT AFTER THIS WEEK
```python
class Solution:
    def isVowel(self, ch):
        ch = ch.lower()
        return ch in "aeiou"

    def sortVowels(self, s):
        mp = {}
        for ch in s:
            if self.isVowel(ch):
                mp[ch] = mp.get(ch, 0) + 1

        temp = "AEIOUaeiou"
        j = 0
        s = list(s)

        for i in range(len(s)):
            if self.isVowel(s[i]):
                while j < len(temp) and mp.get(temp[j], 0) == 0:
                    j += 1
                s[i] = temp[j]
                mp[temp[j]] -= 1

        return "".join(s)

```
