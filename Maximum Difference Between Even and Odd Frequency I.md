# EASY 
#### 3442

First i thought of doing counting for each solution and making an array of indices 0 to 25 for storing the freq of different characters:
But it would have taken a lot of memory
But this was how i was going to approach on first thought -->
* Using the ord() function and finding the ASCII value and then accordingly inreasing frequencies.
* Then accordingly checking for the min even and max odd numbers.

This is how we can use ord function:
```python
ord('a') # output = 97
print(ord('z') - 97) # output =0
```

# Now going with my second Approach :
  * Made an dict to take the frequencies of the numbers and then increased the same accordingly.
  * Solved the isssue of Space Complexity.
  * Time complexity reduced to O(n)

##### CODE:
```python
class Solution(object):
    def maxDifference(self, s):
        """
        :type s: str
        :rtype: int
        """
        dt = {}
        for i in s:
            if i in dt:
                dt[i] +=1
            else:
                dt[i] = 1
        mine = float('+inf')
        maxo = float('-inf')
        for i in dt:
            if dt[i]%2 ==0:
                if dt[i]< mine:
                    mine = dt[i]
            else: 
                if dt[i] > maxo:
                    maxo = dt[i]
        return (maxo - mine)
```
##### TIME COMPLEXITY : O(n)
![image](https://github.com/user-attachments/assets/27f1db02-8db7-48d4-97f9-1565615f94de)

---

# THINGS LEARNED / REVISED
* Using ord
* Using float('-inf') and float('+inf') to give values of -infinity and +infinity to variables
