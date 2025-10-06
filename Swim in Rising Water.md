# HARD
778

# WILL EXPLAIN LATER:
```python
import heapq

class Solution:
    def swimInWater(self, grid):
        n = len(grid)
        directions = [(1, 0), (-1, 0), (0, 1), (0, -1)]
        result = [[float('inf')] * n for _ in range(n)]
        
        # Min-heap (time, i, j)
        pq = [(grid[0][0], 0, 0)]
        result[0][0] = grid[0][0]
        
        while pq:
            curr_time, i, j = heapq.heappop(pq)
            
            # If we reached destination, return time
            if i == n - 1 and j == n - 1:
                return curr_time
            
            # Skip if we’ve already found a better path
            if curr_time > result[i][j]:
                continue
            
            for di, dj in directions:
                ni, nj = i + di, j + dj
                if 0 <= ni < n and 0 <= nj < n:
                    next_time = max(curr_time, grid[ni][nj])
                    if next_time < result[ni][nj]:
                        result[ni][nj] = next_time
                        heapq.heappush(pq, (next_time, ni, nj))
        
        return -1  # Should never reach here

```
