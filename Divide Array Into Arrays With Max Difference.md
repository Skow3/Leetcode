# MEDIUM
Array question
2966
---
The question spelled easy but the example confused me to think that the solution is tougher than i think.

But after analyzing the given and some more of my own example got to some points which made the question easy.
* Sorting the given nums list sorted the question too.
* Since it was given that we can give any one of the example for that therefor the example which were given in the question were
just to confuse.

The solution was this simple:
```python
class Solution(object):
    def divideArray(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[List[int]]
        """
        ans = []
        nums.sort()
        for i in range(0,len(nums),3):
            s =nums[i:i+3]
            if s[-1] - s[0] > k:
                return []
            else:
                ans.append(s)
        return ans
```

TOC : NlogN [91%]

---

# WHAT THIS QUESTION TOUGHT ME 
1. Always beleif that i can do it.
2. Never ever stop taking your examples.
3. Always try to write in a notebook.
