# MEDIUM
2221

# PYTHON
```python
class Solution:
    def triangularSum(self, nums):
        n = len(nums)
        for size in range(n - 1, 0, -1):
            for i in range(size):
                nums[i] = (nums[i] + nums[i + 1]) % 10
        return nums[0]
```
