# MEDIUM
2410

* The question just required a bit of thinking ..
* Will explain it more later

# SOLUTION
```python
class Solution:
    def matchPlayersAndTrainers(self, players, trainers):
        players.sort()
        trainers.sort()

        count = 0
        i = 0
        j = 0
        m = len(players)
        n = len(trainers)

        while i < m and j < n:
            if players[i] <= trainers[j]:
                count += 1
                i += 1
            j += 1

        return count
```

