# EASY 

---

#### 1st Solution
```python
class Solution(object):
    def maxAdjacentDistance(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        maxd = 0
        for i in range(len(nums)):
            if i+1 < len(nums):
                if maxd < abs(nums[i]-nums[i+1]):
                    maxd = abs(nums[i]-nums[i+1])
        if maxd < abs(nums[0]-nums[-1]):
            maxd = abs(nums[0]-nums[-1])
        return maxd
```

#### One liner solution
```python
class solution:
    def maxAdjacentDistance(self, nums):
        return max(abs(nums[0]-nums[-1]), max(abs(x-y) for x, y in pairwise(nums)))
```

#### THINGS I LEARNT :
1. pairwise function from itertools library.
2. Also i learnt to use len for checking out of bound things rather than `is None`

---

