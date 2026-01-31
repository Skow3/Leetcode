# EASY
119

* Easy question got it right.

```PYTHON
class Solution(object):
    def getRow(self, rowIndex):
        """
        :type rowIndex: int
        :rtype: List[int]
        """
        def make(d):
            i=0
            e= list(d)
            for i in range(len(d)-1):
                e[i+1]= d[i]+d[i+1]
            e.append(1)
            return e
        ans= []
        for i in range(rowIndex+1):
            ans = make(ans)
        return ans 
```

TOC : 100%
SC:  85%
