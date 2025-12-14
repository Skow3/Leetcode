# HARD
2147

This question felt easier side to me though ..
* Was nearly on the way to solve this ,I'll have to learn to use the circular way i.e to use % .

```python
class Solution(object):
    def numberOfWays(self, corridor):
        MOD = 10**9 + 7
        
        ans = 1        # total ways
        f = False      # first seat found
        t = False      # second seat found
        c = 0          # plants between seat pairs
        d = 0          # total seats counted
        
        for i in range(len(corridor)):
            if corridor[i] == "S":
                d += 1
                if not f:
                    f = True
                elif not t:
                    t = True
                else:
                    # starting a new section
                    ans = (ans * (c + 1)) % MOD
                    c = 0
                    f = True
                    t = False
            
            elif corridor[i] == "P":
                if f and t:
                    c += 1
        
        # invalid if no seats or odd number of seats
        if d == 0 or d % 2 != 0:
            return 0
        
        return ans

```
