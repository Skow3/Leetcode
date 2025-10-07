# MEDIUM
1488


# WILL EXPLAIN LATER:
```python
class Solution:
    def avoidFlood(self, rains):
        n = len(rains)
        lake_last_filled = {}   
        dry_days = []           
        ans = [1] * n           

        for day in range(n):
            lake = rains[day]

            if lake == 0:
                dry_days.append(day)   
            else:
                ans[day] = -1      

                if lake in lake_last_filled:
                    found = False
                    for i, d in enumerate(dry_days):
                        if d > lake_last_filled[lake]:
                            ans[d] = lake   
                            dry_days.pop(i)
                            found = True
                            break

                    if not found:
                        return []

                lake_last_filled[lake] = day  # record latest day this lake was filled

        return ans

```
