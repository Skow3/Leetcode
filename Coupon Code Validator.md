# EASY
3606

* Missed some corner cases in the beginning like handling of "_" [handled it using a flag later on]
* Also was confused about "How to get the sorted values according to the alphabet but since only 4 options [diff] were there so i handled it by taking some
  arrays.


```python
class Solution(object):
    def validateCoupons(self, code, businessLine, isActive):
        """
        :type code: List[str]
        :type businessLine: List[str]
        :type isActive: List[bool]
        :rtype: List[str]
        """
        e= []
        g= []
        p= []
        r= []
        for i in range(len(code)):
            if len(code[i])==1:
                if code[i]=="_":
                    pg=True
            l=code[i].replace('_',"")
            if l.isalnum() or pg:
                if isActive[i]:
                    if businessLine[i]=="electronics":
                        e.append(code[i])
                    if businessLine[i]=="grocery":
                        g.append(code[i])
                    if businessLine[i]=="pharmacy":
                        p.append(code[i])
                    if businessLine[i]=="restaurant":
                        r.append(code[i])
        ans=[]
        for j in sorted(e):
            ans.append(j)
        for j in sorted(g):
            ans.append(j)
        for j in sorted(p):
            ans.append(j)
        for j in sorted(r):
            ans.append(j)

        return ans
```

TC :65%
SC :85%
