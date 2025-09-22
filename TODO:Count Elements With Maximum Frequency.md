# EASY
3005

# PYTHON
```python
class Solution:
    def maxFrequencyElements(self, nums):
        arr = [0] * 101
        max_freq = 0

        for num in nums:
            arr[num] += 1
            if arr[num] > max_freq:
                max_freq = arr[num]

        count_max = 0
        for freq in arr:
            if freq == max_freq:
                count_max += 1

        return count_max * max_freq
```
