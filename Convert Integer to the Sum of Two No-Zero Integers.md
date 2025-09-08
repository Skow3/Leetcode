# EASY
1317

* The question was quite good .. if a person doesn't strike out to check for one's 0 and then others than it would be tough for him.
* Did this question within 5 mins.

```PYTHON
class Solution(object):
    def getNoZeroIntegers(self, n):
        """
        :type n: int
        :rtype: List[int]
        """
        s = 1
        d = n-1
        f = True
        while f:
            f = False
            for i in str(d):
                print(i)
                if i == '0':
                    s +=1
                    while '0' in str(s):
                        s+=1
                        d-=1
                    d -=1
                    f = True
        return [s,d]
```


What cases i missed [IN ORDER]
* [11]
* [309]
* [4102]

Passed 67.9%
