# MEDIUM
165

WILL EXPLAIN THIS LATER THIS MONTH
```python
class Solution:
    def getTokens(self, version):
        return version.split(".")
    
    def compareVersion(self, version1, version2):
        v1 = self.getTokens(version1)
        v2 = self.getTokens(version2)

        m, n = len(v1), len(v2)
        i = 0

        while i < m or i < n:
            a = int(v1[i]) if i < m else 0
            b = int(v2[i]) if i < n else 0

            if a > b:
                return 1
            elif b > a:
                return -1
            else:
                i += 1

        return 0
