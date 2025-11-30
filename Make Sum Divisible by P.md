# MEDIUM
1590
TO DO
```python
class Solution:
    def minSubarray(self, nums, p):
        total = sum(nums)
        need = total % p
        if need == 0:
            return 0  # no need to remove anything
        
        prefix = 0
        seen = {0: -1}  # remainder -> earliest index
        res = len(nums)
        
        for i, x in enumerate(nums):
            prefix = (prefix + x) % p
            # We need a previous prefix with remainder `target`
            target = (prefix - need) % p
            
            if target in seen:
                res = min(res, i - seen[target])
            
            # Store/overwrite the latest index for this remainder
            seen[prefix] = i
        
        return res if res < len(nums) else -1

```
