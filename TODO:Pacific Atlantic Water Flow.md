# MEDIUM
417

WILL EXPLAIN LATER ON :
```python
class Solution(object):
    def pacificAtlantic(self, heights):
        """
        :type heights: List[List[int]]
        :rtype: List[List[int]]
        """
        if not heights or not heights[0]:
            return []

        rows, cols = len(heights), len(heights[0])

        pacific = set()
        atlantic = set()

        def dfs(r, c, visited, prevHeight):
            if ((r, c) in visited or 
                r < 0 or c < 0 or r >= rows or c >= cols or 
                heights[r][c] < prevHeight):
                return
            visited.add((r, c))
            dfs(r + 1, c, visited, heights[r][c])
            dfs(r - 1, c, visited, heights[r][c])
            dfs(r, c + 1, visited, heights[r][c])
            dfs(r, c - 1, visited, heights[r][c])

        for c in range(cols):
            dfs(0, c, pacific, heights[0][c])
            dfs(rows - 1, c, atlantic, heights[rows - 1][c])
        for r in range(rows):
            dfs(r, 0, pacific, heights[r][0])
            dfs(r, cols - 1, atlantic, heights[r][cols - 1])

        return list(pacific & atlantic)

```
