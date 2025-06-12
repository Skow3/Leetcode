# EASY

##### Concepts:
1. Square and Square rootss
2. Working and dealing in binary numbers

If we do the AND operation on a number with its 1 decrement we will get zero if it is a power of 2
EX. 10000  &  1111  == 0 
So using that concept i did the second code

### FIRST APPROACH 
```python
class solution(object):
    def isPowerOfTwo(self, n):
        """
        :type n: int
        :rtype: bool
        """
        n = bin(n)[2:]
        flag = False
        if n[0] == 1:
            flag = True 
        for i in n[1:]:
            if i==1:
                flag = False
        return flag
```

### SECOND APPROACH 

```python
class Solution(object):
    def isPowerOfTwo(self, n):
        """
        :type n: int
        :rtype: bool
        """
        return n > 0 and (n & (n - 1)) == 0
```

---


