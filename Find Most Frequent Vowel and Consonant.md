# EASY 
3541

* Easy just setting up a dictionary

```python
class Solution:
    def maxFreqSum(self, s: str) -> int:
        """
        :type s: str
        :rtype: int
        """
        countt = [0, 0, 0, 0, 0]  # a, e, i, o, u
        f = {}

        for ch in s:
            if ch == 'a':
                countt[0] += 1
            elif ch == 'e':
                countt[1] += 1
            elif ch == 'i':
                countt[2] += 1
            elif ch == 'o':
                countt[3] += 1
            elif ch == 'u':
                countt[4] += 1
            else:
                f[ch] = f.get(ch, 0) + 1

        max_vowel = max(countt) if countt else 0
        max_consonant = max(f.values()) if f else 0

        return max_vowel + max_consonant

```
