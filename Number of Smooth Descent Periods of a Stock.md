# Medium 
2110

* The question felt quiet tricky at first glance but yes it was good one.
* After getting look at some different examples which i took i understood a pattern.

AND YES THAT PATTERN WORKED:
# PATTERN:
EXAMPLE: [5,4,3,2,1,4]
5->4 : ADD 1
4->3 : ADD 1+ 1 [PREVIOUS LINEUP]
3->2 : ADD 1+ 2 [PREVIOUS LINEUP]
2->1 : ADD 1+ 3 [PREVIOUS LINEUP]

THEN FINALLY ANS + LEN(EXAMPLE)


```python
class Solution(object):
    def getDescentPeriods(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        k=0
        l=0
        ans=0
        for i in range(1,len(prices)):
            if prices[i]==prices[i-1]-1:
                ans+=1+k
                k+=1
            else:
                k=0
        ans += len(prices)
        return ans
```
