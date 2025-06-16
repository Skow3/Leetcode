# EASY
2016

---

See in this problem at first i was trying to do bruteforce method with simple technique :

```python
class Solution:
    def maximumDifference(self, nums):
        maxt =0
        mint = float('+inf')
        flg = 0
        for i in range(1,len(nums)): # maximum element 
            if nums[i] >=maxt:
                maxt = nums[i]
                flg =i
        print(maxt)
        for i in range(0,flg): # min element
            if nums[i]<= mint and nums[i]<maxt:
                mint = nums[i]
        print(mint)
        if mint== float('+inf'):
            return -1
        else:
            return (maxt - mint)
```

---

Though this code passed the maximum of the tests but it failed a test number 47/54

The problem i spotted in this code was that since i was finding the max and the min which comes before tha max but there is a 
case where a min difference is after taking the maxt for example:

CASE : [3,5,100,1,99]
In this example if we go for finding the maxt it would be 100 and therefore the mint  =3 [before 100]  therefore the difference 
will be 97 but clearly we can see that the difference here is 98

---

### COPING UP 
This was the code which i refactored understanding the brute force which i applied earlier 

```python
class Solution:
    def maximumDifference(self, nums):
        min_num = nums[0]   # Initializing the min_num as the first num of the nums
        max_diff = -1  # will return -1 if no case is found
        for num in nums[1:]:
            if num > min_num:
                max_diff = max(max_diff, num - min_num)
            else:
                min_num = min(min_num, num)
        return max_diff
```

---
