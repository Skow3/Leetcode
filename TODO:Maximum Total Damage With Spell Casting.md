# MEDIUM

```python
class Solution(object):
    def maximumTotalDamage(self, power):
        """
        :type power: List[int]
        :rtype: int
        """
        from collections import Counter
        import bisect

        # Step 1: Count frequency of each unique power value
        mp = Counter(power)

        # Step 2: Collect and sort unique values
        nums = sorted(mp.keys())
        n = len(nums)

        # dp[i] = maximum total damage starting from index i
        t = [0] * n
        result = float('-inf')

        # Step 3: Iterate backward
        for i in range(n - 1, -1, -1):
            # Skip current value
            skip = t[i + 1] if i + 1 < n else 0

            # Take current value
            j = bisect.bisect_left(nums, nums[i] + 3, i + 1)
            take = nums[i] * mp[nums[i]] + (t[j] if j < n else 0)

            t[i] = max(skip, take)
            result = max(result, t[i])

        return result

```
