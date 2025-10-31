# EASY
3289

* Just calculated the simple freq and appended in list when it's frequency becomes 2..

```PYTHON
class Solution:
    def getSneakyNumbers(self, nums: List[int]) -> List[int]:
        freq = {}
        ans = []
        for i in nums:
            if i in freq:
                freq[i]+=1
                if freq[i] == 2:
                    ans.append(i)
                # Could do a len comparison and return as soon as len(ans) becomes too
            else:
                freq[i]=1
        return ans
```
