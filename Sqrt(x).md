# EASY
### Python

### I used 2 methods for calculating the sqrt here , although the second method was TLE

## METHOD 1 

Using mathlib
```python
class Solution(object):
    def mySqrt(self, x):
        """
        :type x: int
        :rtype: int
        """
        return int(math.sqrt(x))
```

### This is the second method , this can work for very less constraints
#### NEWTON'S Method
```PYTHON
def sqrtt(n, epsilon=1e-10):
    if n < 0:
        raise ValueError("Cannot compute square root of a negative number")
    if n == 0:
        return 0
    guess = n / 2.0
    while abs(guess * guess - n) > epsilon:
        guess = (guess + n / guess) / 2
    return guess
```


