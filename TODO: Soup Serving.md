# MEDIUM

# WILL EXPLAIN LATR

```python
class Solution:
    def __init__(self):
        self.serves = [(100, 0), (75, 25), (50, 50), (25, 75)]
        self.t = []

    def solve(self, A, B):
        if A <= 0 and B <= 0:
            return 0.5
        if A <= 0:
            return 1.0
        if B <= 0:
            return 0.0

        if self.t[int(A)][int(B)] != -1.0:
            return self.t[int(A)][int(B)]

        probability = 0.0

        for a_serve, b_serve in self.serves:
            probability += 0.25 * self.solve(A - a_serve, B - b_serve)

        self.t[int(A)][int(B)] = probability
        return probability

    def soupServings(self, n):
        if n >= 5000:
            return 1.0

        size = n + 1
        self.t = [[-1.0 for _ in range(size)] for _ in range(size)]
        return self.solve(n, n)

```
