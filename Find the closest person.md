# EASY
3516

* This is the easiest question i have ever seen in leetcode.
* Just simple absolute value comparison.

```python
class Solution(object):
    def findClosest(self, x, y, z):
        """
        :type x: int
        :type y: int
        :type z: int
        :rtype: int
        """
        if abs(z-x) > abs(z-y):
            return 2
        elif abs(z-x) < abs(z-y):
            return 1
        else:
            return 0
```
