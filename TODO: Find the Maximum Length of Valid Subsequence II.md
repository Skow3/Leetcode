# MEDIUM

Will explain this code later on when i'll do dynamic programming separately

# SOLUTION
```python
class Solution:
    def maximumLength(self, nums, k):
        n = len(nums)
        # Creating a 2D dp array with k rows and n columns, all initialized to 1
        dp = [[1] * n for _ in range(k)]
        maxSub = 1

        for i in range(1, n):
            for j in range(i):
                mod = (nums[j] + nums[i]) % k
                dp[mod][i] = max(dp[mod][i], 1 + dp[mod][j])
                maxSub = max(maxSub, dp[mod][i])

        return maxSub
```
