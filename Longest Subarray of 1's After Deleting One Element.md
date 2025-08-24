# MEDIUM
1493

* Got easily striked with the idea of using flags
* Went with cathing all corner cases at once with if-else.

# FINAL CODE:
```python
class Solution(object):
    def longestSubarray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        Zeroone_found = False
        ct=0
        ans=0
        i=0
        j=0
        if nums[i]==0:
            while i<len(nums) and nums[i]==0:
                i+=1
        o=0
        while i<len(nums):
            if nums[i]==0 and Zeroone_found==False:
                Zeroone_found=True
                j=i
                i+=1
                continue
            if nums[i]==0 and Zeroone_found==True:
                Zeroone_found=False
                ans=max(ans,ct)
                ct=0
                i=j+1
                continue
            ct+=1
            i+=1
            o+=1
        if Zeroone_found:
            if ans> ct:
                return(ans)
            else:
                return(ct)
        elif not Zeroone_found:
            if ans > ct-1:
                return(ans)
        if len(nums)== ct:
            return(ct-1)
        else:
            return(ct)
```
