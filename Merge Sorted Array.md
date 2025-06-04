# EASY BUT TRICKY
-> We have to change the nums instead of returning anything 

Also we cannot just have the num value equal to new num value
Instead we should just make each element of num1 to new values


### WHAT I WAS THINKING THIS BEFORE:
```PYTHON
class Solution(object):
    def merge(self, nums1, m, nums2, n):
        """
        :type nums1: List[int]
        :type m: int
        :type nums2: List[int]
        :type n: int
        :rtype: None Do not return anything, modify nums1 in-place instead.
        """
        nums1 = sorted(nums1[0:m]+nums2[0:n])
        print(nums1)
        pass
```

#### AFTER THINKING ALOT I CAME THROUGH THIS SOLUTION

```python
class Solution(object):
    def merge(self, nums1, m, nums2, n):
        """
        :type nums1: List[int]
        :type m: int
        :type nums2: List[int]
        :type n: int
        :rtype: None Do not return anything, modify nums1 in-place instead.
        """
        merged = sorted(nums1[:m] + nums2[:n])
        for i in range(len(merged)):
            nums1[i] = merged[i]
```
