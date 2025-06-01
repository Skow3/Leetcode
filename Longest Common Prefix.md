Using the normal but not BRUTEFORCE 
PYTHON 
```python
class Solution(object):
    def longestCommonPrefix(self, strs):
        """
        :type strs: List[str]
        :rtype: str
        """
        for _ in range(len(strs[0])): # Starting the outer loop for matching
            for s in strs: # inner loop for having the comparison
                print(_,s,strs[0][:_])
                if _ >= len(s) or s[_] != strs[0][_]:
                    return strs[0][:_]
        return 0 # this will not work instead we should use
        return strs[0]
```

By using Slice operator i.e :
We can use it in python in different ways Like 
If you're using _ as a variable, it should have been defined before, e.g.:
``
_ = 3



# OTHER SOLUTIONS WITH FASTER TIME COMPLEXITY 
Using the sorted and using first and final

```python
class solution:
    def longestCommonPrefix(self, v):
        ans=""  # intializing answer string
        v=sorted(v)  # sorting the array helps to arrange such that all the elements between the endpoints must have common 
        first=v[0] 
        last=v[-1]
        for i in range(min(len(first),len(last))):
            if(first[i]!=last[i]):
                return ans
            ans+=first[i]
        return ans
```
print("hello"[:_])  # prints 'hel'
``
