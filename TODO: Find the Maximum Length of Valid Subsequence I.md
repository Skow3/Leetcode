# MEDIUM

not in a mood today to explain this 

```python
class Solution:
    def maximumLength(self, nums):
        count_even = 0
        count_odd = 0

        for num in nums:
            if num % 2 == 0:
                count_even += 1
            else:
                count_odd += 1

        # If nums is empty, return 0
        if not nums:
            return 0

        # Try building alternating parity subsequence
        alt_len = 1  # At least one number
        prev_parity = nums[0] % 2

        for i in range(1, len(nums)):
            curr_parity = nums[i] % 2
            if curr_parity != prev_parity:
                alt_len += 1
                prev_parity = curr_parity

        return max(count_even, count_odd, alt_len)
```
