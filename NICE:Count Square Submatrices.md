# MEDIUM:
1277

The question was nice and to calculate this number of subsquare-matrices i thought for the approach for going and calculating the right,below and diagonal for each cell.
The problem was with a lot of T.C and TLE then used Memoization

```python
class Solution(object):
    def countSquares(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: int
        """
        m, n = len(matrix), len(matrix[0])
        t = [[-1 for _ in range(n)] for _ in range(m)]

        def solve(i, j):
            if i >= m or j >= n:
                return 0
            if matrix[i][j] == 0:
                return 0
            if t[i][j] != -1:
                return t[i][j]

            # GOing Right
            right = solve(i, j + 1)
            # Going Diagonal
            diagonal = solve(i + 1, j + 1)
            # Going Below
            below = solve(i + 1, j)

            t[i][j] = 1 + min(right, diagonal, below)
            return t[i][j]

        result = 0
        for i in range(m):
            for j in range(n):
                result += solve(i, j)

        return result

```


There is one more approach for this but it is with dynamic PROGRAMMING will do that later on next month
