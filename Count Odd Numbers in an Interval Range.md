# EASY
1523

The question was easy but if we try to figure out some quick maths trick.
Idk why i was going through the loop approach first but ..

then i tried some brute-force handling alll the cases but still in vain..


LATER I took and read this :

## NUmber of odds from 1 to x is :
odds(1..x) = (x + 1) // 2


Therefore :

```python
class Solution(object):
    def countOdds(self, low, high):
        """
        :type low: int
        :type high: int
        :rtype: int
        """
        return (high + 1) // 2 - low // 2
```
