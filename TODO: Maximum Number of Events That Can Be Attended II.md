# HARD
1751

Currently have so much of work and packing also for travelling back to college.

will opitmize this code
as soon as i'll get time

# SOlution
```python
class Solution:
    def maxValue(self, events, k):
        events.sort()
        n = len(events)

        # Initializig DP table with -1
        t = [[-1 for _ in range(k + 1)] for _ in range(n + 1)]

        # Custom binary search function
        def upper_bound(events, target_end):
            left, right = 0, len(events)
            while left < right:
                mid = (left + right) // 2
                if events[mid][0] <= target_end:
                    left = mid + 1
                else:
                    right = mid
            return left

        def solve(i, kleft):
            if kleft == 0 or i == n:
                return 0

            if t[i][kleft] != -1:
                return t[i][kleft]

            endt = events[i][1]
            value = events[i][2]

           #next event
            j = upper_bound(events, endt)

            take = value + solve(j, kleft - 1)
            skip = solve(i + 1, kleft)

            t[i][kleft] = max(take, skip)
            return t[i][kleft]

        return solve(0, k)
```


NOTE: After somedays i'll start doing only DP problems 
