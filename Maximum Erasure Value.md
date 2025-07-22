# MEDIUM
1695
**SLIDING WINDOW**
---
* A question of subarray and the first approach as always i forgot that in this we have to find the sub-array so..
* I went with this solution.

```python
class Solution:
    def maximumUniqueSubarray(self, nums: List[int]) -> int:
        nums = [5,2,1,2,5,2,1,2,5]
        nums.sort()
        p = []
        sumt = 0
        i= len(nums)-1
        while i>=0:
            if nums[i] not in p:
                p.append(nums[i])
                sumt+=nums[i]
            i-=1
        return sumt
```


Though after looking again at the question i got the sliding window approach ..:

# FINAL SOLUTION
```PYTHON
class Solution:
    def maximumUniqueSubarray(self, nums):
        n = len(nums)
        seen = set()
        
        i = 0
        j = 0
        total = 0
        result = 0
        
        while j < n:
            if nums[j] not in seen:
                total += nums[j]
                result = max(result, total)
                seen.add(nums[j])
                j += 1
            else:
                while i < n and nums[j] in seen:
                    total -= nums[i]
                    seen.remove(nums[i])
                    i += 1
                    
        return result
```


---
