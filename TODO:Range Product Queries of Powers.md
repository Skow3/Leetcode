# MEDIUM
2438
# WILL DO THE EXPLANATION SOON

```PYTHON
class Solution:
    def __init__(self):
        self.M = 10**9 + 7

    def productQueries(self, n, queries):
        powers = []
        result = []

        for i in range(32):
            if (n & (1 << i)) != 0:  
                powers.append(1 << i)

        for query in queries:
            start, end = query
            product = 1
            for i in range(start, end + 1):
                product = (product * powers[i]) % self.M
            result.append(product)

        return result

```
