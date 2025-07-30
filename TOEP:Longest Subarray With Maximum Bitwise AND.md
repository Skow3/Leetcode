# MEDIUM
2419

---

# FINAL SOLUTION
```PYTHON
class Solution:
    def longestSubarray(self, nums):
        max_val = 0
        result = 0
        streak = 0

        for num in nums:
            if num > max_val:
                max_val = num
                result = 0
                streak = 0

            if num == max_val:
                streak += 1

            else:
                streak = 0

            if streak > result:
                result = streak

        return result
```
