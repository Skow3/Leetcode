# MEDIUM

# WILL EXPLAIN IT LATER
```PYTHON
class Solution:
    def totalFruit(self, fruits):
        n = len(fruits)
        mp = {}
        i = 0
        j = 0
        count = 0

        while j < n:
            fruit = fruits[j]
            if fruit in mp:
                mp[fruit] += 1
            else:
                mp[fruit] = 1

            if len(mp) <= 2:
                count = max(count, j - i + 1)
            else:
                mp[fruits[i]] -= 1
                if mp[fruits[i]] == 0:
                    del mp[fruits[i]]
                i += 1

            j += 1

        return count

```
