# Medium
2054

```PYTHON
class Solution(object):
    def maxTwoEvents(self, events):
        """
        :type events: List[List[int]]
        :rtype: int
        """
        events.sort()
        n=len(events)
        ends=[0]*n
        mx=0
        for i in range(n-1,-1,-1):
            mx=max(mx,events[i][2])
            ends[i]=mx
        res=0
        j=0
        starts=[e[0] for e in events]
        for i in range(n):
            res=max(res,events[i][2])
            l=i+1
            r=n-1
            k=n
            while l<=r:
                m=(l+r)//2
                if starts[m]>events[i][1]:
                    k=m
                    r=m-1
                else:
                    l=m+1
            if k<n:
                res=max(res,events[i][2]+ends[k])
        return res
````
