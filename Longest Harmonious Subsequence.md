# EASY
Though easy but again of a subsequence question , so took time again 
Getting practice more and more and trying to get the grip over the same


---


# APPROACH 1 
* As always i got confused with the subsequence thing.
* At first i was traversing and checking the difference between i and j

```python
nums = [-3,-1,-1,-1,-3,-2]  # THIS WAS NOT WORKING FOR NEGATIVE VALUE ARRAYS 
maxt = 0
for i in range(len(nums)):
    countt = 0
    gl = False
    for j in range(i,len(nums)):
        if abs(nums[j] - nums[i]) ==1 or (gl== True and abs(nums[j] - nums[i]) ==0):
            if gl == False:
                        countt=1
            print(f"{i},{j}")
            countt +=1
            gl = True
        maxt = max(maxt,countt)
print(maxt)
```

So now finding some solution
Now we just counted the number of min number because i got to realise that the longest subsequence will not be effected by the order.
Since we are just looking at a difference of 1 
So if we just calculate the number of elements which have difference of 1 and count the same element :

# APPROACH 2:
```python
counter = dict()
for i in range(len(nums)):
    if nums[i] not in counter:
        counter[nums[i]] = 1
    else:
        counter[nums[i]] += 1
print(counter)     # {-3: 2, -1: 3, -2: 1}
maxt = 0
for key in counter:
    if key + 1 in counter:
        maxt = max(maxt, counter[key] + counter[key + 1])
print(maxt)
```

# APPROACH 3:
More optimised one :
* Doing the sorting first and then checking the lenght between the indices.

```python
class Solution:
    def findLHS(self, nums):
        nums.sort()
        j = 0
        maxLength = 0
        for i in range(len(nums)):
            while nums[i] - nums[j] > 1:
                j += 1
            if nums[i] - nums[j] == 1:
                maxLength = max(maxLength, i - j + 1)
        return maxLength
```

---

### THINGS I LEARNED / REVISED 
1. Counter function
```python
# SYNTAX
from collections import Counter
nums = [-3,-1,-1,-1,-3,-2]
counter = Counter(nums)
print(counter) # Counter({-1: 3, -3: 2, -2: 1})
```
2. Reading the question properly
