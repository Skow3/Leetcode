# Important
## EASY 

## ASKED IN MANY COMPANIES

# FIRST THOUGHT RECURSION 
```python
class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        def climb(n):
            if n==0:
                return 1
            if n<0:
                return 0
            add1 = climb(n-1)
            add2 = climb(n-2)
            return add1+add2
```

Though since it has a time complexity of O(N^2) and the constraints are 0<x>=45
after 39 it will exceed TLE

Now let's see for some solution 

One of it is Memoization since the entries are repetitive
It avoids reduntant computation

```python
class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        memo = {}
        def climb(n):
            if n == 0:
                return 1
            if n < 0:
                return 0
            if n in memo:
                return memo[n]
            memo[n] = climb(n-1) + climb(n-2)
            return memo[n]
        return climb(n)
```

added a memo set for uniques
TC: O(n)

## APPROACH 3
If we have a good look over the above solutions we can come to a conclusion that it is resembling the fibonacci series i.e the ith is the sum of i-1 and i-2 unit 
```python
class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n==1 or n==2 or n==3:
            return n
        a = 1 # i-2
        b = 2 # i-1
        c = 3 # i
        for i in range(3,n+1):
            c = a + b
            temp = b
            b=c
            a= temp
        return c
```


---
# THINGS I RECALLED 

## MEMOIZATION 
## FIBONACCI SERIES
I
