# MEDIUM
2943

GOOD QUESTION;

It god me thinking into the best way to figure out the answer but in the end .. i went to see the solution.
I understood the solution 

```PYTHON
class Solution(object):
    def maximizeSquareHoleArea(self, n, m, hBars, vBars):
        """
        :type n: int
        :type m: int
        :type hBars: List[int]
        :type vBars: List[int]
        :rtype: int
        """
        def longest(arr):
            if not arr:
                return 1
            arr.sort()
            ans=1
            mx=1
            for i in range(1,len(arr)):
                if arr[i]== arr[i-1]+1:
                    ans+=1
                else:
                    mx= max(ans,mx)
                    ans=1
            mx= max(ans,mx)
            return mx+1  # because the space will be one more than the consicutive empty space
        SIDE = min(longest(hBars),longest(vBars))
        return SIDE*SIDE
```
