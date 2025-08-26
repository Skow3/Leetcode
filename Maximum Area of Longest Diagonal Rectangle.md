# EASY
3000

The question was easy just a simple check approach: 

# FINAL CODE:
```python
class Solution(object):
    def areaOfMaxDiagonal(self, dimensions):
        """
        :type dimensions: List[List[int]]
        :rtype: int
        """
        diag =0
        area = 0
        for i in dimensions:
            d = (i[0]*i[0]+i[1]*i[1])**0.5
            if d==diag:
                area = max(area,i[0]*i[1])
            if d> diag:
                diag = d
                area = i[0]*i[1]
        return(area)
```

