# MEDIUM
11


# FIRST SOLUTION :
```python
class Solution:
    def maxArea(self, height):
        n = len(height)
        i, j = 0, n - 1
        water = 0

        while i < j:
            h = min(height[i], height[j])
            w = j - i
            area = h * w
            water = max(water, area)

            if height[i] <= height[j]:
                i += 1
            else:
                j -= 1

        return water
```
