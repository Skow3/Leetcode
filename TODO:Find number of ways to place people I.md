# MEDIUM
3015

Will explain it after exams or on friday [05/09/25]


```python
class Solution:
    def numberOfPairs(self, points):
        n = len(points)

        # Sort: x ascending, if x same then sort y descending
        points.sort(key=lambda p: (p[0], -p[1]))

        result = 0

        for i in range(n):
            x1, y1 = points[i]  # upper left
            bestY = -10**9  # acts like INT_MIN

            for j in range(i + 1, n):
                x2, y2 = points[j]  # lower right

                # Condition: (x2, y2) must not be above (x1, y1)
                if y2 > y1:
                    continue

                if y2 > bestY:
                    result += 1
                    bestY = y2

        return result

```
