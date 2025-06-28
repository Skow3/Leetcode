# EASY 
2099

The question was easy but the only thing which was there was to make it more and more short /one-liner

Earlier i got confused that since we have to return the numbers , we can return it in any order.
But 
It was to be inserted in the actual order of them in the sequence

#### FIRST APPROACH 
```PYTHON
class Solution(object):
    def maxSubsequence(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        ans = []
        nums.sort()
        i=-1
        while k!=0:
            ans.append(nums[i])
            k-=1
            i-=1
        return ans
```

After noticing i went for this solution , which i then converted it to somewhat shorter by checking on some tricks 

# FINAL SOLUTION
```python
class Solution(object):
    def maxSubsequence(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        indexed  = list(enumerate(nums))
        top_k = sorted(indexed,key=lambda x: x[1],reverse =True)[:k]
        top_k_back= sorted(top_k,key=lambda x: x[0])
        return (x[1] for x in top_k_back)
```
TOC: O(nlogn)

## NOTE :
Ik we can do that in minheap too, that came in my mind first but i have yet to revise all the questions once topics wise i'll start that asap.

# THINGS I LEARNT / REVISED:
* sorted() function's parameters like key and reverse.
* Using the key parameter
* Returning an array [single liner]

---
