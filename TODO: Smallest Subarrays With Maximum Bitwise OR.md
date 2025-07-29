# MEDIUM

WILL WRITE THE EXPLANATION LATER 

```PYTHON
class Solution:
    def smallestSubarrays(self, nums):
        n = len(nums)
        result = [0] * n
        setBitIndex = [-1] * 32  # Initialize all bit positions as unset

        for i in range(n - 1, -1, -1):
            endIndex = i
            for j in range(32):
                if not (nums[i] & (1 << j)):  # If j-th bit is not set
                    if setBitIndex[j] != -1:
                        endIndex = max(endIndex, setBitIndex[j])
                else:
                    setBitIndex[j] = i
            result[i] = endIndex - i + 1

        return result
```
