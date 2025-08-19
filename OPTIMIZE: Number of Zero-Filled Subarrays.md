# MEDIUM
2348

* Since it is a subsequence problem and just to count the occurences solved it with simple pointer slide method

# FINAL ANSWER
```python
class Solution(object):
    def zeroFilledSubarray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        nums = [0,0,0,2,0,0]
        i=0
        countt=0
        while i< len(nums):
            if nums[i]==0:
                j=i
                countt+=1
                while j<len(nums) and nums[j]==0:
                    countt+=1
                    j+=1
                countt-=1
                n=j-i
                if n>1:
                    countt+= n*(n+1)/2 -n
                i=j
                continue
            i+=1 
        return int(countt)
```

DONE
