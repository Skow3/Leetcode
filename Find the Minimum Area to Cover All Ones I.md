# MEDIUM
3195

* I got the method strike in first 30 seconds but then slowly catching all the cases i went and solved it.
* Just calculating the START , END , MIN , MAX for both findings in ROW AND COLOUMNS.

# CODE 1 :
```python
class Solution(object):
    def minimumArea(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        pk=0
        for item in grid:
            for i in item:
                if i == 1:
                    pk+=1
                    break
        return pk*len(grid[0])
```



# CODE 2:
```python
class Solution(object):
    def minimumArea(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        MIN = 0
        MAX = -1
        START = 0
        END = 0
        for j in range(len(grid)):
            for i in range(len(grid[j])):
                if grid[j][i] == 1:
                    MIN= min(i,MIN)
                    MAX= max(i,MAX)
                    START = min(j,START)
                    END = max(j,END) 
        return((END-START+1)*(MAX-MIN+1))
```


# FINAL CODE :
```python
class Solution(object):
    def minimumArea(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        rows = len(grid)
        cols = len(grid[0])

        MIN = cols
        MAX = -1
        START = rows
        END = -1

        for r in range(rows):
            for c in range(cols):
                if grid[r][c] == 1:
                    MIN = min(MIN, c)
                    MAX = max(MAX, c)
                    START = min(START, r)
                    END = max(END, r)

        if MAX == -1:  
            return 0

        return (END - START + 1) * (MAX - MIN + 1)
```
