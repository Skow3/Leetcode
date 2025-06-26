# MEDIUM
2311

* The Approach which came to my mind first was converting this k into a binary string and then finding the indexes and then counting 
the zeroes . 
* This approach was completely correct as per me because i thought that the condition is == k .
* But it was <=k .
* Though this code passed 61/153 cases.

### APPROACH 1
```PYTHON
class Solution(object):
    def longestSubsequence(self, s, k):
        """
        :type s: str
        :type k: int
        :rtype: int
        """
        k = bin(k)[2:]
        print(k)
        count = len(k)
        if count > len(s):
            return len(s)
        if k in s:
            g = s.rfind(k)
            print(g)
            while g!=-1:
                if s[g] == '0':
                    count+=1
                    #print(f"{count}, {g}")
                g-=1
        print(count)
```

Now since we have to see <=k we'll do the linear approach 
For example :
We will start from the rightmost index and then go through counting the zeroes and Checking the k value it will work
* I also thought of counting the 0's starting from the rightmost indexed 1
* But doing that will tend to ignore some 1's too [satisfying the condition answer<=k]

SO now .. the code becomes

# SOLUTION
```python
class Solution(object):
    def longestSubsequence(self, s, k):
        """
        :type s: str
        :type k: int
        :rtype: int
        """
        l = 1
        count=0
        i=len(s)-1
        while i >=0:
            if s[i]== '0':
                count+=1
            elif (l <= k):
                k = k - l
                count+=1
            if l <=k:
                l*=2
            i-=1
        return count
```

 --->  NOW THIS WILL WORK AS EXPECTED

