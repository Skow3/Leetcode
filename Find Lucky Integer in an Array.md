# EASY

* This was an easy question just the main thing is to sort which i left earlier bcs all the examples were already sorted.
* So i thought all the test-cases will be sorted.

# SOLUTION:
```python
class Solution(object):
    def findLucky(self, arr):
        """
        :type arr: List[int]
        :rtype: int
        """
        arr.sort()
        i = len(arr)-1
        his = arr[i]
        count=0
        while i!=-1:
            print(f"I VALUE {i}")
            if his == arr[i]:
                count+=1
                print(f"{count},{arr[i]}")
            else:
                if count == arr[i+1]:
                    return arr[i+1]
                his = arr[i]
                count=1
                print(f"{count},{arr[i]}")
            if count == arr[i] and i==0:
                return arr[i]
            i-=1
        return -1
```

# THINGS REVISED :
1. Whenever there is a remembrance of "Largest like return the largest" then we should always go for sorting by default.
2. And we should start from the end.
