# Important Question 
Asked in Amazon 

#### Thought process
##### Solution 1
Recursion Tree : 
This solution was good but since the constraints were very tight i.e 10^6 so GETTING a TC of O(n^3) is not good
```python
  def checkfinal(child,remaining,limit):
    if(child==3):
      if(remaining ==0)
        return true

  ways =0
  for assigned in (0,min(n,limit)):
    if(checkfinal(child+1,n-assigned,limit))
      ways+=1
  return ways
```

##### Solution 2
Iteration :
This solution again gave 3 for loops resulting in a TC = O(n3)
```python
ways =0
for ch1 in (0,min(n,limit):
  for ch2 in (0,min(n-ch1,limit):
    for ch2 in (0,min(n-ch1-ch2,limit)):
      if(ch1+ch2+ch3 == n)
        ways+=1
return ways
```

##### Solution 3 
Reducing the Iteration to O(n2) by reducing one for loop
```python

ways =0
for ch1 in (0,min(n,limit):
  for ch2 in (0,min(n-ch1,limit):
    ch3= n-ch1+ch2  
    if(ch1+ch2+ch3 == n)
    ways+=1
return ways
```

##### Solution 4
Final Solution .. Converting the main question into smaller easier questions 
```python
class Solution(object):
    def distributeCandies(self, n, limit):
        """
        :type n: int
        :type limit: int
        :rtype: int
        """
        # Setting maximum and minimum values for Child1
        minch1 = max(0,n-limit*2)
        maxch1 = min(n,limit)
        ways =0
        for i in range(minch1,maxch1+1):
            N = n-i # Converting the problem into 2 child problem 
            # Now we'll calculate the min and max for the child2 for getting the ways
            minch2 = max(0,N-limit)
            maxch2 = min(N,limit)
            ways += (maxch2 - minch2 +1)
        return ways
```
