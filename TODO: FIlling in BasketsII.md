# EASY

# FINAL SOLUTION :
```python
class Solution:
    def numOfUnplacedFruits(self, fruits, baskets):
        unplaced = 0
        used = [False] * len(baskets)

        for fruit in fruits:
            is_placed = False
            for j in range(len(baskets)):
                if fruit <= baskets[j] and not used[j]:
                    is_placed = True
                    used[j] = True
                    break
            if not is_placed:
                unplaced += 1

        return unplaced
```
