# MEDIUM
There was a same question which i did yesterday
### quite easy

---

The approach or mindset was clear and easy 
  The problem which i did yesterday had the same thing to do the only difference here is that the question is made to look a bit difficult
  and the second this is in the yesterday's problem we were allowed to interchange the digit with 0 but here we're not allowed to change
  the initial digit.

SO .. here is my solution 

1. Changing the first digit of the number to '9' if it is not : maxt
2. Changing the first digit of the number to '1' if it is not '1' : mint
3. Changing the whatsoever digit which comes if the first digits are '9' to '9' : maxt
4. Changing the whatsoever digit which comes if the first digits are '1' to '0' : mint


# CODE:
```PYTHON
class solution:
    def maxDiff(self, num: int) -> int:
        nums = str(num)
        begin = nums[0]
        # Calculate maxi
        if begin != '9':
            maxi = nums.replace(begin, '9')
        else:
            maxi = nums
            for i in nums[1:]:
                if i!='9':
                    maxi = nums.replace(i,'9')
                    break
        # Calculate mint
        if begin != '1':
            mint = nums.replace(begin, '1')
        else:
            mint = nums
            for i in nums[1:]:
                if i != '0' and i != '1':
                    mint = mint.replace(i, '0')
                    break
        return int(maxi) - int(mint)
```

TC : logn ; 100%
