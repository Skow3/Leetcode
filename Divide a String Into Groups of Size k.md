# EASY
2183

Here the question was quite easy for me ..
Approach was also normal in python 

# Solution:
```python
class Solution(object):
    def divideString(self, s, k, fill):
        """
        :type s: str
        :type k: int
        :type fill: str
        :rtype: List[str]
        """
        ans=[]
        for i in range(0,len(s),k):
            if len(s[i:i+k]) < k:
                ans.append(s[i:i+k] + fill*(k-len(s[i:i+k])))
            else:
                ans.append(s[i:i+k])
        return ans
```

---
# THINGS I LEARNT :
1. We can use `k= 'kav'+'a'*2` to form `kavyaa`.

