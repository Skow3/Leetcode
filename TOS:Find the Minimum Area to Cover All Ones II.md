# HARD
3197
TOS : Topic to Study

## Code 1
```python
class Solution:
    def rotateClockWise(self, grid):
        m = len(grid)
        n = len(grid[0])
        rotatedGrid = [[0] * m for _ in range(n)]
        for i in range(m):
            for j in range(n):
                rotatedGrid[j][m - i - 1] = grid[i][j]
        return rotatedGrid

    def minimumArea(self, startRow, endRow, startCol, endCol, grid):
        m = len(grid)
        n = len(grid[0])

        minRow = m
        maxRow = -1
        minCol = n
        maxCol = -1

        for i in range(startRow, endRow):
            for j in range(startCol, endCol):
                if grid[i][j] == 1:
                    minRow = min(minRow, i)
                    maxRow = max(maxRow, i)
                    minCol = min(minCol, j)
                    maxCol = max(maxCol, j)

        if maxRow == -1:  # no 1s found
            return 0
        return (maxRow - minRow + 1) * (maxCol - minCol + 1)

    def utility(self, grid):
        m = len(grid)
        n = len(grid[0])

        result = float("inf")

        # Split into top + bottomLeft + bottomRight
        for rowSplit in range(1, m):
            for colSplit in range(1, n):
                top = self.minimumArea(0, rowSplit, 0, n, grid)
                bottomLeft = self.minimumArea(rowSplit, m, 0, colSplit, grid)
                bottomRight = self.minimumArea(rowSplit, m, colSplit, n, grid)

                result = min(result, top + bottomLeft + bottomRight)

                topLeft = self.minimumArea(0, rowSplit, 0, colSplit, grid)
                topRight = self.minimumArea(0, rowSplit, colSplit, n, grid)
                bottom = self.minimumArea(rowSplit, m, 0, n, grid)

                result = min(result, topLeft + topRight + bottom)

        # Split into top + middle + bottom
        for split1 in range(1, m):
            for split2 in range(split1 + 1, m):
                top = self.minimumArea(0, split1, 0, n, grid)
                middle = self.minimumArea(split1, split2, 0, n, grid)
                bottom = self.minimumArea(split2, m, 0, n, grid)

                result = min(result, top + middle + bottom)

        return result

    def minimumSum(self, grid):
        result = self.utility(grid)
        rotatedGrid = self.rotateClockWise(grid)
        result = min(result, self.utility(rotatedGrid))
        return result
```


# CODE 2 [ FINAL OPTIMIZED ]
```python
class Solution:
    def minimumSum(self, grid: list[list[int]]) -> int:
        """
        Calculates the minimum total area of three non-overlapping bounding boxes
        that enclose all '1's in the grid.
        """
        R, C = len(grid), len(grid[0])

        # Use a padded prefix sum array for cleaner O(1) subgrid sum queries.
        # This avoids boundary checks inside the get_sum function.
        psum = [[0] * (C + 1) for _ in range(R + 1)]
        for r in range(R):
            for c in range(C):
                psum[r + 1][c + 1] = grid[r][c] + psum[r][c + 1] + psum[r + 1][c] - psum[r][c]

        def get_sum(r1, c1, r2, c2):
            """Calculates the sum of 1s in a rectangle using the prefix sum array."""
            return psum[r2 + 1][c2 + 1] - psum[r1][c2 + 1] - psum[r2 + 1][c1] + psum[r1][c1]

        def get_bounding_area(r1, c1, r2, c2):
            """
            Finds the area of the minimal bounding box for 1s within a given partition.
            Returns float('inf') if the partition is empty.
            """
            if get_sum(r1, c1, r2, c2) == 0:
                return float('inf')

            min_r, max_r = r1, r2
            min_c, max_c = c1, c2
            
            # Shrink boundaries inward to find the tightest fit
            while get_sum(min_r, c1, min_r, c2) == 0: min_r += 1
            while get_sum(max_r, c1, max_r, c2) == 0: max_r -= 1
            while get_sum(r1, min_c, r2, min_c) == 0: min_c += 1
            while get_sum(r1, max_c, r2, max_c) == 0: max_c -= 1
            
            return (max_r - min_r + 1) * (max_c - min_c + 1)

        min_total_area = float('inf')

        def check_partitions(p1, p2, p3):
            """Calculates the total area for a set of three partitions and updates the minimum."""
            nonlocal min_total_area
            total_area = get_bounding_area(*p1) + get_bounding_area(*p2) + get_bounding_area(*p3)
            min_total_area = min(min_total_area, total_area)

        # --- Iterate through all 6 fundamental partition patterns ---

        # Pattern 1: Three horizontal stripes
        for r1 in range(R - 2):
            for r2 in range(r1 + 1, R - 1):
                check_partitions((0, 0, r1, C - 1), (r1 + 1, 0, r2, C - 1), (r2 + 1, 0, R - 1, C - 1))

        # Pattern 2: Three vertical stripes
        for c1 in range(C - 2):
            for c2 in range(c1 + 1, C - 1):
                check_partitions((0, 0, R - 1, c1), (0, c1 + 1, R - 1, c2), (0, c2 + 1, R - 1, C - 1))
        
        # Patterns 3-6: One horizontal and one vertical cut
        # This single loop block handles all four mixed-cut scenarios efficiently.
        for r_cut in range(R - 1):
            for c_cut in range(C - 1):
                # Pattern 3: Horizontal cut, top part split vertically
                check_partitions((0, 0, r_cut, c_cut), (0, c_cut + 1, r_cut, C - 1), (r_cut + 1, 0, R - 1, C - 1))
                
                # Pattern 4: Horizontal cut, bottom part split vertically
                check_partitions((0, 0, r_cut, C - 1), (r_cut + 1, 0, R - 1, c_cut), (r_cut + 1, c_cut + 1, R - 1, C - 1))
                
                # Pattern 5: Vertical cut, left part split horizontally
                check_partitions((0, 0, r_cut, c_cut), (r_cut + 1, 0, R - 1, c_cut), (0, c_cut + 1, R - 1, C - 1))

                # Pattern 6: Vertical cut, right part split horizontally
                check_partitions((0, 0, R - 1, c_cut), (0, c_cut + 1, r_cut, C - 1), (r_cut + 1, c_cut + 1, R - 1, C - 1))

        return min_total_area
```
