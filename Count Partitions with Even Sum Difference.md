# EASY
3432

```python
class Solution(object):
    def countPartitions(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        nums = [2,4,6,8]
        ct = sum(nums)
        tp = 0
        ans=0
        for i in range(len(nums)-1):
            tp +=nums[i]
            if (ct-tp-tp)%2==0:
                ans+=1
        return ans
```
