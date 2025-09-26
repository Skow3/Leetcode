# MEDIUM
611

```PYTHON
class Solution:
    def triangleNumber(self, nums):
        n = len(nums)
        if n < 3:
            return 0

        nums.sort()
        count = 0

        for k in range(n - 1, 1, -1):  # k is the largest side
            i, j = 0, k - 1  # two pointers

            while i < j:
                if nums[i] + nums[j] > nums[k]:
                    count += (j - i)  # all pairs (i..j-1, j) will satisfy the inequality
                    j -= 1
                else:
                    i += 1

        return count
```



# 2nd Approach
Optimized from O(n^3) to O(n^2)
```python
class Solution:
  def triangleNumber(self, nums):
    positive_nums = [num for num in nums if num > 0]
    n = len(positive_nums)

    if n < 3:
      return 0

    positive_nums.sort()
    
    count = 0
    
    for k in range(n - 1, 1, -1):
      c = positive_nums[k]
      
      left, right = 0, k - 1
      
      while left < right:
        a = positive_nums[left]
        b = positive_nums[right]
        
        if a + b > c:
          count += (right - left)
          right -= 1
        else:
          left += 1
          
    return count
```
