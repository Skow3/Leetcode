Using the normal but not BRUTEFORCE 
PYTHON 

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
        return 0


By using Slice operator i.e :
We can use it in python in different ways Like 
If you're using _ as a variable, it should have been defined before, e.g.:
``
_ = 3
print("hello"[:_])  # prints 'hel'
``
