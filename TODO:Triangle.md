# MEDIUM 
120

```python
class Solution:
    def minimumTotal(self, triangle):
        n = len(triangle)

        for row in range(1, n):
            for col in range(len(triangle[row])):
                prev_up_val = triangle[row - 1][min(col, len(triangle[row - 1]) - 1)]
                prev_up_left = triangle[row - 1][max(col - 1, 0)]

                triangle[row][col] += min(prev_up_val, prev_up_left)

        return min(triangle[-1])
```
