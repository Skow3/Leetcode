# EASY 

LATER  .. BUSY IN HACKATHON

# FINAL SOLUTION
```PYTHON
class Solution:
    def maxSum(self, nums):
        seen = [-1] * 101 
        total_sum = 0
        max_neg = -float('inf')  

        for num in nums:
            if num <= 0:
                if num > max_neg:
                    max_neg = num
            elif num >= 0 and num <= 100 and seen[num] == -1:
                total_sum += num
                seen[num] = 1

        return max_neg if total_sum == 0 else total_sum
```
