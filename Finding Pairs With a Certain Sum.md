# Medium
The question was just about understanding the language as per i think.
Becuase the coding part was not that difficult for this.

---

# Approach 1
* As i saw that we have to return the pairs so i started thinking over that how to get the indices [bcs the pair of indices was in the answer].
* Then i start thinking about a solution over that.
* Then atlast i tried reading the example again

!! IT WAS RETURNING Number of pairs but not the pairs!

That's it 
I went directly by making an dictionary and then doing the count thing

# SOLUTION 1:
```python
class FindSumPairs(object):

    def __init__(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        """
        self.nums1= nums1
        self.nums2= nums2

    def add(self, index, val):
        """
        :type index: int
        :type val: int
        :rtype: None
        """
        self.nums2[index] += val

    def count(self, tot):
        """
        :type tot: int
        :rtype: int
        """ 
        segt= dict()
        ## making seg
        for i in self.nums2:
            if i in segt:
                segt[i] +=1
            else:
                segt[i] =1
        
        coun = 0
        for i in self.nums1:
            d= tot-i
            if d in segt:
                coun+= segt[d]
        return coun

# Your FindSumPairs object will be instantiated and called as such:
# obj = FindSumPairs(nums1, nums2)
# obj.add(index,val)
# param_2 = obj.count(tot)
```

This passed 21/23 cases.
But after reviewing the code again i saw that the segt was created every time the count function was called.
So it was taking time.
Instead of that i made it to intialize at the start.
Also changing the freq dict everytime anything is added 

# FINAL SOLUTION
```python
class FindSumPairs(object):

    def __init__(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        """
        self.nums1 = nums1
        self.nums2 = nums2
        self.freq = dict()
        for num in nums2:
            self.freq[num] = self.freq.get(num, 0) + 1

    def add(self, index, val):
        """
        :type index: int
        :type val: int
        :rtype: None
        """
        old_val = self.nums2[index]
        self.freq[old_val] -= 1
        if self.freq[old_val] == 0:
            del self.freq[old_val]

        self.nums2[index] += val
        new_val = self.nums2[index]
        self.freq[new_val] = self.freq.get(new_val, 0) + 1

    def count(self, tot):
        """
        :type tot: int
        :rtype: int
        """ 
        coun = 0
        for i in self.nums1:
            d = tot - i
            if d in self.freq:
                coun += self.freq[d]
        return coun
```


# THINGS REVISED / LEARNT 
* The initialize function in python in leetcode.
* Two sum return problem.

---

