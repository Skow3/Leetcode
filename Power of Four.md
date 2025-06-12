# EASY

#### USED THE CONCEPTS I USED IN Power of Two in Approach 1

```python
class Solution(object):
    def isPowerOfFour(self, n):
        """
        :type n: int
        :rtype: bool
        """
        c=0
        n = bin(n)[2:]
        flag = False
        if n[0] == '1':
            flag = True
        for i in n[1:]:
            if i == '1':
                flag= False
            else:
                c+=1
        if c%2 != 0:
            flag = False
        return flag
```

Solved with 100% TR
Solved with 54% MR
