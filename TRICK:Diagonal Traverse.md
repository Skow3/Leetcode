# MEDIUM
463

* It is a nice question and i got a concept of Handling diagonal in matrices.

If it is ->(upwards) diagonal then i+j
If it is ->(downwards) diagonal then i-j

# FINAL CODE:
```python
class Solution(object):
    def findDiagonalOrder(self, mat):
        """
        :type mat: List[List[int]]
        :rtype: List[int]
        """
        m, n = len(mat), len(mat[0])
        mp = {}
        # Fill the map using i + j
        for i in range(m):
            for j in range(n):
                if i + j not in mp:
                    mp[i + j] = []
                mp[i + j].append(mat[i][j])
        result = []
        flip = True
        for key in sorted(mp.keys()):
            if flip:
                mp[key].reverse()
            result.extend(mp[key])
            flip = not flip
        return(result)
```
