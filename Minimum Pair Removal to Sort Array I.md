# EASY

* The question was easy but i took time because i was busy in finding out some pattern.
* But in the end i got that this one will /can be solved in a easy way too.

# Solution 
```python
class Solution(object):
    def minimumPairRemoval(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        ans=0
        def checksorted(nums):
            for i in range(1,len(nums)):
                if nums[i-1] > nums[i]:
                    return True
            return False
        minSum= float('inf')
        minArena=10
        while checksorted(nums):
            minArena= 0
            minSum= float('inf')
            for i in range(1,len(nums)):
                    if minSum > nums[i-1]+nums[i]:
                        minSum= nums[i-1]+nums[i]
                        minArena = i
            if minArena!=0:
                nums[minArena-1]= nums[minArena-1]+nums[minArena]
                nums.pop(minArena)
                ans+=1
        return ans
```


TC : 100%
