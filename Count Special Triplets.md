# MEDIUM
3583


```python
class Solution:
    def specialTriplets(self, nums):
        MOD = 1000000007
        left = {}
        right = {}
        
        for x in nums:
            right[x] = right.get(x, 0) + 1
        
        ans = 0
        
        for x in nums:
            right[x] -= 1
            d = x * 2
            if d in left and d in right:
                ans = (ans + left[d] * right[d]) % MOD
            left[x] = left.get(x, 0) + 1
        
        return ans
```
