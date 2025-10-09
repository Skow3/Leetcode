# MEDIUM

3494


WILL EXPLAIN LATER 

```PYTHON
class Solution(object):
    def minTime(self, skill, mana):
        """
        :type skill: List[int]
        :type mana: List[int]
        :rtype: int
        """
        n = len(skill)
        m = len(mana)
        finishTime = [0] * n  
        for j in range(m):
            finishTime[0] += mana[j] * skill[0]

            for i in range(1, n):
                finishTime[i] = max(finishTime[i], finishTime[i - 1]) + mana[j] * skill[i]

            for i in range(n - 1, 0, -1):
                finishTime[i - 1] = finishTime[i] - mana[j] * skill[i]

        return finishTime[n - 1]

```
