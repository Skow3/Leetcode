# MEDIUM
2044

---

* This problem was quite based on mathematical understanding of how bitwise operators work.
* Especially OR operation.
* Since we can just go for iterating over all n entries of nums and then get the maxOR value.
* Then since we just have to find the number of Subsets rather then noting them down.
* So i went for simple recursion of Take and Don't take

---
# FINAL SOLUTION
```python
class Solution(object):
    def Countsub(self,index , currOr, nums,maxOR):
        if index == len(nums):
            if currOr == maxOR:
                return 1
            return 0
        
        takecount = self.Countsub(index+1,currOr | nums[index],nums,maxOR)
        nottakecount = self.Countsub(index+1,currOr,nums,maxOR)

        return takecount+nottakecount
    def countMaxOrSubsets(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        maxOR = 0
        for i in nums:
            maxOR |= i
        
        currOr = 0
        return self.Countsub(0,currOr,nums,maxOR)
```

---

* Was a bit confused for the self operator for some minutes while submitting.
