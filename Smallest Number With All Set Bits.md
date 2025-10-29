# EASY 
3370

This was easy till i was not finding the optimized solution ..
The optmized solution was a bit tricky.

Now :

# VERSION 1:
```python
class Solution:
    def smallestNumber(self, n: int) -> int:
        while True:
            if (n+1 & n)==0 :
                return(n)
            n+=1
```


# OPTIMIZATION:
explained in the file manager
```python
class Solution:
    def smallestNumber(self, n: int) -> int:
        n |= (n >> 1)
        n |= (n >> 2)
        n |= (n >> 4)
        n |= (n >> 8)
        n |= (n >> 16)
        n |= (n >> 32)
        return n
```
