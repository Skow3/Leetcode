# MEDIUM 
3147

```python
class Solution(object):
    def maximumEnergy(self, energy, k):
        """
        :type energy: List[int]
        :type k: int
        :rtype: int
        """
        n = len(energy)
        t = [0] * n  # DP array
        for i in range(n - 1, -1, -1):
            if i + k < n:
                t[i] = energy[i] + t[i + k]
            else:
                t[i] = energy[i]

        return max(t)

```
